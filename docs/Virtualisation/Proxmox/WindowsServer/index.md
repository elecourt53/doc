---
icon: simple/windows10
---
# Installation de Windows Server 2022 sur Proxmox

Il est simple d'installer un serveur Windows sur Proxmox.

L'installation est similaire à celle de [:simple-windows11: Windows 11](../Windows11/installation.md).

## 1 - Télécharger l'ISO et ajout à Proxmox
[Télécharger l'ISO de :simple-windows10: Windows Server ici](https://software-static.download.prss.microsoft.com/sg/download/20348.169.210806-2348.fe_release_svc_refresh_SERVER_EVAL_x64FRE_fr-fr.iso)

Pour l'ajouter au serveur, il faut :

- Cliquer sur :material-server: Datacenter -> le nom du serveur (pve01 ou 02), -> local -> ISO images -> Upload
  
Après il faut sélectionner le fichier ISO et cliquer sur upload.

## 2 - Télécharger les pilotes et ajout au serveur
[Télécharger les pilotes](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/latest-virtio/virtio-win.iso)

Pour ajouter l'ISO des pilotes au serveur, comme pour l'ISO :simple-windows10: Windows Server, il faut :

- Cliquer sur :material-server: Datacenter -> le nom du serveur (pve01 ou 02), -> local -> ISO images -> Upload

Après il faut sélectionner le fichier ISO et cliquer sur upload.

## 3 - Création d'une VM
Il faut aller sur le bouton "Create VM" situé en haut à droite.

<figure markdown="span">
  ![Bouton "Create VM"](../Windows11/images/creationVM/01%20-%20création%20VM%20bouton.png){ width="500" }
</figure>

<figure markdown="span">
  ![Nom VM et cluster](./Captures/creationVM/01%20-%20nom%20VM.png){ width="500" }
</figure>

## 4 - Choix du système d'exploitation (ajout de l'ISO)

!!! warning "Attention !!"
    Il faut aussi ajouter l'ISO des pilotes pour :simple-windows10: Windows

    - Cliquer sur "Add additional drive for VirtIO drivers" puis choisir l'ISO des pilotes

    Sur l'image ci-dessous les pilotes sont sélectionnés.

Dans "Guest OS", il faut choisir :simple-windows10: Windows 11/2022/2025.

<figure markdown="span">
  ![Choix OS](./Captures/creationVM/02%20-%20choix%20iso.png){ width="500" }
</figure>

## 5 - Configuration du système
Il faut activer le "qemu-agent", sélectionner "local-lvm" pour le stockage de l'EFI et sélectionner "local-lvm" pour le stockage de la puce TPM.

Il faut aussi vérifier que BIOS = "OVMF (UEFI)" et que le controleur SCSI soit : "VirtIO SCSI" (attention il faudra installer le pilote plus tard).

<figure markdown="span">
  ![Choix OS](./Captures/creationVM/03%20-%20system.png){ width="500" }
</figure>

## 6 - Configuration des disques durs
!!! info
    Si les VM sont stockées sur un SSD, choisir "SSD emulation", ce qui permettra à :simple-windows10: Windows de comprendre que l'on utilise un SSD.

Choisir "SCSI" dans Bus/Device, "Write back" dans cache (cela permet d'améliorer les performances) et "Discard" pour gérer le provisionnement dynamique.

<figure markdown="span">
  ![Choix HDD](./Captures/creationVM/04%20-%20disks.png){ width="500" }
</figure>

## 7 - Configuration CPU
Choisir le nombre de coeurs dans "Cores", dans "Type" choisir dans la liste le dernier choix "Host".
<figure markdown="span">
  ![Configuration CPU](./Captures/creationVM/05%20-%20cpu.png){ width="500" }
</figure>

## 8 - Configuration RAM
Choisir le nombre de Go de RAM pour la VM.

<figure markdown="span">
  ![Configuration RAM](./Captures/creationVM/06%20-%20ram.png){ width="500" }
</figure>

## 9 - Configuration carte réseau

Sélectionner VirtIO (paravirtualized) dans le modèle.

<figure markdown="span">
  ![Configuration carte réseau](./Captures/creationVM/07%20-%20network.png){ width="500" }
</figure>

## 10 - Ajout des pilotes lors du partitionnement des disques.
Lancer l'installation de :simple-windows10: Windows, puis choisir la version que l'on souhaite j'ai sélectionné la Standard avec Expérience du Bureau pour avoir une interface graphique.

<figure markdown="span">
  ![Menu édition Windows](./Captures/installWindows/01%20-%20edition.png){ width="500" }
</figure>

Puis, au moment du partionnement des disques, il va falloir installer les pilotes.

<figure markdown="span">
  ![Menu partitionnement disque](../Windows11/images/ajoutPilotespendantinstall/01%20-%20probleme%20pendant%20install.png){ width="500" }
</figure>

Cliquer sur "Charger un pilote".

<figure markdown="span">
  ![Menu charger un pilote](../Windows11/images/ajoutPilotespendantinstall/02%20-%20menu%20charger%20un%20pilote.png){ width="500" }
</figure>

Cliquer sur "Parcourir", puis D:, "amd64" et "2k22" et cliquer sur OK.

<figure markdown="span">
  ![Menu parcourir](./Captures/installWindows/02%20-%20recherche%20pilote.png){ width="500" }
</figure>

Sélectionner le pilote fonctionnant avec la VM.

<figure markdown="span">
  ![Sélection pilote](./Captures/installWindows/03%20-%20choix%20pilote.png){ width="500" }
</figure>

Le pilote est désormais fonctionnel.

<figure markdown="span">
  ![Pilote fonctionnel](../Windows11/images/ajoutPilotespendantinstall/05%20-%20menu%20partitionnement.png){ width="500" }
</figure>

