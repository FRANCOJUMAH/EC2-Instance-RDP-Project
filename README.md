# Ajira Cloud Computing Project


## 🎯 Task Overview

![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/a28a5e4d5e8199f5405c1114de3e82c93bcb1a18/images/ec2%20rdp.png)

- **This project entails launching a Windows EC2 instance, enabling Remote Desktop Protocol (RDP) access via security groups, and configuring Amazon Cloudwatch for Monitoring & Amazon SNS to send notifications.**
-  _Create an RDP server, configure network security, and use SNS to monitor or alert on instance state changes (e.g., stopping/starting) for a complete, managed remote environment_

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
 
   - Double click the downloaded rdp file _(tuko-kadi)_ and use the decrypted password to login
  ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/b2a7801b8f47e5ce1fc07a06b7a6d0efbcedee6c/images/Remote%20connection.png)
  
  - Now we have successfully connected to our ec2 instance which is running windows server 2025
  ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/b2a7801b8f47e5ce1fc07a06b7a6d0efbcedee6c/images/virtual%20WINserver.png)

  - You now realize that the _public-IP (13.220.42.226)_ and _private-IP (172.31.10.27)_ address of the remote server matches that of the ec2 instance created initially.
![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/3e6a06b2893c0cd21f3f3cf4a070549cd76abc1c/images/ip%20addr1.png)
![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/3e6a06b2893c0cd21f3f3cf4a070549cd76abc1c/images/ip%20addr2.png)

4. **Enable SNS Notifications**
 - Create Topic: Navigate to Amazon SNS, click "Topics" -> "Create topic" (Standard type). Name it _(tuko-kadi)_ and create the topic.
     ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/25bb7229c72f024dd68063cef500c33d75445435/images/create%20SNS%20topic.png)

 - Create Subscription: Within the topic, create a subscription, choose "sms" as the protocol, and enter your number as the endpoint for receiving SNS notifications
     ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/25bb7229c72f024dd68063cef500c33d75445435/images/create%20subscription.png)
     
 - The SNS topic _(tuko-kadi)_ is now created with SMS as the subscription as shown below
     ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/25bb7229c72f024dd68063cef500c33d75445435/images/SNS%20topic.png)
     
 5. **Create Alarm**
  - Create Alarm: Navigate to Cloudwatch, click "Alarms" -> "Create alarm" 
  -  Specify the metric (CPUUtilization) set to a threshold of greater than 0.01 within an average period of 10 seconds
  -  Configure the actions (step 3): state - in alarm, send a notification to the created SNS topic _(tuko kadi)_
    
  ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/46ed1fe3c14656c741fb1c2f987be07e2db1f974/images/Configure%20actions.png)

  -  Add alarm name(step 4) - (_tuko-kadi-alarm_). then proceed to create the alarm
  -  Confirm the alarm is created successfully with the SNS topic, alarm, metric and threshold set correctly.
     ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/ea5bcca1033e009ab3b061cdc8ae458600cb4ee3/images/alarm%20created.png)

  6. **Verify and Test**
     - Verify and test that the alarm is working.
     - To achieve this, reboot the ec2 instance and wait for the alarm notification on the phone via sms
       
                       **SNS alerts were successfully delivered through SMS as seen in the image below**
        ![image](https://github.com/FRANCOJUMAH/EC2-Instance-RDP-Project/blob/d6a0b15ef24ea474da4cc0979a1dc6550a02595f/images/sms-confirmation.jpg)

     
    **Summary of AWS Services Used**
     - EC2: Hosting the Windows RDP server.
     - Security Groups: Acting as a firewall to allow RDP traffic on port 3389.
     - Amazon Cloudwatch : Create alarms based on the defined metrics
     - SNS: Sending sms alerts for instance state changes.
  
    



  
