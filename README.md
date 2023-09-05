# DNS sur windows server : installation, configuration et test

_____

Sur un Windows Server déployé sur une VM, l'idéal étant de reprendre celui utilisé pour DHCP   
Pense à faire un clone de ta machine (Snapshot) pour avoir un backup, en cas où tu ferais une mauvaise configuration qui rendrait ta machine inutilisable   
•	Mettre en place le service DNS sur le serveur*    
•	Ce serveur fera autorité sur la zone wilders.lan    
•	Enregistre les champs A pour ce serveur et pour la machine ayant une réservation IP fixe    
•	Ajoute un CNAME pour ton serveur. Il pourrait par exemple aussi s'appeler dns.wilders.lan    
•	Test maintenant que tout fonctionne correctement sur le serveur mais aussi sur une machine client    
•	Poste une procédure permettant pas à pas d'obtenir cette configuration ainsi que les tests associés    
•	Il est possible de faire une résolution de nom et une résolution inverse depuis le serveur et depuis une machine du réseau    
•	Le serveur est bien joignable via 2 noms distincts    
•	La procédure est claire et permet effectivement lorsqu'elle est appliquée de répondre aux critères du challenge    
______

#### Les étapes :
#### Branchement de la machine-cliente et la machine-serveur sur le même switch et configuration des 2 machines sur le réseau Accès par pont
#### Installation du rôle DNS
#### Configuration de la zone "wilders.lan"
#### Ajout d'enregistrements A et CNAME
#### Test
***

✔ Après avoir relié par **câbles RJ45**, une **machine cliente** qui héberge un **site web** à un **switch** et **une autre machine** qui héberge **DNS sur windows server** au même **switch**, configurer les deux machines sur **Accès par pont**  :

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/9e2ea9c0-7c6e-4d24-99b7-bfe821942998)

***

✔ Donner le rôle DNS à windows Server, pour cela aller dans Gérer --> Ajouter des rôles et fonctionnalités --> Dans Type d'installation, sélectionner Installation basée sur un rôle ou une fonctionnalité --> Dans sélection du serveur --> Sélectionner un serveur du pool de serveurs --> Sélectionnner le serveur de destination --> Dans la liste des rôles, cochez Serveur DNS.

***

✔ Configurer la zone **"wilders.lan"**, pour cela aller sur **Gestionnaire DNS**, cliquer avec le bouton droit sur **"Zones de recherche directe"** et sélectionner **"Nouvelle zone"** :

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/22ff3765-bb95-492a-818f-b8d26518e7f6)    


![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/3b98aa98-7af1-4206-8a85-69e9280e6807)

***

✔ Suivre l'**Assistant Nouvelle Zone**, cliquer sur suivant, sélectionner **zone principale**, renseigner le nom de la zone principale, dans notre cas **"wilders.lan"**.

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/d4f12ef5-93bb-403d-9f98-16e80c3263af)

***

✔ Renseigner également la partie zone de **recherche inversée** en renseignant l'**ID Réseau** qui dans ce cas, n'enregistre que les 3 premiers octets :

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/aa60d0d3-78bd-4e37-a73b-e4dc0881ef1d)

***

✔ Clic-droit sur **"wilders.lan"** ---> Clic droit **Nouvel hôte A** ---> Remplir la fenêtre **Nouvel hôte** en renseignant l'adresse IP attribuée à la machine cliente et valider.

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/12359e72-a405-4f4d-9f9f-01328ed77c69)

***

✔ Clic droit sur **"wilders.lan"** ---> **Nouvel Alias CNAME** ---> Remplir la fenêtre **Nouvel enregistrement de ressource** ---> Parcourir ---> Double-clic sur **SRV-DHCP** ---> Double-clic sur **zones de recherche directes** ---> Double-clic sur **wilders.lan** ---> Sélectionner **Projet2 hôte A** ---> **ok**.

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/09adcebd-45a2-4567-af01-96f49f367fb8)

***
✔ Test depuis le serveur :

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/cc82df89-36fd-47f2-8b09-ae2d304581c8)

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/c63835d1-75fc-4886-9eef-dbdc374e4ac1)

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/bc170260-e945-45eb-8209-7701cc1a88b5)


