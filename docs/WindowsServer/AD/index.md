---
icon: simple/windows10
---
# Création d'un Active Directory

## Ajout du rôle

!!! info
    Il faut mettre une adresse IP fixe, et un nom de machine est préférable.

Lancer le Gestionnaire de serveurs, puis cliquer sur : "Ajouter des rôles et des fonctionnalités"
<figure markdown="span">
  ![Ajouter des rôles et des fonctionnalités](./Captures/Creation/01%20-%20menu%20gestionnaire%20srv.png){ width="500" }
</figure>

Sélectionner l'installation d'un rôle, puis le serveur où il sera installé.
<figure markdown="span">
  ![Choix du serveur](./Captures/Creation/02%20-%20choix%20srv%20destination.png){ width="500" }
</figure>

Ajouter le rôle " Service AD DNS"
<figure markdown="span">
  ![Démarrage de la machine et choix de l'installation graphique](./Captures/Creation/03%20-%20ajout%20role%20ad.png){ width="500" }
</figure>

Après, il ne faut pas indiquer de fonctionnalité supplémentaire et cliquer sur Suivant.

Il faut maintenant configurer l'installation de l'AD.


## Configuration post-déploiement
Il faut promouvoir le serveur en contrôleur de domaine.
<figure markdown="span">
  ![Promouvoir le serveur](./Captures/Creation/04%20-%20promouvoir%20serveur.png){ width="500" }
</figure>

Puis, il faut ajouter une nouvelle forêt et lui donner un nom.
<figure markdown="span">
  ![Ajout d'une forêt](./Captures/Creation/05%20-%20nom%20nouvelle%20foret.png){ width="500" }
</figure>

Après, il faut vérifier les options et ajouter un mot de passe.
<figure markdown="span">
  ![Ajout mot de passe](./Captures/Creation/06%20-%20options%20et%20mdp%20controleur%20domaine.png){ width="500" }
</figure>

Il faut aussi vérifier que le nom netBIOS corresponde au nom du domaine choisi.
<figure markdown="span">
  ![Vérification nom netBIOS](./Captures/Creation/07%20-%20nom%20netBIOS.png){ width="500" }
</figure>

Il y a un résumé de la configuration.
<figure markdown="span">
  ![Résumé configuration](./Captures/Creation/08%20-%20verification%20configuration.png){ width="500" }
</figure>

## Ajout redirecteur DNS

Après avoir configuré l'AD, si besoin ajouter un redirecteur DNS.
Il faut aller sur DNS, sélectionner le serveur, puis clique droit, et redirecteurs.
<figure markdown="span">
  ![Ajout redirecteur DNS](./Captures/Creation/09%20-%20ajout%20redirecteurs%20dns.png){ width="500" }
</figure>