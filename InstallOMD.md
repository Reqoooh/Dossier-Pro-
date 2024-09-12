## <span style="color: #FFFF00">**Mise a jour du systeme** 
```
apt-get update
apt-get upgrade
```
## <span style="color: #FFFF00">**Installation des packages**
```
apt-get -y install postfix mailutils vim python-mysqldb
apt-get update && apt-get install -y gnupg2
```

## <span style="color: #FFFF00">**Ajout des cles GPG et configuration du depot**
```
  wget -q "https://labs.consol.de/repo/stable/RPM-GPG-KEY" -O - | sudo apt-key add -
 
  curl -s "https://labs.consol.de/repo/stable/RPM-GPG-KEY" | sudo apt-key add -
  
  echo "deb http://labs.consol.de/repo/stable/debian $(lsb_release -cs) main" > /etc/apt/sources.list.d/labs-consol-stable.list

  apt-get update
 ```
## <span style="color: #FFFF00">**Installation d'OMD**
```
 apt-get install -y omd
```
