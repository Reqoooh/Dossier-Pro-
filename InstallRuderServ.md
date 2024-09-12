## INSTALLATION DE RUDDER SERVER 
```
apt install default-jre
```
# Ajout de la cle repository 
```
wget --quiet -O /etc/apt/trusted.gpg.d/rudder_apt_key.gpg https://repository.rudder.io/apt/rudder_apt_key.gpg
```
# Ajout du fichier a notre systeme 
```
echo "deb http://repository.rudder.io/apt/7.2/ $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/rudder.list
```
# Update the repository index with:
```
apt update
```
# Installation de rudder server 
```
apt install rudder-server
```
# Configuration du rudder-server 
```
rudder server create-user -u "username"
```
# Ouverture des ports pour accessibilites
```
ufw allow 443/tcp
```
```
ufw allow 5309/tcp
```
# Relancer le services rudder 
```
systemctl restart rudder-server
```
# Connection au serveur rudder 
```
https://<ipaddress>/rudder
```
