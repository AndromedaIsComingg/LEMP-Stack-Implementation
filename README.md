# LEMP-Stack-Implementation

##### LEMP is a web stack which comprises of 
- LINUX Operating Ststem
- NGINX Web Server
- MySQL for Database Management
- PHP to Empower Server-side Functionality

It is similar to LAMP Stack with the major difference beineg that the web server in LAMP Stack, APACHE, is being replaced by NGINX.
We will start this implementation by launching a Linux Ubuntu operating system from our AWS EC2 compute service.

## AWS Account & EC2 Instance
###### Created an AWS Account and spinned an EC2 instance named `For Instance`
<img width="1280" alt="AWS Acct" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/14e2925b-50d3-4442-8bae-1dbc8768da8a">


## Private Key
###### Created and downloaded a private key named `1stkey`
###### The .pem file was saved in the "Downloads" folder as shown below

<img width="320" alt="pem file in dwnlds" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/d73e3fac-39ac-42ef-a5d3-844018d53cbe">


###### From Terminal, working directory was changed to the "Downloads" folder
<img width="272" alt="cd Downloads" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/f0d64650-0ac8-40d6-b2ae-5177940e2a91">

###### From Terminal, permission was changed for the private key.
<img width="412" alt="changing permission for private key" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/6890a6f6-da94-49d0-a2e5-cc5894f8888d">

## Connecting to the EC2 Instance
###### Connected to the EC2 instance by running the command `ssh -i <private-key-name>.pem ubuntu@<Public-IP-address>`
<img width="598" alt="starting ubuntu" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/26d1bd55-66c9-4463-b6f2-404f2108b137">

## Installing Nginx Web Server
The Nginx web server will serve to display the web pages to visitors,
in order to install this we will be using the apt package manager along side the sudo command so a to grant admin privilages.
The package was installed using the following command `sudo apt install nginx`
Please note that the `-y` flag is to handle future prompts

<img width="1280" alt="Nginx install" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/c04e87bf-e160-4555-875d-bb1815d75d4b">

## Verifying Nginx
The instalation of Nginx can be confirmed using the following command to be assured that it is running properly.
`sudo systemctl status nginx`

<img width="883" alt="Nginx status" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/ef0066b7-1e4e-4fa3-9d59-691664bc026b">

## Editing Inbound Rule
###### Edited inbound rule such that connection through port 80 is allowed and from any ip address.<img width="1271" alt="editing inbound rule" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/b90f17dd-51aa-422a-a2e3-f19a52b4b278">


## Accessing Server
##### Since our server is up and running we try to access it from our local machine and also from a web browser
Accessing via the local machine, we are going to access via the IP and also via DNS name both of which will be carried out with the "curl command"
Using the commands `curl http://127.0.0.1:80` `curl http://localhost:80`

<img width="747" alt="curl ip   DNS" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/4251e216-7135-4ed2-b2fc-3f8e65ced545">

We shall now be checking if the Nginx server can respond to internet requests via a web browser.
This will be done using the public IP.
We can use the following command to fetch the public IP from the local machine, instead of going on AWS EC2 instance using the command
'curl -s http://169.254.169.254/latest/meta-data/public-ipv4'

<img width="633" alt="public IP check" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/29264ebb-f743-4ac5-871d-f1c869395f58">

Now that we have the public IP, we can now use it with the following command to check if Nginx responds to internet requests.
Using a web browser, we will enter the public IP into the address bar with or without specifying port 80
this is because all web browsers use port 80 by default.

<img width="1023" alt="welcome Nginx" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/8473287b-8739-4ab1-8112-e966fcd6cf0f">


## Installing MySQL
###### Used apt to install this software using the command `sudo apt install mysql-server`
###### The sudo command gives admin previlages and when prompted, installation was confirmed by typing y and then pressing enter.
<img width="1222" alt="sudo MySQL install" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/82feb343-7c33-4cce-851c-0a29fd3d31df">


###### After installation, logged into the Mysql Console with the command `sudo mysql`
<img width="561" alt="MySQL Start up" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/605ca9d8-7387-493e-ab01-18536f1da7bd">


##### Password was set for root user using the command `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`
<img width="661" alt="user password" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/a8c63d47-187a-4499-8b24-adc24fe7a93e">


##### When done, tested to login into the MySQL console by using the command `sudo mysql -p`
##### The -p flag prompts for password after the root user password has been chnaged.
##### The "mysql> exit" command was used to exit the MySQL console.

<img width="580" alt="login test   exit" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/ed835c52-1429-4213-b3a9-4c8eac184d0c">

## Installing PHP
Now that we have Nginx to serve web services and MySQL to handle database,
we can now procede to install PHP to process code and generate dynamic content for the web server.
To use an Nginx server, we will need to install some external programs for it to communicate with PHP.
They are `php-fpm` (PHP fastCGI process manager) and `php-mysql`, a PHP module that helps PHP to communicate with MySQL-based database.
These two packages can be installed using the command `sudo apt install php-fpm php-mysql`
<img width="920" alt="two external progs" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/9251a042-9870-467c-924d-385420b4ce24">

## Configuring Nginx to Use PHP Processor
Similar to the use of virtual hosts in Apache, Nginx web server have server blocks can also be configured to accomodate configuration details
and host more than one domain on a single server.
To acheive this we will have to create a new working directory leaving var/www/html in its place as the default directory
which will be served if client's directory does match any other site.
we will name this directory "projectLEMP" which will be created with the following command `sudo mkdir /var/www/projectLEMP`

<img width="432" alt="mkdir projLEMP" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/794e7552-bc31-4f65-bf63-6a6e0df5e9ae">

Then we assign ownership which will reference to the current system user with the command `sudo chown -R $USER:$USER /var/www/projectLEMP`
<img width="524" alt="chown projLEMP" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/85868654-766a-4815-a4da-5aac9123cfd1">

Now using any command line editor, we will open a new configuration file in Nginx's site-available directory using the command
`sudo nano /etc/nginx/sites-available/projectLEMP`

