## Passage en mode configuration 
```
Sw1#configure terminal
```
## Sélectionner la plage d'interfaces
```
#Sw1(config)#interface range fastEthernet 0/1 - 2
```
## Création d'un groupe EtherChannel n°1 avec le protocole LACP (mode active)
```
#Sw1(config-if-range)#channel-group 1 mode active
```

Explication :
Cette commande crée un groupe d'agrégation de liens nommé channel-group 1 en utilisant le protocole LACP (Link Aggregation Control Protocol) en mode "actif".

channel-group 1 : Désigne le numéro du groupe d'agrégation (ou EtherChannel) qui sera utilisé pour regrouper les interfaces sélectionnées.
mode active : Utilise le protocole LACP en mode actif. En mode "actif", le switch envoie activement des paquets LACP pour établir et maintenir l'agrégation de liens avec le switch ou dispositif partenaire, en s'assurant que l'autre côté participe également à l'agrégation.

## Création d'une interface de port-channel
```
Sw1(config-if-range)#exit
```
## Accès au paramétrage du port-channel créé
```
#Sw1(config)#interface port-channel 1
```
## Passer le port-channel en mode trunk pour pouvoir faire passer plusieurs VLANs
```
#Sw1(config-if)#switchport mode trunk
```
