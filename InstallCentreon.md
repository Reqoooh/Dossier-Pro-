apt update 
apt upgrade 

systemctl stop firewalld
systemctl disable firewalld

apt update && apt install lsb-release ca-certificates apt-transport-https software-properties-common wget gnupg2 curl

echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/sury-php.list

wget -O- https://packages.sury.org/php/apt.gpg | gpg --dearmor | tee /etc/apt/trusted.gpg.d/php.gpg  > /dev/null 2>&1
apt update

curl -LsS https://r.mariadb.com/downloads/mariadb_repo_setup | bash -s -- --os-type=debian --os-version=11 --mariadb-server-version="mariadb-10.5"

echo "deb https://packages.centreon.com/apt-standard-22.10-stable $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/centreon.list
echo "deb https://packages.centreon.com/apt-plugins-stable/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/centreon-plugins.list

wget -O- https://apt-key.centreon.com | gpg --dearmor | tee /etc/apt/trusted.gpg.d/centreon.gpg > /dev/null 2>&1

apt update
apt install -y --no-install-recommends centreon
systemctl daemon-reload
systemctl restart mariadb

hostnamectl set-hostname new-server-name

Edit the **/etc/php/8.1/mods-available/centreon.ini** file and check the timezone.

systemctl restart php8.1-fpm

systemctl enable php8.1-fpm apache2 centreon cbd centengine gorgoned centreontrapd snmpd snmptrapd

systemctl enable mariadb
systemctl restart mariadb

mysql_secure_installation

Answer **yes** to all questions except "Disallow root login remotely?".

systemctl start apache2

### Installation Web
Connection a l'interface web via : http://IP.centreon

## Etape 1: cliquer sur next 
![[Pasted image 20240214162941.png]]
## Etape 2: Verification des dependances 
Verification des modules prerequis pour le bon fonctionnement de centreon.
Tous les modules doivent etre charger en vert.
Si ce n'est pas le cas faites les actions correctrice et appuie sur refresh
![[Pasted image 20240214163025.png]]
### Etape 3: Monitoring engine information 
Permet de definir les chemin utilise par centreon.
Conseiller de les laisser par defauts
![[Pasted image 20240214163047.png]]
### Etape 4: Broker module information 
Permet de definir les chemins pour le broker.
Conseiller de les laisser par defauts
![[Pasted image 20240214163210.png]]

### Etape 5: Admin information
Permet de definir les credentials pour la connection sur l'application web 
Le mdp doit avoir une conformite de 12 caracteres minimum avec lettres miniscules et majuscules, chiffres et caracteres speciaux.
Nous pouvons changer la politique de mot de passe par la suite dans l'interface web centreon.
![[Pasted image 20240214163853.png]]
### Etape 6: Database information
Permet de fournir les informations de connexion a la base de donnees 

Database Host Address: a laisser vide si nous utilisons une base de donnee locale, sinon renseigner l'addresse ip de la base de donnee.

Root user/password: Compte par defaut root et le mot de passe est celui que nous avons defini a l'execution du cli mysql_secure_installation.

Database Username/Password: Compte qui sera utiliser pour interagir avec les bases de donnees centreon. Le compte sera creer pendant l'installation de base 
![[Pasted image 20240214164059.png]]
Puis cliquez sur next

### Etape 7: Installation 

L'assistant de configuration creer les fichiers de configuration et les bases de donnees.
![[Pasted image 20240214164755.png]]
Cliquez sur next quand le processus est fini 

### Etape 8: Installations des modules 
Selectionner les modules et widget que vous souhaiter et cliquez sur install
![[Pasted image 20240214164844.png]]
Cliquez sur next une fois installes 
### Etape 9: Installation Terminer 

![[Pasted image 20240214165028.png]]
