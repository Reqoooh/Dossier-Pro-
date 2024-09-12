
Supervision 04-08 /03/2024
ZABBIX : Installation Agent Passif
fedora (curl -0) si pas de wget

wget -q https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-4+ubuntu22.04_all.deb  
dpkg -i zabbix-release_6.0-4+ubuntu22.04_all.deb 
apt update
apt install -y -qq zabbix-agent 
echo "
Server=192.168.105.140
Hostname=z2
">> /etc/zabbix/zabbix_agentd.conf
systemctl restart zabbix-agent
systemctl enable zabbix-agent
Installation du Configuration > Hosts > template + group

Télécharger l'agent Zabbix
Utilisez la commande wget ou curl pour télécharger l'archive de l'agent Zabbix depuis le site officiel. Par exemple :

wget https://repo.zabbix.com/zabbix/5.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.4-1+ubuntu20.04_all.deb
sudo dpkg -i zabbix-release_5.4-1+ubuntu20.04_all.deb
sudo apt install zabbix-agent
sudo nano /etc/zabbix/zabbix_agentd.conf
sudo systemctl start zabbix-agent
sudo systemctl enable zabbix-agent
sudo systemctl status zabbix-agent
Une fois que vous avez suivi ces étapes, l'agent Zabbix devrait être installé et configuré sur votre machine Unix, prêt à être utilisé pour surveiller avec un serveur Zabbix.

Centreon Installation
https://docs.centreon.com/fr/docs/installation/installation-of-a-central-server/unattended-install-central/ sur debian 11

apt update && apt upgrade

curl -L https://raw.githubusercontent.com/centreon/centreon/23.10.x/centreon/unattended.sh --output /tmp/unattended.sh

bash /tmp/unattended.sh install -t central -v 23.10 -r stable -s -l DEBUG 2>&1 |tee -a /tmp/unattended-$(date +"%m-%d-%Y-%H%M%S").log

Interface web : ip_de_la_machine pas de port spécifique

Mise en place du SNMP V3
Pour les machine linux mieux vaut faire par netdata

apt install snmp
apt install snmpd
apt install net-tools

stoper le service systemctl stop snmpd
nano /var/lib/snmp/snmpd.conf
supprimer la ligne user en trop
nano /etc/snmp/snmpd.conf
agentaddress 127.0.0.1,192.168.105.103
rouser centreon authpriv -V systemonly

systemctl restart snmpd

snmpwalk -v3 -u centreon -a SHA-512 -A centreontest123 -x AES -X centreontest321 -l authpriv localhost

Liaison netdata
Ajout de host Centreon
Prendre les bon package template sur Rouage -> Monitoring Connector Manager

Rouage->Host add Host -> remplir les macros

Après Poller
à chaque fois qu'on ajoute une machine/host
-pollers
-configure pollers
-export configuration
- tous coché sauf Post generation commande !!

Plugins
ajout de plugins /etc/apt/sources.list.d apt-get dist upgrade

apt-get install centreon-plugin-aplications-* (installer tous les plugins)
