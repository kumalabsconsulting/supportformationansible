---
title: CheatSheet k3s
#weight: 3100
---


### K3s Cheatsheet

Ajout d'un disque pour un k3s :
```bash
## TITITITI
journalctl --vacuum-size=200M # Vider le journal systèmedf -h|more
k3s crictl rmi --prune # vide les images inutiliséescd ../
cfdisk /dev/sdb # vérifie que le disk /dev/sdb existecat /etc/fstab
df -h|more
pvcreate /dev/sdb # création du physical volumevgcreate VG-RANCHER /dev/sdb # création du Volume Groupelvcreate -n lv-k3s -l 100%FREE VG-RANCHER # création du logical Volumemkfs -t ext4 /dev/mapper/VG--RANCHER-lv--k3s # Formatage en ext4mkdir /mnt/temp # Création d'un rep temporaire pour y monter dedans le nouveau logical volumemount /dev/mapper/VG--RANCHER-lv--k3s /mnt/temp/ # montage du logical volumedf -h # Vérification###### Sur LEns faire un DRAINE du noeud/usr/local/bin/k3s-killall.sh # Arrêt complet de kubernetesdf -hlsof /var/lib/rancher # Vérification qu'aucun processus réclame ce répertoirersync -av --progress /var/lib/rancher/* /mnt/temp/ # Copie/Collerdu -sh /mnt/temp/
du -sh /var/lib/rancher/
rm -rf /var/lib/rancher/*
df -humount /mnt/temp
mount /dev/mapper/VG--RANCHER-lv--k3s /var/lib/rancher
ll /var/lib/rancher
df -hsystemctl restart k3s
vi /etc/fstab # on edite le fichier pour y insérer définitivement le monage du logical volume
```