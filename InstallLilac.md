## Creation de la database 

#### Connection en root a MySQL

```
mysql -u root -p
```

```
CREATE DATABASE Lilac_db;
```


#### Creation de l'utilisateur lilac
```
CREATE USER 'lilac'@'localhost' IDENTIFIED BY 'Mot De Passe';
```

#### Donne tous les droits a l'utilisateur lilac sur la bdd 
```
GRANT ALL PRIVILEGES ON lilac_db.* TO 'lilac'@'localhost';
```

#### Permet de recharger la table des privileges 
```
FLUSH PRIVILEGES;
```

#### Quitter 
```
EXIT;
```



```
cd /var/www/html/
```

```
git clone https://github.com/EyesOfNetworkCommunity/lilac.git
```


#### Change les droits proprietaire du chemin de fichiers a www-data
```
sudo chown -R www-data:www-data /var/www/html/lilac/includes
```

#### Donne les droits a l'utilisateur www-data pour le chemin du fichier 
```
sudo chmod -R 775 /var/www/html/lilac/includes
```

```
nano lilac-conf.php
```
#### Mettre les credentials de la database
![[Pasted image 20240730150721.png]]


#### Pour chercher toutes les updates dispo pour la base sql 
```
find /var/www/html/lilac -name "*.sql" 
```
![[Pasted image 20240730150815.png]]

#### Pour mettre a jours la bdd sql en fonction de quelle version nous avons besoin
```
mysql -u lilac -p lilac_db < /chemin/vers/le/fichier_sql.sql
```



#### Page sur laquelle vous arrivez en faisant toutes les commandes 
![[Pasted image 20240730150913.png]]
