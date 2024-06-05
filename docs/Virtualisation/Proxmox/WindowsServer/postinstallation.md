---
icon: material/remote-desktop
---
# Après l'installation (pilotes, activation RDP)

## Installation pilotes et du "guest-agent"
!!! info
    Remettre l'ISO des pilotes sur le lecteur DVD si enlevé prédcédemment.

Ouvrir l'explorateur de fichiers, choisir le lecteur de CD avec les pilotes, puis cliquer sur "virtio-win-guest-tools.exe".

<figure markdown="span">
  ![Explorateur de fichiers pilotes](../WindowsServer/Captures/installpilotes/01%20-%20explorateur.png){ width="500" }
</figure>

Lancer l'installation des logiciels en cliquant sur "Install".

<figure markdown="span">
  ![Installation pilotes](../WindowsServer/Captures/installpilotes/02%20-%20menu%20install.png){ width="500" }
</figure>

Choisir les pilotes que l'on veut utiliser (j'ai laissé les choix par défaut).

<figure markdown="span">
  ![Choix pilotes](../WindowsServer/Captures/installpilotes/03%20-%20choix%20pilotes.png){ width="500" }
</figure>

## Activation du RDP

Aller dans Paramètres -> Système -> Bureau à distance et l'activer

## Créer un modèle de VM

Pour faire du déploiment, il faut utiliser le logiciel sysprep.

Dans l'explorateur de fichier, aller dans "C:\Windows\System32\Sysprep" et cliquer sur "sysprep.exe"

Il faut cliquer sur "Généraliser" et dans le menu déroulant "Eteindre".

Dans Proxmox, faire un clique droit sur la VM puis "Convert to template".