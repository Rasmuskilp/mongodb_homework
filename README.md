wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
The operation should respond with an OK.

However, if you receive an error indicating that gnupg is not installed, you can:

Install gnupg and its required libraries using the following command:

sudo apt-get install gnupg
Once installed, retry importing the key:

wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
2
Create a list file for MongoDB.
Create the list file /etc/apt/sources.list.d/mongodb-org-4.2.list for your version of Ubuntu.

Click on the appropriate tab for your version of Ubuntu. If you are unsure of what Ubuntu version the host is running, open a terminal or shell on the host and execute lsb_release -dc.

Ubuntu 18.04 (Bionic)	Ubuntu 16.04 (Xenial)
The following instruction is for Ubuntu 16.04 (Xenial). For Ubuntu 18.04 (Bionic), click on the appropriate tab.

Create the /etc/apt/sources.list.d/mongodb-org-4.2.list file for Ubuntu 16.04 (Xenial):

echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
3
Reload local package database.
Issue the following command to reload the local package database:

sudo apt-get update
4
Install the MongoDB packages.
You can install either the latest stable version of MongoDB or a specific version of MongoDB.

Install the latest version of MongoDB.	Install a specific release of MongoDB.
To install the latest stable version, issue the following

sudo apt-get install -y mongodb-org
