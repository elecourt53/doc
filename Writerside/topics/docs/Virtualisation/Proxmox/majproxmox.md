---
icon: simple/proxmox
---
# Mises à jour de Proxmox

Pour mettre à jour Proxmox, il faut d'abord :

- (Dans mon cas ajouter un serveur proxy :
Datacenter -> Options -> HTTP proxy -> ajouter le lien du proxy avec le port)

- Changer les repositories, ceux par défaut sont pour les clients qui achètent la licence pour le support et les mises à jour.

## Changement de repositories

Il faut aller sur pve01 (ou 02), puis "repositories", sélectionner les dépots pxe-entreprise et ceph version entreprise.

<figure markdown="span">
  ![Configuration réseau](./Captures-maj/01%20-%20menu%20apt%20avant%20desac.png){ width="500" }
</figure>

Après, il faut ajouter les dépots "No-Subscription" et "Ceph No-Subscription" pour pouvoir bénéficier des mises à jour.

<figure markdown="span">
  ![Configuration réseau](./Captures-maj/02%20-%20add%20no%20subscription.png){ width="500" }
</figure>
<figure markdown="span">
  ![Configuration réseau](./Captures-maj/03%20-%20add%20no%20subscription%20ceph.png){ width="500" }
</figure>

A la fin, il faut cliquer sur "reload" puis aller dans le menu "Updates" puis "Refresh"

<figure markdown="span">
  ![Configuration réseau](./Captures-maj/04%20-%20menu%20maj.png){ width="500" }
</figure>

## Mise à jour

Il faut maintenant cliquer sur "Upgrade" pour mettre a jour le serveur Proxmox.
Une page pop-up va se lancer (il faut l'autoriser).