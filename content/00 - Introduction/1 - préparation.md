---
title: 1 - Préparation de l'environnement
weight: 011
draft: no
---


<td>&nbsp;</td>


----------



Toutes nos formations sont accompagnées par des environnements à base de :
  * Soit de Ubuntu 22.04 LTS Servers (Cloud-init version)
  * Soit de Debian Bullseye server (Cloud-init version)

## Formation à distance - accéder à une machine distante grâce à Guacamole

Dans le cadre d'une formation à distance, toutes les VM sont installé avec chacune leurs propre serveur Guacamole.


### Instructions pour toutes plateformes avec un desktop

- Lancez votre navigateur, Chrome, Firefox ou Brave
    - Connectez-vous à votre environnement grâce à votre trigram =>  `https://trigram.sc.kumalabs.consulting`
    - Tapez le login => `bdxuser`
    - Tapez le mot de passe `Bdx33;;`


### Une fois sur la session linux desktop distante

 - Conseil: mettez votre navigateur en plein écran (nous ferons tout sur la machine distante)
 - Prenez vos notes avec l'outils de text disponible dans votre bureau distant


## Formation présentiel
Dans le cadre d'une formation présentielle dans vos locaux, il y a deux possibilités:
  * Votre service IT repecte nos prérequis pour une accès aux environnements que nous vournissons
  * Vous avez des impératifs de sécurités, vous préférez gérer l'environnement de formation au sein de votre réseau.

### Prérequis d'accès à nos environnements de formation
 il faut vérifier que vos firewall laissent passer les flux suivants vers l'extérieur.

| **Source**   | **Protocol** | **Port** | **Destination**       | **Protocol** | **Port** | **Comments**                            |
|:------------:|:------------:|:--------:|:---------------------:|:------------:|:--------:|:---------------------------------------|
| VM formation | TCP          | Any      | fr.archive.ubuntu.com | TCP          | 80/443   | HTTP/HTTPS Acces to Ubuntu repositories |
| VM formation | TCP          | Any      | security.ubuntu.com   | TCP          | 80/443   | HTTP/HTTPS Acces to Ubuntu repositories |
| VM formation | TCP          | Any      | deb.debian.org        | TCP          | 80/443   | HTTP/HTTPS Acces to Ubuntu repositories |
| VM formation | TCP          | Any      | *.kumalabs.consulting | TCP          | 80/443   | HTTP/HTTPS to our domain                |

**Note**
https://tableconvert.com/markdown-generator


### Vous fournissez l'environnement de formation
Votre service IT devra quand même respecter ces prérequis:


| **Source**   | **Protocol** | **Port** | **Destination**       | **Protocol** | **Port** | **Comments**                                 |
|:------------:|:------------:|:--------:|:---------------------:|:------------:|:--------:|:--------------------------------------------|
| VM formation | TCP          | Any      | fr.archive.ubuntu.com | TCP          | 80/443   | HTTP/HTTPS Acces to Ubuntu repositories      |
| VM formation | TCP          | Any      | security.ubuntu.com   | TCP          | 80/443   | HTTP/HTTPS Acces to Ubuntu repositories      |
| VM formation | TCP          | Any      | deb.debian.org        | TCP          | 80/443   | HTTP/HTTPS Acces to Ubuntu repositories      |
| VM formation | TCP          | Any      | *.kumalabs.consulting | TCP          | 80/443   | HTTP/HTTPS to our formation website supports |



#### Dans le cadre de l'utilisation de votre poste de travail - importer une machine Linux virtualbox

- Récupérez une machine virtualbox ubuntu ou xubuntu (22.04) desktop: vous pouvez en récupérer sur le net par exemple [ici](https://www.osboxes.org/ubuntu/)
- Configurez la avec 4Go de RAM minimum (8Go si possible) et et 2 à 4 processeurs. sur votre poste de travail. 
- Démarrez la machine

#### Dans tous les cas, veuillez installer les prérequis suivants

- Faites les mises à jours (`sudo apt update` et `sudo apt upgrade -y`)
```bash
sudo apt update
sudo apt upgrade -y
```
- Installez quelques paquets:
```bash
sudo apt install -y git curl wget
```
- Installez docker via https://github.com/kumalabsconsulting/install-docker.git (utilisez le fichier install_docker.sh $USER)
```bash
git clone https://github.com/kumalabsconsulting/install-docker.git
cd install-docker
./install_docker.sh $USER
```


### Installer quelques logiciels (dans le cas d'une machine vierge Ubuntu)

- Installez VSCode avec le gestionnaire de paquet snap : `snap install code --classic`
```bash
snap install --classic code
```
- Puis installez quelques extensions qui pourraient vous interesser
```bash
## Commons extensions
code-server --install-extension  mhutchie.git-graph
code-server --install-extension  redhat.vscode-yaml
code-server --install-extension  mechatroner.rainbow-csv
code-server --install-extension  formulahendry.auto-close-tag
code-server --install-extension  formulahendry.auto-rename-tag
code-server --install-extension  anteprimorac.html-end-tag-labels
code-server --install-extension  abusaidm.html-snippets
code-server --install-extension  sndst00m.vscode-native-svg-preview
code-server --install-extension  pranaygp.vscode-css-peek
code-server --install-extension  anseki.vscode-color
code-server --install-extension  ms-azuretools.vscode-docker
# themes
code-server --install-extension  armandphilippot.coldark
code-server --install-extension  RobbOwen.synthwave-vscode
code-server --install-extension  nadim-vscode.infinity-dark-theme
code-server --install-extension  emroussel.atomize-atom-one-dark-theme
code-server --install-extension  teabyii.ayu
code-server --install-extension  wesbos.theme-cobalt2
code-server --install-extension  github.github-vscode-theme
code-server --install-extension  armandphilippot.coldark
code-server --install-extension  radiolevity.search-lights
code-server --install-extension  vladeeg.vscode-theme-vlight
code-server --install-extension  akamud.vscode-theme-onelight
code-server --install-extension  akamud.vscode-theme-onedark
code-server --install-extension  rubjo.ultimate-dark-neo
code-server --install-extension  sainnhe.edge
code-server --install-extension  circleci.circleci
code-server --install-extension  lakshitsomani.best-themes-redefined
code-server --install-extension  usernamehw.prism
# icons
code-server --install-extension  emroussel.atom-icons
code-server --install-extension  laurenttreguier.vscode-simple-icon
```
- Installez quelques navigateurs avec le gestionnaire de paquet snap
```bash
snap install brave
snap install firefox
snap install chrome
```
- En ligne de commande (`apt`) installez `htop`, `ncdu`
```bash
sudo apt install -y htop ncdu jq
```



