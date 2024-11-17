# Procedures :

+ Logged into out free tier root account and created a user and attached a inline policy providing ***AdministratorAccess*** as good practices.

IMG

+ Once user created, we can update the password in "Security Credentials" tab as show below

IMG

+ Then, logged into the user profile with the new creds and created a VPC.
  
+ Using "VPC and more" option, created 1 VPC with 1 Subnet of CIDR Range ***10.0.0.0/28*** in 1AZ.
  
IMG

+ A route table is also created along with the VPC and an internet gateway as well allowing ***0.0.0.0/0 (All ips - internet)***
  
  IMG

+ Then went to Ec2 and created EC2 instance with the below mentioned configurations :
    + Application and OS Images : Ubuntu
    + Instance Type : t2.micro
    + Keypair can be generated (.pem file for ubuntu and linux), but I prefer to use Instance connect for this case.
    + VPC : Given the VPC and subnet that was newly created
    + Auto-assign public IP : Enable
    + Check Create new Security group allowing ssh on port 22 and inbound from anywhere for this case.
    + boot storage options : default
    + Using advanced details drop down, provided user data to exexute while creation and booting of instance
      > sudo apt install apache2 -y
      > sudo apt update
    + No. of instance : 1

+ Then created the instance and go to the instance details and we can see the public ip address.
  
+  In the instance details page, give ***Connect***, Selected ***Instance Connect***.
  
+  Tried accessing internet : ping -c 3 www.google.com
Output : 
--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms

+
