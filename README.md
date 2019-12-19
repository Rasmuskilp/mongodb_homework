# this guide gives instructions on how to install mongodb on an VM ubuntu
## as is standard, you need vagrant and virtualbox installed in order to use vm
### start by creating a folder where you want to create the vagrant
- do vagrant init to initialise vagrant
## inside vagrantfile
- change config.vm.box to ubunutu/xenial64

### vagrant up to initialise the vm
- vagrant up
#### vagrant ssh to enter the ubuntu vm
- vagrant ssh
### you can enter this commands manually inside ubuntu but in order to automate
- create  a provision.sh file
###
- add provision shell with provision.ph path inside vagrantfile
### inside provison.sh add these commands:
- wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
sudo apt-get update
sudo apt-get install -y mongodb-org
sudo service mongod start
## by doing this you should have successfully automated the mongodb installation
## process inside a vm ubunu
# to get the ip Change
### from inside ubuntu copu the mongod.conf file to to the project
### manually make the necessary Changes
## then the task is to link the mongod.conf file on windows into ubunutu
### do synced folder on vagrantfile
-     config.vm.synced_folder "environment/db", "/home/ubuntu/environment"
## on provision use this command to link the mongod.conf files
- sudo ln -s /home/ubuntu/environment/mongod.conf /etc/mongod.conf
