# Part 2: Demonstrating Cybersecurity Operations in SIEM

## Table of Contents
1. [Enable Artificial Intelligence in SIEM](#1-enable-artificial-intelligence-in-siem)
2. [Create Watchlist to Detect Cybersecurity Threats](#2-create-watchlist-to-detect-cybersecurity-threats)
3. [Create Detection Rule for Cybersecurity Threat](#3-create-detection-rule-for-cybersecurity-threat)
4. [Create User Account in Azure for SIEM Investigation](#4-create-user-account-in-azure-for-siem-investigation)
5. [Infiltrating User Account to Generate Incidents in SIEM](#5-infiltrating-user-account-to-generate-incidents-in-siem)
6. [Exploring Created Cybersecurity Incidents in SIEM](#6-exploring-created-cybersecurity-incidents-in-siem)
7. [How to Investigate Cybersecurity Incidents in SIEM](#7-how-to-investigate-cybersecurity-incidents-in-siem)
8. [Remediate Cybersecurity Incident](#8-remediate-cybersecurity-incident)



## 1. Enable Artificial Intelligence in SIEM

In this demonstration, we will enable Artificial Intelligence (AI) features in Microsoft Sentinel to detect unusual behaviors within our system. This functionality enhances the capability of our SIEM to proactively identify potential cybersecurity threats.

### Steps to Enable AI in Microsoft Sentinel
1. **Access Microsoft Sentinel Settings:**
   - Open Microsoft Sentinel and navigate to the settings section in the left pane.
  
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/eb9b4dda-4948-4757-ae97-90b9c9b7818a)


2. **Enable User and Entity Behavior Analytics (UEBA):**
   - Within the settings, click on "Settings" again.
   - Locate and select "User and Entity Behavior Analytics (UEBA)."
   - Apply UEBA to existing data sources for comprehensive monitoring.
  
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/e1164881-0bc6-4b8e-b440-189fab39a0a7)


3. **Configure Playbook Permissions:**
   - To fully utilize AI capabilities, enable Playbook permissions.
   - Click on "Configure permissions" in the Configure permissions drop-down menu.
   - Choose the appropriate resource group where Microsoft Sentinel is deployed.
   - Confirm and apply the changes to enable Playbook permissions for AI-driven automation.

   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/b2390080-951a-4d2a-93da-8c9f0f96ee5b)



## 2. Create Watchlist to Detect Cybersecurity Threats

In this demonstration, we will create a watchlist in Microsoft Sentinel to monitor Tor exit nodes' IP addresses, enhancing our ability to detect cybersecurity threats associated with Tor network usage.

### Steps to Create Watchlist

1. **Add New Watchlist:**
   - Navigate to the watchlist section in the left menu of Microsoft Sentinel.
   - Click on "Add new" to create a new watchlist.
   - Provide a name and an alias for the new watchlist.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/efa625e1-1217-4751-a78e-18f90b90b8ba)


2. **Configure Source and Search Key:**
   - For the source file, upload the Tor exit nodes' IP addresses file provided.
   - Ensure to optimize query performance by adding a search key.
  
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/d6e204b5-9078-4903-b82d-fb4fd48ca164)


3. **Review and Create:**
   - Proceed to the review and create section.
   - Click on "Create" to finalize the creation of the watchlist.
   - After creation, wait for a moment, and you will see the newly created watchlist in the watchlist section.

4. **View Watchlist Logs:**
   - Click on the created watchlist and select "View in logs" to see the results of the KQL query run by Microsoft.
  
   ![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/70d5ef53-5c6b-4c20-8c1f-7915e442982a)


5. **Modify Watchlist (Optional):**
   - Watchlists in Microsoft Sentinel are easily modifiable.
   - To update watchlist items, go to the watchlist section, click on "Update watchlist," and then select "Edit watchlist items" to add, update, or delete IP addresses from the Tor IP address list.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/52b7769c-b136-459e-89fe-9c1d6fb2810e)



## 3. Create Detection Rule for Cybersecurity Threat

In this demonstration, we will create a detection rule in Microsoft Sentinel to monitor threats originating from the Tor network. This rule will leverage the watchlist we previously created to enhance threat detection capabilities.

### Steps to Create Detection Rule
1. **Access Configuration and Analytics:**
   - Navigate to the configuration section and click on "Analytics" in Microsoft Sentinel.
  
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/68f96395-3a8e-4142-aaa9-d81aa2b4b7f7)

2. **Create Scheduled Analytics Rule:**
   - Click on "Create" and select "Scheduled" for the rule type.

3. **Configure Rule Details:**
   - Provide a name, proper description, and select tactics and techniques for the rule.
   - Choose "External Remote Services" as the initial access tactic.
   - Set severity from medium to high.
  
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/d617bb15-ac3e-4a08-a16d-0d61f78e32e5)


