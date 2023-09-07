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

## Verifying NGINX
The instalation of Nginx can be confirmed using the following command to be assured that it is running properly.
`sudo systemctl status nginx`

<img width="841" alt="Nginx Check" src="https://github.com/AndromedaIsComingg/LEMP-Stack-Implementation/assets/140917780/898e0a85-6602-438c-84fc-8c107a068b8c">

## Editing Inbound Rule
###### Edited inbound rule such that connection through port 80 is allowed and from any ip address.<img width="1271" alt="editing inbound rule" src="https://github.com/AndromedaIsComingg/Lamp-Stack-Implementation/assets/140917780/b90f17dd-51aa-422a-a2e3-f19a52b4b278">




