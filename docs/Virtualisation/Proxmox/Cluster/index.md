---
icon: simple/proxmox
---
## Qu'est ce qu'un cluster sur Proxmox ?

Un cluster permet de relier plusieurs machines physiques appelés (noeuds).

Cela permet :

- de gérer plusieurs serveurs physiques sur une seule interface,
  
- de migrer plus facilement des VM / conteneurs entre les noeuds (par exemple si un serveur doit être arrêté pour maintenance, les VM peuvent être migrées sur un autre serveur et donc les services présents seront disponibles.),
  
- d'avoir de la haute disponibilité (par exemple si un serveur tombe en panne, les VM seront transférées automatiquement sur un autre serveur du cluster.)

## Comment créer un cluster ?

Sur le premier serveur, aller sur Datacenter -> Cluster et puis "Create cluster".
<figure markdown="span">
  ![Bouton Create cluster](./Captures/03%20-%20boutons.png){ width="500" }
</figure>

Donner un nom à ce cluster et sélectionner l'adresse IP.
<figure markdown="span">
  ![Création du cluster](./Captures/01%20-%20creation%20cluster.png){ width="500" }
</figure>

Les informations à copier sur le second serveur sont présentes.
<figure markdown="span">
  ![Join information](./Captures/02%20-%20cluster%20join%20info.png){ width="500" }
</figure>

Sur le second serveur, aller sur Datacenter -> Cluster et puis "Join cluster".
<figure markdown="span">
  ![Bouton Join cluster](./Captures/03%20-%20boutons.png){ width="500" }
</figure>

Coller les informations copiées précédemment, il y a juste à ajouter le mot de passe de connexion à Proxmox.
<figure markdown="span">
  ![Joindre le cluster](./Captures/04%20-%20cluster%20join.png){ width="500" }
</figure>

Les serveurs sont maintenant présents sur le cluster.
<figure markdown="span">
  ![Liste des serveurs dans le cluster](./Captures/05%20-%20liste%20cluster.png){ width="500" }
</figure>
