
##  <span style="color: #00FFFF">**Supervision réseau**

- **Communication entre les machines.**
-  **S'assurer du bon fonctionnement des communications et de la performance des liens (débit, latence, taux d'erreurs). **
- **C'est dans ce cadre que l'on va vérifier par exemple si une adresse IP est toujours joignable, ou si tel port est ouvert sur telle machine, ou faire des statistiques sur la latence du lien réseau.**

##  <span style="color: #00FFFF">**Supervision système**

- **La surveillance se cantonne dans ce cas à la machine elle-même et en particulier ses ressources.**
- **Contrôle de  la mémoire utilisée ou la charge processeur sur le serveur voire analyser les fichiers de logs système.**

##  <span style="color: #00FFFF">**Supervision applicative**

- **Cette technique est plus subtile, c'est elle qui va nous permettre de vérifier le fonctionnement d'une application lancée sur une machine.**
- **Cela peut être par exemple une tentative de connexion sur le port de l'application pour voir si elle retourne ou demande bien les bonnes informations, mais aussi de l'analyse de logs applicatifs.**
- **En effet rien ne garantit qu'un port X ouvert veut dire que l'application qui tourne derrière n'est pas "plantée".**
