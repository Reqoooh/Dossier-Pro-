# Pour une Serveur:
## ENABLE 
```
#en 
```
## Pour rentrer dans les configurations
```
#conf t
```
## Permet de le mettre en mode master
```
#vtp mode server
```
## Permet de le mettre dans un domaine commun a tous les cisco
```
#vtp domain "Exemple"
```
## Permet de mettre un mot de passe pour ce domaine
```
#vtp password "MDP"
```
## Permet de choisir la version du VTP
```
#vtp version 2
```
## Permet d'activer le pruning si besoin
```
#vtp pruning
```
Quand le pruning VTP est activé, un switch envoie seulement le trafic des VLANs qui sont réellement utilisés par les autres switches connectés. Si un VLAN particulier n'est pas utilisé par un switch, le trafic de ce VLAN ne sera pas envoyé sur le lien trunk vers ce switch.
