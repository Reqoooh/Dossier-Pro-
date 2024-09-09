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
## Creating a port-channel interface Port-channel 1 
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
