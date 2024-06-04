---
icon: simple/windows11
---
## 1 - Télécharger l'ISO et ajout à Proxmox
[Télécharger l'ISO de :simple-windows11: Windows 11 ici](https://www.microsoft.com/fr-fr/software-download/windows11)

Pour l'ajouter au serveur, il faut :

- Cliquer sur :material-server: Datacenter -> le nom du serveur (pve01 ou 02), -> local -> ISO images -> Upload
  
Après il faut sélectionner le fichier ISO et cliquer sur upload.

## 2 - Télécharger les pilotes et ajout au serveur
[Télécharger les pilotes](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/latest-virtio/virtio-win.iso)

Pour ajouter l'ISO des pilotes au serveur, comme pour l'ISO :simple-windows11: Windows 11, il faut :

- Cliquer sur :material-server: Datacenter -> le nom du serveur (pve01 ou 02), -> local -> ISO images -> Upload

Après il faut sélectionner le fichier ISO et cliquer sur upload.

## 3 - Création d'une VM
Il faut aller sur le bouton "Create VM" situé en haut à droite.

<figure markdown="span">
  ![Bouton "Create VM"](./images/creationVM/01%20-%20création%20VM%20bouton.png){ width="500" }
</figure>

Donner un nom à la VM et choisir le serveur physique du cluster (si on en a un).

<figure markdown="span">
  ![Nom VM et cluster](./images/creationVM/02%20-%20nom%20vm.png){ width="500" }
</figure>

## 4 - Choix du système d'exploitation (ajout de l'ISO)

!!! warning "Attention !!"
    Il faut aussi ajouter l'ISO des pilotes pour :simple-windows11: Windows

    - Cliquer sur "Add additional drive for VirtIO drivers" puis choisir l'ISO des pilotes

    Sur l'image ci-dessous les pilotes sont sélectionnés.

Dans "Guest OS", il faut choisir :simple-windows11: Windows 11.

<figure markdown="span">
  ![Choix OS](./images/creationVM/03%20-%20choix%20OS.png){ width="500" }
</figure>

## 5 - Configuration du système
Il faut activer le "qemu-agent", sélectionner "local-lvm" pour le stockage de l'EFI et sélectionner "local-lvm" pour le stockage de la puce TPM.

Il faut aussi vérifier que BIOS = "OVMF (UEFI)" et que le controleur SCSI soit : "VirtIO SCSI" (attention il faudra installer le pilote plus tard).

<figure markdown="span">
  ![Choix OS](./images/creationVM/04%20-%20configuration%20système.png){ width="500" }
</figure>

## 6 - Configuration des disques durs
!!! info
    Si les VM sont stockées sur un SSD, choisir "SSD emulation", ce qui permettra à :simple-windows11: Windows de comprendre que l'on utilise un SSD.

Choisir "SCSI" dans Bus/Device, "Write back" dans cache (cela permet d'améliorer les performances) et "Discord" pour gérer le provisionnement dynamique.

<figure markdown="span">
  ![Choix HDD](./images/creationVM/05%20-%20configuration%20HDD.png){ width="500" }
</figure>

## 7 - Configuration CPU
Choisir le nombre de coeurs dans "Cores", dans "Type" choisir dans la liste le dernier choix "Host".
<figure markdown="span">
  ![Configuration CPU](./images/creationVM/06%20-%20configuration%20CPU.png){ width="500" }
</figure>

## 8 - Configuration RAM
Choisir le nombre de Go de RAM pour la VM.

<figure markdown="span">
  ![Configuration RAM](./images/creationVM/07%20-%20configuration%20RAM.png){ width="500" }
</figure>

## 9 - Configuration carte réseau
!!! info
    - Il faut désactiver la carte réseau pour que :simple-windows11: Windows n'oblige pas à se connecter avec un compte Microsoft.
    
    - La carte réseau sera réactivée plus tard.
<figure markdown="span">
  ![Configuration carte réseau](./images/creationVM/08%20-%20configuration%20carte%20réseau.png){ width="500" }
</figure>

## 10 - Ajout des pilotes lors du partitionnement des disques.
Lancer l'installation de :simple-windows11: Windows, au moment du partionnement des disques, il va falloir installer les pilotes.

<figure markdown="span">
  ![Menu partitionnement disque](./images/ajoutPilotespendantinstall/01%20-%20probleme%20pendant%20install.png){ width="500" }
</figure>

Cliquer sur "Charger un pilote".

<figure markdown="span">
  ![Menu charger un pilote](./images/ajoutPilotespendantinstall/02%20-%20menu%20charger%20un%20pilote.png){ width="500" }
</figure>

Cliquer sur "Parcourir", puis D:, "amd64" et "w11" et cliquer sur OK.

<figure markdown="span">
  ![Menu parcourir](./images/ajoutPilotespendantinstall/03%20-%20menu%20parcourir.png){ width="500" }
</figure>

Sélectionner le pilote fonctionnant avec la VM.

<figure markdown="span">
  ![Sélection pilote](./images/ajoutPilotespendantinstall/04%20-%20choix%20pilote.png){ width="500" }
</figure>

Le pilote est désormais fonctionnel.

<figure markdown="span">
  ![Pilote fonctionnel](./images/ajoutPilotespendantinstall/05%20-%20menu%20partitionnement.png){ width="500" }
</figure>

## 11 - Bypass Compte Microsoft
Si au démarrage du PC, il est demandé de se connecter à un compte Microsoft, voir [cette page](./bypassmicrosoft.md)

## 12 - Après l'installation
Pour installer les pilotes réseaux et le RDP, voir [cette page](./postinstallation.md)

## Sources
- [technonagib.fr](https://technonagib.fr/virtualiser-windows-11-proxmox-ve/)

- [florianmuller.com](https://florianmuller.com/install-windows-11-on-proxmox-7-0-13-with-tpm-2-0-chip-emulation)