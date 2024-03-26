
## 1. Demo: Enable Artificial Intelligence in SIEM

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




Here's the documentation section for creating a watchlist to detect cybersecurity threats in Microsoft Sentinel based on your provided steps:


## 2. Demo: Create Watchlist to Detect Cybersecurity Threats

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






Here's the documentation section for creating a detection rule for cybersecurity threats in Microsoft Sentinel based on your provided steps:


## 3. Demo: Create Detection Rule for Cybersecurity Threat

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
     

7. **Configure Entities:**
   - Entity are onjects in Microsoft Sentinel which represent important information such as Ip addresses , host, users etc. 
   - Add two different identities: Account (select sid and userID) and User IP Address and other as shown in Screenshot below.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/7b76ec83-0af5-43ca-8a7e-247048b3ad3d)


8. **Set Query Scheduling:**
   - Choose the frequency to run the query, such as every 5 minutes.

9. **Configure Incident Settings:**
   - Turn on the "Alert grouping" option to manage incident grouping.
   - We can see that up to only 150 alerts can be grouped into a single incident. if there are more than 150 then a new new incident will be created for it. 

10. **Review and Create:**
    - Proceed to the review + create option and click on "Create" to finalize the creation of the analytics rule.

![image](https://github.com/ijlal321/Cyber-Security-Projects/assets/103317626/cbab47b6-3891-459a-9a4a-ebc64a298490)

