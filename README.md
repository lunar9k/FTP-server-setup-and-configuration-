# FTP-server-setup-and-configuration-

The FTP (file tranfer protocol) is use for transter file between remote server and client 

## Installation

### Objective 
setup a linux server 
- SSL /TLS Integration
- support virtual user
- Limited bandwidth
- virtual IP configuration

Use `sudo apt install vsftpd` for installation vsftpd

Use `sudo systemctl status vsftpd` for check status of ftp server is running or not 

![Screenshot (40)](https://github.com/user-attachments/assets/873ed614-3a57-4ea0-9fb3-cc5074f01ccb)


## Configuration Firewall 
We have to configure firewall for security purpose , we have to open ports of server which use 20 & 21
for this we use UFW firewall in linux

* first we have to enable firewall
  we use this command `sudo ufw enable`
  ```
  sudo ufw allow 20/tcp
  sudo ufw allow 21/tcp
  sudo ufw allow 990/tcp
  sudo ufw allow 5000:10000/tcp
  ```
  for allow ports from firewall

## Configure users
we have to create users for specific purpose

- We have to host public Ftp server to download file
- We want to upload files to linux server for personal use and we would not have public user

* In first case we need to create an additional user and share its username and password with clients to access the files

use `sudo adduser ftpuser`for add user in server

![Screenshot (42)](https://github.com/user-attachments/assets/1b4f7c05-3e6f-41de-88ff-b9b3bba19ddd)

For security , we disable ssh permission for this user we have to configure this
for this we use `sudo nano /etc/ssh/sshd-config` add `Denyusers ftpuser` and save it

![Screenshot (44)](https://github.com/user-attachments/assets/33f489c7-19c9-4376-9a72-4427162412ec)
![Screenshot (43)](https://github.com/user-attachments/assets/d0992a3a-afba-408a-986e-8947e9350921)

Then we have ro restart SSH service using `sudo systemctl restart sshd`

## Create Ftp folder and set permissions
To create folder use `sudo mkdir /ftp` 
add this to configuration file 
![Screenshot (46)](https://github.com/user-attachments/assets/8c14d902-4247-4266-b5d4-1ee1120bd2fb)

## How to use FTP server 

for use ftp we have username and password or IP adress of server then we have to use `ftp IPADRESS` command in client machine

![Screenshot (47)](https://github.com/user-attachments/assets/fad10d38-f8c8-4fe5-886c-950f4167f310)


Then we free to access server and transfer files remotely

![Screenshot (48)](https://github.com/user-attachments/assets/d5bca0c9-d379-4a36-969e-90c9a3217b6b)









