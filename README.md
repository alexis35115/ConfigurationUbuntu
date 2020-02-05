# Configuration machine Ubuntu


__CECI EST ENCORE UN DOCUMENT DE TRAVAIL__

Voici quelques instructions pour configurer une machine Ubuntu 18.04 LTS

commencer par : sudo apt update && sudo apt upgrade

## Programmes

### Nodejs et npm 
[Nodejs et npm](https://tecadmin.net/install-latest-nodejs-npm-on-ubuntu/

sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install nodejs

### Visual Studio Code

[Installer Visual Studio Code Ubuntu](https://code.visualstudio.com/docs/setup/linux)
[Exporter extension Visual Studio Code](https://stackoverflow.com/questions/35773299/how-can-you-export-vs-code-extension-list)


Installation : sudo snap install --classic code

configuration visual studio code??

extensions : 

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

### Git

[Configurations initiales Git](https://git-scm.com/book/fr/v2/Personnalisation-de-Git-Configuration-de-Git)

installation : sudo apt install git -y

Configuration : 
git config --global user.name "Alexis Garon-Michaud"
git config --global user.email "alexis_35115@hotmail.com"

### GitCola

sudo apt-get install git-cola

### Chrome

Installation : 
sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
[Installer Chrome](https://itsfoss.com/install-chrome-ubuntu/)

ajouter des favorits pour phpmyadmin? 

### LAMP (Linux Apache MySql PHP)

<https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/>

apache : sudo apt install apache2 -y

mysql : sudo apt install mysql-server -y

 pour phpmyadmin : https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-18-04    (ajouter la doc pour l'étape du user root et tout...) et activer phpmyadmin dans apache https://stackoverflow.com/a/13416092

phpmyadmin : sudo apt install phpmyadmin php-mbstring php-gettext -y    -> sudo phpenmod mbstring   -> sudo systemctl restart apache2

mot de passe : password

php et extensions : sudo apt install php7.2 libapache2-mod-php7.2 php-mysql -y


------ > dans /var/www/ créer un répertoire php et changer la sécurité  sudo chown -R $USER:$USER /var/www/html <https://askubuntu.com/questions/766041/cant-create-folder-or-document-in-var-www-html>


Faire un test d'être capable de me connecter à la base de données!

et l'Affaire de cache j'en parle pas.. manque d'autres trucs?

### Docker

https://phoenixnap.com/kb/how-to-install-docker-on-ubuntu-18-04 -> Alternative: Install Docker from Official Repository

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

### DockStation.io

https://www.techrepublic.com/article/how-to-install-dockstation-on-ubuntu19-04/

télécharger le .deb file et le mettre dans download
sudo dpkg -i dockstation*.deb    à partir du répertoire download
sudo apt-get install -f


### Virtual Box

<https://tecadmin.net/install-virtualbox-on-ubuntu-18-04/>

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"
sudo apt update
sudo apt install virtualbox-6.0

ESSAYER UNE vm

### Installer .net core 3.1

https://docs.microsoft.com/en-us/dotnet/core/install/linux-package-manager-ubuntu-1804

wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb

sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1

sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1

sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1

### Eclipse

<https://linuxize.com/post/how-to-install-the-latest-eclipse-ide-on-ubuntu-18-04/>

sudo apt install default-jre
sudo snap install --classic eclipse

### PostgresSQL

https://www.howtoforge.com/tutorial/how-to-install-postgresql-and-pgadmin4-on-ubuntu-1804-lts/

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

sudo apt update

sudo apt -y install postgresql postgresql-contrib

sudo su - postgres

psql

\password postgres   -> voir l'image <https://www.howtoforge.com/images/how_to_install_pgadmin4_on_ubuntu_1804_server/1.png>

j'ai mis le mot de passe "password"


RÉFÉRENCE : https://stackoverflow.com/questions/7695962/postgresql-password-authentication-failed-for-user-postgres ET https://www.liquidweb.com/kb/what-is-the-default-password-for-postgresql/

### PgAdmin

https://www.howtoforge.com/tutorial/how-to-install-postgresql-and-pgadmin4-on-ubuntu-1804-lts/


wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" >> /etc/apt/sources.list.d/pgdg.list'

sudo apt update

sudo apt install pgadmin4 pgadmin4-apache2 -y

postgres@localhost comme email po ur la connexion
pw = "password"

login page : http://localhost/pgadmin4 ET NON http://10.9.9.15/pgadmin4/

### MongoDB

à faire https://www.howtoforge.com/tutorial/install-mongodb-on-ubuntu/

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

### Jed

Install jed
Installing jed package on Ubuntu 14.04 (Trusty Tahr) is as easy as running the following command on terminal:

sudo apt-get update
sudo apt-get install jed

## TODOS

script de mise à jour? et validation de la configuration?

script pour printer la version des logiciels pour une comparaison facile?

script pour valider les services au démarrage?

script pour restarter les différents services? ou du moins la ligne de commande.

JE N'AI PAS LA BONNE VERSION DE NODEJS ???? JE VEUX LA LTS

voir le fuck quand je fais apt-get update avec les choses en double
seulement supprimer les lignes en doubles : <https://askubuntu.com/questions/760896/how-can-i-fix-apt-error-w-target-packages-is-configured-multiple-times>


avoir un repo bidon que je pourrais faire un git clone et tout pour valider le php et apache

installer -> https://github.com/microsoft/cascadia-code


faut que je valide mes trucs!!! 

## Résolutions de problèmes

### Réinitialiser son mot de passe root sous mysql

https://linuxconfig.org/how-to-reset-root-mysql-password-on-ubuntu-18-04-bionic-beaver-linux

### dsada

