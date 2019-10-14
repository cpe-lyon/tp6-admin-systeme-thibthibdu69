# TP6 - Gestion des disques / Tâches d'administration


## Exercice 1. Disques et partitions


### 1) Dans l’interface de configuration de votre VM, créez un second disque dur, de 5 Go dynamiquement alloués ; puis démarrez la VM

    Ajouter un nouveau disque
    VHD
    Alloué dynamiquement
    5.00GB

### 2) Vérifiez que ce nouveau disque dur est bien détecté par le système

    On peut afficher tous les disques durs du système grâce à la commande :

    ll /dev/sd*

### 3) Partitionnez ce disque en utilisant fdisk : créez une première partition de 2 Go de type Linux (n°83), et une seconde partition de 3 Go en NTFS (n°7)

    sudo fdisk /dev/sdb

    Command : n
    Select : p
    Partition number : 1
    First Sector : default
    Last Sector : 2G

    Command : n
    Select : p
    Partition number : 1
    First Sector : default
    Last Sector : 3G

### 4) A ce stade, les partitions ont été créées, mais elles n’ont pas été formatées avec leur système de fichiers. A l’aide de la commande mkfs, formatez vos deux partitions ( pensez à consulter le manuel !)

    sudo mkfs.ext4 /dev/sdb1
    sudo mkfs.ntfs /dev/sdb2

### 5) Pourquoi la commande df -T, qui affiche le type de système de fichier des partitions, ne fonctionne-telle pas sur notre disque ?

    Car notre disque dur n'est pas monté, et donc pas reconnu par le système.

### 6) Faites en sorte que les deux partitions créées soient montées automatiquement au démarrage de la machine, respectivement dans les points de montage /data et /win (vous pourrez vous passer des UUID en raison de l’impossibilité d’effectuer des copier-coller)

    sudo mkdir /data /win
    sudo nano /etc/fstab
        /dev/sdb1 / ext4 defaults 0 0
        /dev/sdb2 / ntfs defaults 0 0

### 7) Utilisez la commande mount puis redémarrez votre VM pour valider la configuration

    sudo mount -a
    sudo poweroff



## Exercice 2. Partitionnement LVM

### 1) On va réutiliser le disque de 5 Gio de l’exercice précédent. Commencez par démonter les systèmes de fichiers montés dans /data et /win s’ils sont encore montés, et supprimez les lignes correspondantes du fichier /etc/fstab

### 2) Supprimez les deux partitions du disque, et créez une patition unique de type LVM

