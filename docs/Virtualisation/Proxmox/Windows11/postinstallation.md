---
icon: material/remote-desktop
---
# Après l'installation (pilotes réseau, activation RDP)
## Ajout carte réseau
Il faut selectionner la VM, cliquer sur "Hardware" puis "Add", "Network Device"
Il faut choisir le modèle "VirtIO (paravirtualized)"
<figure markdown="span">
  ![Ajout carte réseau](./images/ajoutPilotesapresinstall/01%20-%20ajout%20carte%20réseau.png){ width="500" }
</figure>

## Installation pilote Contrôleur PCI
!!! info
    Remettre l'ISO des pilotes sur le lecteur DVD si enlevé prédcédemment.

Lancer le gestionnaire de périphériques, cliquer sur "Contrôleur PCI de communication simplifiées" puis "Mettre à jour le pilote".

Sélectionner le pilote (voir capture d'écran pour chemin)
<figure markdown="span">
  ![Ajout carte réseau](./images/ajoutPilotesapresinstall/02%20-%20ajout%20pilote%20PCI.png){ width="500" }
</figure>

<figure markdown="span">
  ![Ajout carte réseau](./images/ajoutPilotesapresinstall/03%20-%20chemin%20pilote%20PCI.png){ width="500" }
</figure>

## Installation pilote carte Ethernet

Lancer le gestionnaire de périphériques, cliquer sur "Contrôleur Ethernet" puis "Mettre à jour le pilote".

Sélectionner le pilote (voir capture d'écran pour chemin)

<figure markdown="span">
  ![Ajout carte réseau](./images/ajoutPilotesapresinstall/04%20-%20ajout%20pilote%20Ethernet.png){ width="500" }
</figure>

<figure markdown="span">
  ![Ajout carte réseau](./images/ajoutPilotesapresinstall/05%20-%20chemin%20pilote%20Ethernet.png){ width="500" }
</figure>

## Installation du "guest-agent"
Pour que toutes les informations de la VM soient transmises à Proxmox, il faut installer le "guest-agent"
Il est disponible dans 
```
D:\guest-agent
```
<figure markdown="span">
  ![Ajout carte réseau](./images/ajoutPilotesapresinstall/06%20-%20installation%20guest-agent.png){ width="500" }
</figure>

## Activation du RDP

Aller dans Paramètres -> Système -> Bureau à distance et l'activer

## Créer un modèle de VM

Pour faire du déploiment, il faut utiliser le logiciel sysprep.

Dans l'explorateur de fichier, aller dans "C:\Windows\System32\Sysprep" et cliquer sur "sysprep.exe"

Il faut cliquer sur "Généraliser" et dans le menu déroulant "Eteindre".

Dans Proxmox, faire un clique droit sur la VM puis "Convert to template".