
# Project Title: Password Manager Hosted in the Cloud

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Deployment Steps](#deployment-steps)
   - [3.1 Setting Up Passbolt on AWS](#setting-up-passbolt-on-aws)
   - [3.2 Configuring HTTPS for Secure Communication (Optional)](#configuring-https-for-secure-communication-optional)
   - [3.3 Passbolt Configuration](#passbolt-configuration)
4. [Project Closure](#project-closure)
5. [Conclusion](#conclusion)
6. [Additional Notes](#additional-notes)
7. [Working Demonstration](#Working-Demonstration)


### **1. Introduction<a name="introduction"></a>**

This document provides a detailed guide on deploying Passbolt, an open-source password manager, on Amazon Web Services (AWS). The deployment includes setting up Passbolt on an EC2 instance, configuring HTTPS for secure communication, connecting the instance to an Ubuntu machine, and finally, cleaning up AWS resources to avoid unnecessary charges.


### **2. Prerequisites<a name="prerequisites"></a>**

Before starting the deployment process, ensure you have the following prerequisites:

- An AWS Account with appropriate permissions to create EC2 instances.
- Ubuntu Installed on VMware or Virtual Box for managing the EC2 instance.
- (Optional) A domain name from a registrar like Namecheap for SSL configuration and accessibility.


### **3. Deployment Steps<a name="deployment-steps"></a>**
Certainly! Here's the improved formatting of the section "3.1 Setting Up Passbolt on AWS":

### **3.1 Setting Up Passbolt on AWS<a name="setting-up-passbolt-on-aws"></a>**

1. Visit the Passbolt official website and navigate to the AWS section under Getting Started.

   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/060b3d72-43f1-4c54-94e6-3f3531d1f003)

2. This will lead us to AWS Marketplace. Click Continue to subscribe.

   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/4976ab8f-93f7-4036-a3c8-e9076153ac2b)

3. Subscribe to Passbolt (the software is free, but there may be infrastructure costs) and choose a region that is geographically close to your location.

   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/89ceea9e-b892-4c4f-b8ef-e67be114d5f4)

4. Configure the instance settings and launch a new instance based on the seller's settings.

5. Create an EC2 key pair for authentication. Use `ssh-keygen` on Ubuntu to generate keys and import the public key to AWS.

   - Click "Create New" based on Seller Settings.

     ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/82373a5e-12a5-435b-832e-eeb645484e1b)

   - Put a name and description on it and just save it for now.

   - Go to key pair settings, where we will create an EC2 key pair. It has a public key and a private key that are used to authenticate your access to the system.

     ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/52ec0702-c4e0-48ba-b632-8b462042187e)

   - Click on "Import Key Pair" from the action buttons on the top right. Enter the name and public key. To create a public-private key pair, use the `ssh-keygen` command on your Ubuntu machine.
   
     ```
     Ssh-keygen
     ```

     Provide a location for the key to save (press enter for the default location). Press enter again, and your key will be saved. If you already have a key saved, you can choose to overwrite it.

     ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/8067aee2-82b7-4b39-a197-9f1cf6f50aec)

   - Use `cat` to open your key, copy the key, and paste it into AWS.

     ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/8e78209f-d9d8-49df-8aa6-4f0e4607ec7f)

   - Click on "Import Key Pair" in AWS.

     ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/b4a9a9f4-e04a-45ce-9e46-8b579d43c8f9)

   - Remember to select the key from the key pair settings.

     ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/0946fd47-6e7e-47cd-98e0-8762de248acf)

6. Launch the EC2 instance and wait for it to initialize.

#### **3.2 Configuring HTTPS for Secure Communication (Optional<a name="configuring-https-for-secure-communication-optional"></a>)**

1. Access the EC2 instance using its public IPv4 address (Put IPv4 in a new Tab). You will reach this page.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/7cb60b0b-5b99-4ae3-84a2-0fa6e591850e)

2. Start the HTTPS configuration process in Passbolt. If using a domain, configure SSL accordingly (optional but recommended for security).
3. Connect the EC2 instance to your Ubuntu machine using SSH.

Now we have everything set up and ready to configrure.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/00b87c77-2167-40c5-a817-9eb57b749382)


#### **3.3 Passbolt Configuration<a name="passbolt-configuration"></a>**

1. Start the Passbolt configuration from the web interface.
2. Enter the server name, email, and skip SMTB configuration (if not needed).
3. Download and install the Passbolt extension for your browser.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/446fec87-b57d-4369-b31f-94a939a6e78d)

4. Create and manage passwords by clicking on create new on top left.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/bb4c7991-bf16-41a0-aa30-a9a726b3dccd)

5. Use Entension to Autofill your passwords.


### **4. Project Closure<a name="project-closure"></a>**

To avoid unnecessary charges, it's crucial to clean up AWS resources after completing the project. Follow these steps:

1. Log in to the AWS Management Console.
2. Navigate to the EC2 Dashboard.
3. Terminate the EC2 instance created for Passbolt deployment.
4. Ensure all associated resources (e.g., security groups, key pairs) are also deleted or disassociated.


### **5. Conclusion<a name="conclusion"></a>**

By following this documentation, you have successfully deployed Passbolt on AWS, configured HTTPS for secure communication, and managed the Passbolt configuration. Remember to regularly update and maintain your Passbolt instance for optimal security and performance.


### **6. Additional Notes:<a name="additional-notes"></a>**

- For detailed instructions and troubleshooting tips, refer to the official Passbolt documentation and AWS documentation.
- Regularly back up Passbolt data to prevent data loss.
- Monitor AWS billing to avoid unexpected charges, especially if you have enabled additional services or resources.

### **7. Working Demonstration:<a name="Working-Demonstration"></a>>**

1. Navigate to the desired website (e.g., TalentLMS) where you intend to store your credentials.


![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/7e05bd69-3837-427f-816e-90781577d48a)


2. Choose the option to create a new credential. Enter the Name, Username, and Password according to your preferences, then save the credentials.


![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/3e68a09e-f593-4d8e-8e7f-1996efe81174)


![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/1c76f034-852d-4ded-8319-92f9aa7df3bd)


3. Verify your identity by entering your passphrase.

4. Congratulations! Your password has been successfully saved. You will automatically login next time you visit your website.


![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/f86e8a31-dc85-4e66-a5fa-55fe318ce58f)



This documentation provides a comprehensive guide for deploying Passbolt on AWS, ensuring secure communication, and properly closing the project to avoid unnecessary costs. Adjustments can be made based on specific requirements or preferences during implementation.
