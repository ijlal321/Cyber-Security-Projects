# Documentation: Setting Up a Honeypot on Azure Using PuTTY and T-Pot

## Prerequisites
1. Azure account
2. PuTTY installed on your local machine

## Step 1: Create VM on Azure

### 1.1 Create New Resource Group
- Name: [Name of your choice]

### 1.2 Configure VM Settings
- Name: [Enter name for honeypot machine]
- Zone: [Select zone closest to you]
- Image: Debian 11 'Bullseye' -64 Gen2
- Azure Spot Discount: Check the box to reduce overall cost
- Size: Choose a size with recommended RAM size of 8GB

### 1.3 Authentication Type
- SSH authentication
- Username: [Your username]
- Key Pair: [Name of your key pair]

### 1.4 Disks Options
- Create or attach a new 128GB disk

### 1.5 Networking Section
- Use the default settings

### 1.6 Management Section
- Enable auto shutdown function

### 1.7 Review and Create
- Review settings and click "Create"
- Download private key and save it

## Step 2: Configure Azure VM

### 2.1 Open All Ports
- Go to the resource of your VM
- Navigate to Networking settings
- Create inbound port rule to open all ports (0-65535)

## Step 3: Generate SSH Key Pair with PuTTYgen

### 3.1 Open PuTTYgen
- Load the private key file downloaded from Azure
- Generate the key pair
- Save the private key on your local machine

## Step 4: Connect to Azure VM Using PuTTY

### 4.1 Find VM IP Address
- Go to Azure portal > Overview section to find the IP address

### 4.2 Configure PuTTY
- Open PuTTY
- Enter VM IP address in the Host Name field
- Under Connection > SSH > Auth, browse and add the private key file

### 4.3 Connect to VM
- Click "Open" to connect to the Azure VM
- Enter the username you selected during VM creation
- Update packages using `sudo apt-get update`

## Step 5: Install T-Pot Honeypot

### 5.1 Clone T-Pot Repository
- Install Git: `sudo apt install git`
- Clone T-Pot repository: `git clone https://github.com/telekom-security/tpotce`
- Navigate to T-Pot installer directory: `cd tpotce/iso/installer/`

### 5.2 Run T-Pot Installer
- Run installer as root: `sudo ./install.sh --type=user`
- Follow the installation prompts and select a username/password

## Step 6: Access T-Pot Dashboard

### 6.1 Open Browser
- Open a new tab in your browser
- Enter the URL format: `https://[Your IP Address]:64297`

### 6.2 Explore T-Pot Dashboard
- Demonstration of attack map, Elasticvue, dashboard, and T-Pot dashboard functionalities

## Conclusion
Congratulations! You have successfully set up a honeypot using T-Pot on an Azure VM. You can now monitor and analyze network attacks and security threats using T-Pot's dashboard and visualization tools.