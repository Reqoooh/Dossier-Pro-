# ADCS : installer un certificat webserver pour un Vhost Apache

le nom de domaine est à adapter ici c'est pour www.bobdy.lan
les captures d'écrans sont pour un autre FQDN

## 1) Génération du clé avec openssl
**Création de la clé**

```cd /etc/ssl/private ```


``` sudo openssl genrsa -out mydomain.key 2048```

## 2) Création d'un fichier de conf avec les subjectAltName
**Création du fichier de conf avec les SubjectAltName**

```
cd /etc/ssl  
nano www.bobdy.lan.conf
```

```
[req]
default_bits = 2048
prompt = no
default_md = sha256
req_extensions = req_ext
distinguished_name = dn
[ dn ]
C=FR
ST=CVDL
L=Tours
O=CEFIM
OU=IT
emailAddress=info@bobdy.lan
CN = www.bobdy.lan
[ req_ext ]
subjectAltName = @alt_names
[ alt_names ]
DNS.1 = bobdy.lan
DNS.2 = www.bobdy.lan
```


## 3) Création du csr avec notre fichier de conf
**On se place à l'endroit ou est notre clé on indique qu'on veut un certificat csr avec comme config notre fichier de conf crée juste avant**
``` cd /etc/ssl/private ```

```openssl req -new -key www.bobdy.lan.key -out www.bobdy.lan.csr -config ../www.bobdy.lan.conf```

## 4) Importer notre csr sur notre AD-CS

J'ai utilisé la solution winscp et les vmtools personnellement  



## 5) Signer notre csr avec notre authorité de certification

**Déplacer vous dans l'emplacement ou vous avez deposé votre .csr ensuite on lance une requête afin qu'il signe notre certificat et nous le redonne en .cer**

```
cd ./desktop 
certreq -submit -attrib "CertificateTemplate:WebServer" www.bobdy.lan.csr
```

<img src= "https://i.imgur.com/qVtt5j7.png">

Ensuite vous donner un nom à votre fichier.  
Par exemple www.bobdy.lan

<img src= "https://i.imgur.com/eIfAdpg.png">

## 6) Importer votre .cer dans votre apache 
**J'ai utilisé la solution winscp et les vmtools personnellement**
Déposer votre .cer dans votre /etc/ssl/cert
<img src= "https://i.imgur.com/GHlOPvg.png">

## 7) Configuration d'apache
**Mettre le bon path pour chaque certificat**  

```
cd /etc/apache2/sites-available
nano default-ssl.conf
```
```
SSLCertificateFile      /etc/ssl/certs/www.bobdy.lan.cer
SSLCertificateKeyFile   /etc/ssl/private/www.bobdy.lan.key
```

<img src= "https://i.imgur.com/hjXzi3a.png">

```
systemctl restart apache2
```

***
## 8) Configuration du client
**Importer et rajouter votre root CA dans le navigateur**

Dans votre AD-CS  
*windows + R*

Mettre certmgr.msc

Aller dans autorités de certification racine > puis dans certificats

<img src= "https://i.imgur.com/RmfvEzK.png">

Clique droit sur votre Root-CA  
Toutes les taches > exporter

<img src= "https://i.imgur.com/2qkh5N6.png">

Exporter bien en base64 et pas DER

<img src= "https://i.imgur.com/fPWE94e.png">
<img src= "https://i.imgur.com/ec4SyCB.png">

Il vous suffit après d'importer votre ROOT-CA dans votre navigateur.