4. **Set Rule Logic (KQL Query):**
   - Use the following KQL query to define the rule logic:
     ```kql
     let TorNodes = (_GetWatchlist('Tor-Ip-Addresses') | project TorIp = IpAddress);
     SigninLogs 
     | where IPAddress in (TorNodes)
     | where ResultType != 50126
     ```
   - The key point is that 50126 specifically represents failed sign-in attempts due to invalid user credentials .
     

5. **Configure Entities:**
   - Entity are onjects in Microsoft Sentinel which represent important information such as Ip addresses , host, users etc. 
   - Add two different identities: Account (select sid and userID) and User IP Address and other as shown in Screenshot below.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/7b76ec83-0af5-43ca-8a7e-247048b3ad3d)


6. **Set Query Scheduling:**
   - Choose the frequency to run the query, such as every 5 minutes.

7. **Configure Incident Settings:**
   - Turn on the "Alert grouping" option to manage incident grouping.
   - We can see that up to only 150 alerts can be grouped into a single incident. if there are more than 150 then a new new incident will be created for it. 

8. **Review and Create:**
    - Proceed to the review + create option and click on "Create" to finalize the creation of the analytics rule.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/cbab47b6-3891-459a-9a4a-ebc64a298490)


## 4. Create User Account in Azure for SIEM Investigation

### Introduction
In this demonstration, we will create a new user account in the Azure environment specifically for SIEM investigation purposes. This account will be used to simulate unusual activity for testing and analysis within Microsoft Sentinel.

### Steps to Create User Account
1. **Turn Off Security Defaults in Azure Active Directory:**
   - Search and navigate to Microsoft Active Directory from the search bar in Azure.
   - Go to the Properties tab and select "Manage security defaults."
   - Turn off security defaults and provide a reason, such as testing. Save the changes.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/8352c492-61f3-4f9f-a741-3de02372071c)


2. **Create New User in Azure:**
   - Go to the Users section from the left tab in Azure and click on "Create new user."
   - Provide an appropriate username, display name, and proceed to Next: Properties.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/810f3a40-7fe4-4c76-bd47-6e5b05f2b2f4)


3. **Fill Basic Details:**
   - Fill in all the basic details as shown in the Properties tab for the new user account.
   - Proceed to Review + Create, and copy the user principal name and password for future use.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/2abb1753-ff30-41b4-97e8-ff692db8933e)


4. **Assign Roles to the User:**
   - Add Azure AD role:
     - Click on the newly created account and navigate to Assigned roles.
     - Click on "Add assignments" and assign the role of Security Reader.
   - Add Azure role (Contributor):
     - Open your Microsoft Sentinel resource group and click on Access control (IAM).
     - Click on "Add" and select "Add role assignment."
     - Choose "Contributor" from the role section and select the newly created user.
     - Save the role assignment.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/28e6f7b8-8eba-4ce2-ab2c-6ef9d74eeddb)


5. **Login Using New Account:**
   - Open a new window and log in to the Microsoft account and Azure portal using the newly created user account.
  
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/fcf2dce7-025a-4b48-87e8-94d14e05ce58)


By following these steps, you have successfully created a user account in Azure dedicated to SIEM investigation in Microsoft Sentinel. This account can be used to simulate unusual activity for testing and security analysis purposes.


