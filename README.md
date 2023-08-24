# DNS sur windows server : installation, configuration et test

#### Les étapes :
#### Installation du rôle DNS
#### Configuration de la zone "wilders.lan"
#### Ajout d'enregistrements A et CNAME
#### Test
***

✔ Après avoir relié par **câble RJ45**, une **machine cliente** qui héberge un **site web** à un **switch** et **une autre machine** qui héberge **DNS sur windows server** au même **switch**, configurer les deux machines sur **Accès par pont**  :

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

***

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/aa60d0d3-78bd-4e37-a73b-e4dc0881ef1d)

✔ Clic-droit sur **"wilders.lan"** ---> Clic droit **Nouvel hôte A** ---> Remplir la fenêtre **Nouvel hôte** en renseignant l'adresse IP attribuée à la machine cliente et valider.

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/be717a73-2a3d-4689-a0d8-1c2413770d24)

***

✔ Clic droit sur **"wilders.lan"** ---> **Nouvel Alias CNAME** ---> Parcourir ---> Double-clic sur **SRV-DHCP** ---> Double-clic sur **zones de recherche directes** ---> Double-clic sur **wilders.lan** ---> Sélectionner **Projet2 hôte A** ---> **ok**.

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/09adcebd-45a2-4567-af01-96f49f367fb8)

***
✔ Test depuis le serveur :

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/91a42a42-2748-4665-bac6-d0f28fb32306)

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/c63835d1-75fc-4886-9eef-dbdc374e4ac1)

![image](https://github.com/techerbeatrice/DNS_windows-server/assets/138071140/bc170260-e945-45eb-8209-7701cc1a88b5)


