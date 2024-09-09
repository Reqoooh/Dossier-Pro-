# Creation d'un portail captif

## Configuration du Portail Captif
```
Sélectionner : Services – Captive Portal
```
![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-1.jpg)
```
Cliquez sur « + Add »
```
![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-2.jpg)
```
Renseigner le Nom du Portail Captif et sa description. Pour l’exemple : « PORTAIL »
```
![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-3.jpg)
```
Activer « Enable Captive Portal« 
```
```
Sélectionner l’interface « LAN« 
```
```
Maximum concurrent connections : 1 (Limite le nombre de connexions simultanées d’un même utilisateur)
```
```
Idle timeout (Minutes) : Choisir entre 1 a 5 (Les clients seront déconnectés après cette période d’inactivité)
```
![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-4.jpg)
```
Activer « Enable logout popup window » (une fenêtre popup permet aux clients de se déconnecter)
```
```
Définir « Pre-authentication Redirect URL » (URL HTTP de redirection par défaut. Les visiteurs ne seront redirigés vers cette URL après authentification que si le portail captif ne sait pas où les rediriger)
```
```
Définir « After authentication Redirection URL » (URL HTTP de redirection forcée. Les clients seront redirigés vers cette URL au lieu de celle à laquelle ils ont initialement tenté d’accéder après s’être authentifiés)
```
```
Activer « Disable Concurrent user logins » (seule la connexion la plus récente par nom d’utilisateur sera active)
```
```
Activer « Disable MAC filtering » (nécessaire lorsque l’adresse MAC du client ne peut pas être déterminée)
```
```
*Note : URL HTTP > « http://….. » devant le domaine : « https://www.pc2s.fr » – La redirection HTTPS vers HTTP ne peut pas fonctionner car il faut un certificat valide pour que la redirection se fasse sans problème.*
```
![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-5.1.png)
```
Sélectionner « Use an Authentication backend« 
```
```
Sélectionner « Local Database » pour « Authentication Server »
Attention : Ne pas sélectionner « Local Database » pour « Secondary Authentication Server »
```
```
Activer « Local Authentication Privileges » (Autoriser uniquement les utilisateurs avec les droits de « Connexion au portail captif »)
```
![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-6.jpg)

## Resultat

![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-8.jpg)
```
Exemple de lien d’accès au portail : http://192.168.2.1:8002/index.php?zone=portail  
```
```
(zone=portail : car notre portail captif se nomme « PORTAIL »)
```
![](https://www.pc2s.fr/wp-content/uploads/2018/10/pfSense-portail-captif-39.jpg)
