## Installation SUDO
```
su -
```
```
apt install sudo
```
# Creation du fichier sudo dans /etc/sudoers.d
```
nano /etc/sudoers.d/sysadmin
```
# configuration d'un user dans le fichier sysadmin
![](https://i.gyazo.com/26c2dd08bc481e719113baa4d279280c.png)
```
exit
```
```
sudo -i
```
## INSTALLATION DE DOCKER 
# Desinstallation des packages pouvant causer des conflits
```
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
# Creation du repertoire docker
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
# Installation de la derniere version 
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
# Verification de l'installation via l'image Hello-World
```
 sudo docker run hello-world
 ```
## INSTALLATION DE PORTAINER 
# Creation du volume qui servira de datastore
```
docker volume create portainer_data
```
# Telechargement et installation du serveur Portainer
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
# Verification que le serveur portainer fonctionnent
```
docker ps 
```
# Connection a la page web
```
https://iP_ADDRESS:9443
```
## INSTALLATION DE NETDATA 
# Creation du container
```
docker run -d --name=netdata \
  --pid=host \
  --network=host \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /etc/localtime:/etc/localtime:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /etc/os-release:/host/etc/os-release:ro \
  -v /var/run/docker.sock:/var/run/docker.sock:ro \
  --restart unless-stopped \
  --cap-add SYS_PTRACE \
  --cap-add SYS_ADMIN \
  --security-opt apparmor=unconfined \
  netdata/netdata
  ```
# Connection a la page web 
```
http://IP_ADDRESS:19999
```


## INSTALLATION DE BTOP 
```
apt install btop
```

# Vu de BTOP 
![](https://i.gyazo.com/7629bb95e7f4108e29367fd6d7d1257d.png)