## 5. Infiltrating User Account to Generate Incidents in SIEM 
Once you got log in, you can do some infiltrations in your own, make some changes, and we will discuss tits impact on next section.


## 6. Exploring Created Cybersecurity Incidents in SIEM 
    - Right off the bat ,we see we have about 17 new incidents, lets explore them.
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/7c164693-dc63-49cd-a8e8-021968d75b24)

    - Click on incidents, from left tab, and you will see details of all the incidents

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/435a7e47-fb0b-4987-8a68-5b6f2e7f7adf)

## 7. How to Investigate Cybersecurity Incidents in SIEM

This section outlines the steps to investigate cybersecurity incidents within a SIEM (Security Information and Event Management) system. Effective investigation is crucial for understanding the nature of incidents and identifying potential threats.

### Steps to Investigate Cybersecurity Incidents

1. **Access Incidents Section:**
   - Navigate to the Incidents section in your SIEM platform.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/7f41439b-38d1-4b03-95ed-8dc27ddbf7cd)


2. **Select Incident for Investigation:**
   - Click on a specific incident, preferably a successful sign-in incident, from the list of incidents.
   - On the left side of the incident view, you will see essential details about the incident, including severity, description, affected entities, timestamp, and status.
   - Click on a event to view further details related to the incident.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/a7be89af-e49c-4de5-b314-4f07e11ee241)


3. **Check IP Reputation on AbuseIPDB:**
   - Copy the IP address from the incident details.
   - Visit AbuseIPDB or a similar threat intelligence platform to check the reputation of the copied IP address.
   - Verify if the IP address is associated with malicious activity based on community reports and ratings.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/81adf010-b1c7-4d7b-9b55-401cc96f4f26)

4. **Explore Other Incidents (as needed):**
   - Repeat the investigation process for other incidents as per the need and priority.


## 8. Remediate Cybersecurity Incident

Remediating cybersecurity incidents is crucial to mitigate risks and restore the security posture of the environment. This section outlines the steps to remediate incidents effectively within a SIEM (Security Information and Event Management) system.

### Steps to Remediate Cybersecurity Incident

1. **Remove Compromised Account:**
   - Navigate to Active Directory in your management console.
   - Go to the Users section and locate the compromised account.
   - Click on the account and select "Edit account status."
   - Uncheck the box for "Account enabled" to disable the compromised account.
   - Confirm the changes to disable the account.
  
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/f8d978e4-28b8-4962-8c41-2527c4f0efbe)


2. **Remediate Other Incidents (as needed):**
   - Review other incidents listed in the Incidents page of your SIEM platform.
   - Depending on the nature of each incident, take appropriate remediation actions:
     - If an incident involves malicious software, quarantine affected systems and perform thorough scans.
     - For unauthorized access incidents, change affected user credentials and review access controls.
     - Implement security patches or updates to address vulnerabilities identified in incidents.
     - Follow incident response procedures and guidelines specific to your organization's policies.

3. **Close Solved Incidents:**
   - Navigate to the Incidents page and review all incidents that have been resolved or mitigated.
   - Close each resolved incident by adding comments detailing the actions taken and the resolution status.
   - Adding comments helps maintain an audit trail and provides context for future incident analysis.
  
![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/bbff190e-d6ac-4a36-a93c-352071a65d3d)


4. **Document Remediation Steps:**
   - Document the steps taken to remediate each incident, including:
     - Details of the incident, such as severity, affected entities, and impact.
     - Actions taken to mitigate the incident, including disabling accounts, applying patches, or implementing security measures.
     - Comments added during incident closure for transparency and reference.


## Conslusion

In conclusion, the implementation of advanced security measures in SIEM has significantly enhanced our threat detection and incident response capabilities. By leveraging Artificial Intelligence, creating custom watchlists, and developing tailored detection rules, we have improved our ability to proactively identify cybersecurity threats and respond effectively to incidents. The integration of Azure for SIEM investigation further strengthens our security posture by providing a comprehensive platform for monitoring and remediation. This project underscores the importance of continuous improvement and innovation in cybersecurity practices to mitigate risks and protect sensitive assets.
