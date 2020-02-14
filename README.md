# Configuration machine Ubuntu

__CECI EST ENCORE UN DOCUMENT DE TRAVAIL__

Voici quelques instructions pour configurer une machine Ubuntu 18.04 LTS

commencer par : sudo apt update && sudo apt upgrade

## Programmes

### Node.js et npm

[Référence](https://tecadmin.net/install-latest-nodejs-npm-on-ubuntu/)

```sh
sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install nodejs
```

### Visual Studio Code

[Installer Visual Studio Code Ubuntu](https://code.visualstudio.com/docs/setup/linux)
[Exporter extension Visual Studio Code](https://stackoverflow.com/questions/35773299/how-can-you-export-vs-code-extension-list)

Installation :

```sh
sudo snap install --classic code
```

configuration visual studio code??

expliquer comment ajouter les extensions ???

extensions :

```sh
code --install-extension DavidAnson.vscode-markdownlint
code --install-extension DotJoshJohnson.xml
code --install-extension eamodio.gitlens
code --install-extension esbenp.prettier-vscode
code --install-extension Fudge.auto-using
code --install-extension jchannon.csharpextensions
code --install-extension k--kato.docomment
code --install-extension lihui.vs-color-picker
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-vscode-remote.remote-wsl
code --install-extension ms-vscode.csharp
code --install-extension ms-vscode.vs-keybindings
code --install-extension ms-vsliveshare.vsliveshare
code --install-extension msjsdiag.debugger-for-chrome
code --install-extension ritwickdey.LiveServer
code --install-extension spywhere.guides
code --install-extension VisualStudioExptTeam.vscodeintellicode
code --install-extension yzane.markdown-pdf
code --install-extension yzhang.markdown-all-in-one
code --install-extension Zignd.html-css-class-completion
```

"configuration du fichier json"?

AJOUTER CECI :
PHP Extension Pack
felixfbecker.php-pack
Felix Becker
1,156,771
Repository
License
Everything you need for PHP development

l'extension de docker aussi?

faudrait valider la liste des extensions, faudrait faire un ménage??

Expliquer comment installer snap?

### Git

Installation :

```sh
sudo apt install git -y
```

[Configuration](https://git-scm.com/book/fr/v2/Personnalisation-de-Git-Configuration-de-Git) :

```sh
git config --global user.name "Alexis Garon-Michaud"
git config --global user.email "alexis_35115@hotmail.com"
```

Pour ne pas avoir à saisir ton identifiant et son mot de passe sur Github lors d'un push. Il faut exécuter la [ligne](https://stackoverflow.com/a/35943882) ici-bas :

```sh
git config --global credential.helper store
```

### [GitCola](https://git-cola.github.io/)

```sh
sudo apt-get install git-cola
```

### [Chrome](https://www.google.com/intl/fr/chrome/)

[Référence](https://itsfoss.com/install-chrome-ubuntu/)

```sh
sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

### LAMP (Linux Apache MySql PHP)

<https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/>

apache : sudo apt install apache2 -y

mysql : sudo apt install mysql-server -y

 pour phpmyadmin : <https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-18-04>    (ajouter la doc pour l'étape du user root et tout...) et activer phpmyadmin dans apache <https://stackoverflow.com/a/13416092>

phpmyadmin : sudo apt install phpmyadmin php-mbstring php-gettext -y    -> sudo phpenmod mbstring   -> sudo systemctl restart apache2

mot de passe : password

php et extensions : sudo apt install php7.2 libapache2-mod-php7.2 php-mysql -y

------ > dans /var/www/ créer un répertoire php et changer la sécurité  sudo chown -R $USER:$USER /var/www/html <https://askubuntu.com/questions/766041/cant-create-folder-or-document-in-var-www-html>

Faire un test d'être capable de me connecter à la base de données!

et l'Affaire de cache j'en parle pas.. manque d'autres trucs?

### [Docker](https://www.docker.com/)

<https://phoenixnap.com/kb/how-to-install-docker-on-ubuntu-18-04> -> Alternative: Install Docker from Official Repository

installation :
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu  $(lsb_release -cs)  stable"
sudo apt-get update
sudo apt-get install docker-ce

Start and Automate Docker
The Docker service needs to be setup to run at startup. To do so, type in each command followed by enter:

sudo systemctl start docker
sudo systemctl enable docker

Créer le groupe de docker <https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket>

Create the docker group -> sudo groupadd docker
Add your user to the docker group -> sudo usermod -aG docker ${USER}
You would need to loog out and log back in so that your group membership is re-evaluated or type the following command-> su -s ${USER}
Verify that you can run docker commands without sudo -> docker run hello-world

docker compose :

sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

### [DockStation.io](https://dockstation.io/)

[Référence](https://www.techrepublic.com/article/how-to-install-dockstation-on-ubuntu19-04/)

Télécharger le .deb file et le mettre dans download

À partir du répertoire "Downloads" :

```sh
sudo dpkg -i dockstation*.deb
sudo apt-get install -f
```

### [VirtualBox](https://www.virtualbox.org/)

[Référence](https://tecadmin.net/install-virtualbox-on-ubuntu-18-04/)

```sh
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -

wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"

sudo apt update

sudo apt install virtualbox-6.0
```

### [Net Core 3.1](https://dotnet.microsoft.com/)

[Référence](https://docs.microsoft.com/en-us/dotnet/core/install/linux-package-manager-ubuntu-1804)

```sh
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

```sh
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

```sh
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

```sh
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

### [Eclipse](https://www.eclipse.org/downloads/packages/release/mars/r/eclipse-ide-java-developers)

[Référence](https://linuxize.com/post/how-to-install-the-latest-eclipse-ide-on-ubuntu-18-04/)

```sh
sudo apt install default-jre
sudo snap install --classic eclipse
```

_Prendre note que l'installation ajoute également le OpenJDK._

### [PostgreSQL](https://www.postgresql.org/)

[Référence](https://www.howtoforge.com/tutorial/how-to-install-postgresql-and-pgadmin4-on-ubuntu-1804-lts/)

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

sudo apt update

sudo apt -y install postgresql postgresql-contrib

sudo su - postgres

psql

\password postgres   -> voir l'image <https://www.howtoforge.com/images/how_to_install_pgadmin4_on_ubuntu_1804_server/1.png>

j'ai mis le mot de passe "password"


RÉFÉRENCE : <https://stackoverflow.com/questions/7695962/postgresql-password-authentication-failed-for-user-postgres> ET <https://www.liquidweb.com/kb/what-is-the-default-password-for-postgresql/>

### [PgAdmin](https://www.pgadmin.org/)

<https://www.howtoforge.com/tutorial/how-to-install-postgresql-and-pgadmin4-on-ubuntu-1804-lts/>


wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

sudo apt update

sudo apt install pgadmin4 pgadmin4-apache2 -y

postgres@localhost comme email po ur la connexion
pw = "password"

login page : <http://localhost/pgadmin4> ET NON <http://10.9.9.15/pgadmin4/>

### [MongoDB](https://www.mongodb.com/fr)

<https://www.howtoforge.com/tutorial/install-mongodb-on-ubuntu/>

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 68818C72E52529D4

sudo echo "deb http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list

sudo apt-get update

sudo apt-get install -y mongodb-org

sudo systemctl start mongod
sudo systemctl enable mongod

mongo

use admin

db.createUser({user:"admin", pwd:"password", roles:[{role:"root", db:"admin"}]})

user : admin
pw : password

sudo nano /lib/systemd/system/mongod.service
On the 'ExecStart' line 9, add the new option '--auth'.

ExecStart=/usr/bin/mongod --auth --config /etc/mongod.conf

sudo systemctl daemon-reload

pour se connecter :
mongo -u admin -p password --authenticationDatabase admin

### [Jed](https://www.jedsoft.org/jed/)

[Référence](https://zoomadmin.com/HowToInstall/UbuntuPackage/jed)

```sh
sudo apt-get update
sudo apt-get install jed
```

## Résolutions de problèmes

### Réinitialiser son mot de passe `root` sous mysql

<https://linuxconfig.org/how-to-reset-root-mysql-password-on-ubuntu-18-04-bionic-beaver-linux>, script à faire?

inclure le lien pour les lock lors des updates et celui des duplicates aussi

## TODOS

1. Script de mise à jour? et validation de la configuration?
2. Script pour printer la version des logiciels pour une comparaison facile
3. Essayer une vm
4. script pour valider les services au démarrage?
5. script pour restarter les différents services? ou du moins la ligne de commande.
6. voir le fuck quand je fais apt-get update avec les choses en double
seulement supprimer les lignes en doubles : <https://askubuntu.com/questions/760896/how-can-i-fix-apt-error-w-target-packages-is-configured-multiple-times>
7. avoir un repo bidon que je pourrais faire un git clone et tout pour valider le php et apache
8. installer -> <https://github.com/microsoft/cascadia-code>
9. faut que je valide mes trucs!!!
10. Inclure des procédures pour valider l'installation et tout?
11. script créer un logon dans mysql  https://www.a2hosting.com/kb/developer-corner/mysql/managing-mysql-databases-and-users-from-the-command-line
12. pour git inclure ça? https://stackoverflow.com/questions/10032461/git-keeps-asking-me-for-my-ssh-key-passphrase
13. procédure pour réinitialiser le mot de passe root sur LAMP, XAMP https://stackoverflow.com/questions/24566453/resetting-mysql-root-password-with-xampp-on-localhost/57073767 et https://linuxconfig.org/how-to-reset-root-mysql-password-on-ubuntu-18-04-bionic-beaver-linux
14. Corriger la résolution d'ubuntu à partir de Hyper-V https://metinsaylan.com/8991/how-to-change-screen-resolution-on-ubuntu-18-04-in-hyper-v/
