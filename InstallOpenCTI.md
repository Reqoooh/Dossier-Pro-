### Pre-requisites

**Debian12  
80Go d'espace pour les containers
10Cores CPU
64Go RAM**

 **Linux**
`sudo su`

`apt install docker-compose`
### Récupérer les sources 

```

mkdir -p /path/to/your/app && cd /path/to/your/app
git clone https://github.com/OpenCTI-Platform/docker.git
cd docker`
```

### Configurer les variables d'environnement

Par défaut, un fichier `.env.sample` existe, il convient donc d'en faire une copie `.env` et de modifier son contenu pour personnaliser les variables d'environnement

```

apt install -y jq
cd ~/docker

(cat << EOF 
OPENCTI_ADMIN_EMAIL=admin@opencti.io 
OPENCTI_ADMIN_PASSWORD=ChangeMePlease 
OPENCTI_ADMIN_TOKEN=$(cat /proc/sys/kernel/random/uuid)
MINIO_ROOT_USER=$(cat /proc/sys/kernel/random/uuid)
MINIO_ROOT_PASSWORD=$(cat /proc/sys/kernel/random/uuid)
RABBITMQ_DEFAULT_USER=guest
RABBITMQ_DEFAULT_PASS=guest
ELASTIC_MEMORY_SIZE=4G
CONNECTOR_HISTORY_ID=$(cat /proc/sys/kernel/random/uuid)
CONNECTOR_EXPORT_FILE_STIX_ID=$(cat /proc/sys/kernel/random/uuid)
CONNECTOR_EXPORT_FILE_CSV_ID=$(cat /proc/sys/kernel/random/uuid)
CONNECTOR_IMPORT_FILE_STIX_ID=$(cat /proc/sys/kernel/random/uuid)
CONNECTOR_IMPORT_REPORT_ID=$(cat /proc/sys/kernel/random/uuid) 
EOF
) > .env
```



OpenCTI utilisant une dépendance sur ElasticSearch, il faut initialiser le`vm.max_map_count` avant de lancer le conteneur.

`sysctl -w vm.max_map_count=1048575`

Ainsi le paramètre `vm.max_map_count=1048575` devient rémanent  dans le fichier `/etc/sysctl.conf`:

### Données persistantes

Les données par défaut OpenCTI doivent rester stables, dans le fichier `docker-compose.yml`, la liste des volumes persistants pour les dépendances se trouvent en fin de fichier.

```
volumes:
	esdata:     # ElasticSearch data
	s3data:     # S3 bucket data  
	redisdata:  # Redis data  
	amqpdata:   # RabbitMQ data`
```
### Démarrer OpenCTI

#### Docker simple

Une fois le fichier `.env` personnalisé, on peut démarrer le `docker-compose` en mode "détaché" (-d) :

```
sudo systemctl start docker.service 
docker-compose up -d`
```

### Installation terminée
