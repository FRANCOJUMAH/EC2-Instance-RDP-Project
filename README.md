# Ajira Cloud Computing Project


## 🎯 Task Overview

![image](https://github.com/FRANCOJUMAH/Creating-an-AWS-EC2-Instance-/blob/7f19c7ebde1540ea02377bb90e4616605f546a7e/resources/ec2.png)

- **This project involves launching a Windows EC2 instance, enabling Remote Desktop Protocol (RDP) access via security groups, and configuring Amazon SNS to send notifications. You will create an RDP server, configure network security, and use SNS to monitor or alert on instance state changes (e.g., stopping/starting) for a complete, managed remote environment**

## 📝 Project Steps

1. **Created the EC2 Instance (Windows)**
   - Log in to the AWS Management Console (https://signin.aws.amazon.com/), 
   ![image](https://github.com/FRANCOJUMAH/Creating-an-AWS-EC2-Instance-/blob/2efa99f82ef7d9d4d59a3921a3ef55a47846d58a/resources/Console.png)
   - Go to the EC2 Dashboard in the AWS Management Console and click "Launch Instance".
   - Name the instance ("tuko-kadi") and selected a Windows AMI (Microsoft Windows Server 2025 Base).
   - Choose an instance type, such as t2.micro (Free Tier eligible).
   - Create a new key pair, download the .pem file, and store it securely.
   - Under Network Settings, ensure "Auto-assign public IP" is enabled
     
2. **Configure Security Group for RDP**
   - After successful login. Go to console home where you get to see different AWS resources listed : VPC, IAM, EC2, RDS as shown in the image below
   - Create a new Security Group.
   - Add an inbound rule: Type: RDP, Protocol: TCP, Port Range: 3389, Source: "Anywhere" (0.0.0.0/0) for temporary testing.
   - Launch the instance.
   - Verify the instance is now created and running as shown below
   ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/2b71f92ed20cf1f7cf54005fa3ba7d2fe6107c02/images/tuko-kadi%20running.png)

3. **Connect via RDP**
   - Select the instance and click "Connect", then choose the "RDP client" tab.
   - Click "Download remote desktop file" to download the rdp client and use it to retrieve your password
   
     ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/2b58893ff5646086200b824811369486fab8f085/images/connect.png)
     
   - Click "Get password" and upload your .pem file to decrypt the password.
   - Download the RDP file, open it, and enter the decrypted password.
   
 ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/023afc66722fc36bbbbcf9b389f133511ed28e19/images/rdp%20file.png)
 
   - Double click the downloaded rdp file (tuko-kadi) and use the decrypted password to login
  ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/b2a7801b8f47e5ce1fc07a06b7a6d0efbcedee6c/images/Remote%20connection.png)
  
  - Now we have successfully connected to our ec2 instance which is running windows server 2025
  ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/b2a7801b8f47e5ce1fc07a06b7a6d0efbcedee6c/images/virtual%20WINserver.png)

  - You now realize that the public and private IP address of the remote server matches that of the ec2 instance created initially.
![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/3e6a06b2893c0cd21f3f3cf4a070549cd76abc1c/images/ip%20addr1.png)
![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/3e6a06b2893c0cd21f3f3cf4a070549cd76abc1c/images/ip%20addr2.png)
4. **Specify Instance name & type, AMI Image, Keypair**
   - Here you get to see if there are any running instances, key pairs, security groups, load balancers, Auto Scaling groups etc. 
   - Click on launch instance to create a new EC2 instance.
