# Documentation: Setting Up a Honeypot on Azure Using PuTTY and T-Pot

## Prerequisites
1. Azure account
2. PuTTY installed on your local machine

## Step 1: Create VM on Azure

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/f082d9f8-8dd7-4721-a9d8-bc9da9763bc4)

### 1.1 Create New Resource Group
- **Name:** Name your resource group

### 1.2 Configure VM Settings
- **Name:** Enter the name for the honeypot machine
- **Zone:** Select the zone closest to you
- **Image:** Debian 11 'Bullseye' -64 Gen2
- **Azure Spot Discount:** Check the box to reduce overall cost
- **Size:** Choose a size with recommended RAM size of 8GB

### 1.3 Authentication Type
- **SSH authentication**
- **Username:** Enter your username
- **Key Pair:** Name your key pair

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/ea1294be-4923-4889-ba05-0b1d4a154fd8)


### 1.4 Disks Options
- Create or attach a new 128GB disk

### 1.5 Networking Section
- Use the default settings

### 1.6 Management Section
- Enable auto shutdown function

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/990be06f-1de7-41f2-a71c-807a1c6cbc32)


### 1.7 Review and Create
- Review settings and click "Create"
- Download private key and save it

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/dce417f1-8f45-4e5b-8d5f-837060f503b2)


## Step 2: Configure Azure VM

### 2.1 Open All Ports
- Click Go to the resource of your VM

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/34175d56-ca75-43e5-9cf1-70c872bed1f1)


- Navigate to Networking settings
- Create inbound port rule to open all ports (0-65535)

## Step 3: Generate SSH Key Pair with PuTTYgen

### 3.1 Open PuTTYgen
- Load the private key file downloaded from Azure
- Generate the key pair
- Save the private key on your local machine

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/70514c9b-523e-4adc-80da-83e67279b233)


## Step 4: Connect to Azure VM Using PuTTY

### 4.1 Find VM IP Address
- Go to Azure portal > Overview section to find the IP address

### 4.2 Configure PuTTY
- Open PuTTY
- Enter VM IP address in the Host Name field
- Under Connection > SSH > Auth, browse and add the private key file

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/852cf780-a1b3-4c4f-b3d8-1697975c6ada)


### 4.3 Connect to VM
- Click "Open" to connect to the Azure VM
- Enter the username you selected during VM creation
- Update packages using `sudo apt-get update`

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/f32460af-5b37-4a19-ab77-d7812237d529)


## Step 5: Install T-Pot Honeypot

### 5.1 Clone T-Pot Repository
- Install Git: `sudo apt install git`
- Clone T-Pot repository: `git clone https://github.com/telekom-security/tpotce`
- Navigate to T-Pot installer directory: `cd tpotce/iso/installer/`

### 5.2 Run T-Pot Installer
- Run installer as root: `sudo ./install.sh --type=user`
- Follow the installation prompts and select a username/password

  if everything works upto now, you would have a screen like this

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/dc882a06-c09b-4f0c-9ffc-ca00b2953592)


## Step 6: Access T-Pot Dashboard

### 6.1 Open Browser
- Open a new tab in your browser
- Enter the URL format: `https://[Your IP Address]:64297`

  ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/c54a4f68-5125-4f61-a6a8-15a9d7072c4c)


## Conclusion
Congratulations! You have successfully set up a honeypot using T-Pot on an Azure VM. You can now monitor and analyze network attacks and security threats using T-Pot's dashboard and visualization tools.

## Demonstration 
- Demonstration of attack map, Elasticvue, dashboard, and T-Pot dashboard functionalities

### Attack Map
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/cf96d750-a7a7-424f-8195-ea86ee18c011)

### Elasticvue
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/8ad34b18-d83a-4c3e-afc7-ee8fbe372ffa)


### Dashboards
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/221990db-339f-42a7-9d8d-43150647819d)

### T-pot Dashboard
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/c0aaaa29-d666-4a4d-9e05-d61c16f19417)
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/d4d0d760-571e-44b0-993c-9a037e81da2d)
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/22d86f53-7d84-42af-b6f1-e7e68656e1f9)
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/43f7f8a3-0dc1-47a6-910a-37d482488ac5)

