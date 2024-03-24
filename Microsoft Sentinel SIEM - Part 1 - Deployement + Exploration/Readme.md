# Project: Microsoft Sentinel Deployment and Exploration

# Table of Contents
- [Part 1: Deployment and Configuration](#part-1-deployment-and-configuration)
  - [Introduction](#introduction)
  - [Prerequisites](#prerequisites)
  - [Deployment Steps](#deployment-steps)
    - [Access GitHub Template](#Access-Github-Template)
    - [Azure Portal Deployment](#azure-portal-deployment)
    - [Configuring Settings](#configuring-settings)
    - [Configuring Content Hub](#configuring-content-hub)
    - [Configuring Data Connector](#configuring-data-connector)
    - [Analytics Rules Setup](#analytics-rules-setup)
    - [Review and Deployment](#review-and-deployment)
  - [Post-Deployment Actions](#post-deployment-actions)
    - [Deployment Completion](#deployment-completion)
    - [Resolving Deployment Issues](#resolving-deployment-issues)
- [Part 2: Exploration](#part-2-exploration)
  - [Introduction](#introduction-1)
  - [Access Microsoft Sentinel](#access-microsoft-sentinel)
  - [Exploration Microsoft Sentinel](#exploration-microsoft-sentinel)
    - [Overview and System Status](#overview-and-system-status)
    - [Data Analysis using KQL](#data-analysis-using-kql)
    - [Data Connectors](#data-connectors)
    - [Analytics](#analytics)
  - [Conclusion and Next Steps](#conclusion-and-next-steps)


## Part 1: Deployment and Configuration

### Introduction

This part of the project focuses on deploying and configuring Microsoft Sentinel using the all-in-one template available on GitHub.

### Prerequisites

Ensure you have an active Azure subscription and a stable internet connection before proceeding.

### Deployment Steps

1. **Access GitHub Template:**
   - Go to the GitHub billing page provided in the project documentation.
   - Click on the Deploy button to start the deployment process.
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/96a9144d-9483-4eaf-b0c9-be416c8c3b5e)

2. **Azure Portal Deployment:**
   - You will be redirected to the Azure portal.
   - Enter location, Resource Group name, and workspace name.
   - In Microsoft Sentinel, set the data ingestion limit to 10 Gigabits per day (for free).
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/99a4a2df-e230-4b11-acb3-2d569f120605)

3. **Configurating Settings:** 
   - Enable Sentinel Health Diagnostics.
   - Select relevant options in Content Hub Solutions and Data Connector tabs.

4. **Configurating Content Hub:**
   - Select all available options for the sake of simplicity in this project.

5. **Configurating Data Connector:**
   - Choose modules for data ingestion, focusing on Azure Working Directory for sign-in and login data.

6. **Analytics Rules Setup:**
   - Enable all available analytics rules for threat detection.

7. **Review and Deployment:**
   - Review settings and click Create to deploy Microsoft Sentinel.
   ![Deployment Completion](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/dfd6c79d-13cd-423e-aafe-3bfc62a053eb)

### Post-Deployment Actions

1. **Deployment Completion:**
   - Wait for deployment to complete (approximately 15 minutes).
   ![Deployment In Progress](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/3e495c7e-6f71-4796-88c1-46650d313469)

2. **Resolving Deployment Issues:**

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/cf80f06b-a585-44b8-b0a7-f8f7012b760c)

After the deployment is completed, you may encounter failures or issues due to unlicensed modules. Follow these steps to resolve such issues:
   
   2.1. **Access Resource Group:**
      - Go to the Azure portal and navigate to the resource group associated with your project.
   
   2.2. **Select Resource:**
      - Select the resource with the same name as your project from the resource group.
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/a289728c-acf6-4b51-8330-ed17e455f774)

   2.3. **Configure Diagnostic Settings:**
      - In the left pane, click on Diagnostic settings.
      - Click on New diagnostic settings to create a new configuration.
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/1e8e18ac-57b6-4d9b-8a5f-db110513cf58)

   2.4. **Diagnostic Settings Configuration:**
      - Check the boxes for all logs and metrics.
      - Choose to send the diagnostics to the log analytics workspace.
      - Provide a name for the diagnostic settings.
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/2c153330-5381-4bfd-8281-bf746b41a664)

   2.5. **Save Configuration:**
      - Save the diagnostic settings configuration.

---

## Part 2: Exploration

### Introduction

This part focuses on exploring the features and capabilities of Microsoft Sentinel post-deployment.

### Access Microsoft Sentinel:
   - To open Microsoft Sentinel from the Azure portal, search for Microsoft Sentinel on search bar and select your project.

### Exploration Microsoft Sentinel 


1. **Overview and System Status:**
   - Explore the overview screen to understand system health and key metrics.
   ![Overview](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/2e45a002-a09d-49ba-ba50-467516baa4dc)
     
2. **Data Analysis using KQL:**
   - Use Kusto Query Language (KQL) to search and analyze data within logs and tables.
   ![KQL Data Analysis](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/73e8dd3a-b151-4d86-bd55-069f683279d6)
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/e3bbb2be-dfd3-4fc1-8b9e-07523eb207d7)

3. **Data Connectors:**
   - Explore Data Connectors to understand data sources.
     
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/2acd38e8-01f1-47c9-92d2-c9dc6102ade8)

   - Click on any data connector to see its details.
     
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/693a5d51-bce1-437f-b3ef-e61e0dc05084)

4.  **Analytics**
   - Navigate to the Analytics section to manage analytics rules and detections.
   
   ![Analytics](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/1d67a665-898d-47e1-a0c7-b4e4a8baab7c)

   - Most of them are from analytics rules, and were automatically deployed and enabled for you. Right now we have about 135 rules already ready for us (As seen in screenshot).

### Conclusion and Next Steps

This documentation provides a structured approach to deploying and exploring Microsoft Sentinel. Part 1 focuses on deployment steps and configuration settings, while Part 2 guides you through initial exploration and usage of Sentinel's features.
