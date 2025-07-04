# SOC Automation Lab

## Objective

Build a functional SOC automation lab integrating Shuffle for security workflow automation, Wazuh for endpoint detection and telemetry collection, Gmail for phishing analysis, TheHive for case management, and Digital Ocean as the cloud provider for hosting the EDR, demonstrating end-to-end alert triage and secure investigation workflows.

## Skills Learned

- **Security Workflow Automation**: Used Shuffle to build playbooks that automate alert processing, case creation, and notifications across tools.
- **Case Management Integration**: Automated ticket creation and evidence enrichment in TheHive from multiple sources using Shuffle.
- **Alert Triage Workflow**: Integrated email-based alerts into TheHive to simulate real-world incident response cases.
- **Endpoint Detection & Telemetry**: Deployed Wazuh agents to collect security telemetry from endpoints for monitoring and correlation.
- **EDR Alert Correlation**: Integrated Wazuh alerts with TheHive through Shuffle to simulate real-time endpoint detection and response.
- **SOC Process Familiarity**: Practiced full alert lifecycle handling with automation, case documentation, and cross-tool integration in a simulated SOC environment.

## Tools Used

- **Shuffle**: Security automation platform used to trigger workflows from Wazuh alerts and automate case creation in TheHive.
- **TheHive**: Open-source SOC case management and alert triage system.
- **Gmail**: Source of suspicious emails and phishing attempts.
- **Wazuh**: Open-source SIEM for endpoint detection, file integrity monitoring, and log analysis.
- **Digital Ocean**: Cloud provider used to deploy Wazuh and TheHive on.
- **SOC Automation Scripts**: Custom and open-source scripts to simulate alert ingestion.
  
## Steps

Built a logical diagram using Draw.io to map out the data flow:

![image](https://github.com/user-attachments/assets/63c1d6c4-1405-4175-ae02-412a3508dd2c)

Created a "droplet" on Digital Ocean to begin the deployment of the Wazuh Server:

![image](https://github.com/user-attachments/assets/0b427d25-08e2-4b3b-b0e0-4b1ed4b19f76)

Set region as Toronto.

![image](https://github.com/user-attachments/assets/323f544a-40a7-4152-beb8-9d6dacd7547e)

Chose the Ubuntu OS option using an Intel CPU with 8GB of RAM:

![image](https://github.com/user-attachments/assets/4b2b021c-d4d8-4e82-baaf-954e0cf7f251)

Named the Host "Wazuh".

![image](https://github.com/user-attachments/assets/6ca3de82-dd38-4ecf-8988-641784b63563)

Successfully created the Wazuh machine.

![image](https://github.com/user-attachments/assets/fe8e849a-08f7-4e89-bdd1-687ed9e2e681)

Started the creation of a firewall.

![image](https://github.com/user-attachments/assets/3d5310dd-4ac0-4a7f-8d17-bf324a4c7714)

Added my host's IP to the Inbound Rules so I can access the machine.

![image](https://github.com/user-attachments/assets/c4f3b26e-b19b-48de-b752-38fb2ee4b318)

Created the firewall.

![image](https://github.com/user-attachments/assets/7f013b3e-3b4d-4c07-8fd5-867d33ae0e2c)

Added the Wazuh machine to the firewall.

![image](https://github.com/user-attachments/assets/d94b43cd-41af-4edb-94e5-2cb24c74da8d)

![image](https://github.com/user-attachments/assets/094e93ae-9874-4f3f-9513-021b7cac1060)

Accessed the Wazuh VM by launching it through the Droplet console:

![image](https://github.com/user-attachments/assets/f9e32b4e-61f1-4705-a9e8-526d82d92027)

Updated the Wazuh VM with the following command:

![image](https://github.com/user-attachments/assets/ace1b470-4245-4a7f-88d6-692e5a199568)

Installed Wazuh with the following command:

![image](https://github.com/user-attachments/assets/15c6ca51-259e-4fd5-8f82-2059a989915c)

Accessed Wazuh by going to the IP of the Wazuh VM:

![image](https://github.com/user-attachments/assets/7945299f-c6fc-4b52-8f08-94aa4c7333bf)

![image](https://github.com/user-attachments/assets/4d6a31cc-bd94-4d28-9343-1697094c6212)

Created a new VM that will be used for installing TheHive and added it to the firewall:

![image](https://github.com/user-attachments/assets/1de464cd-d816-46c9-af8e-89abe1c42da2)

![image](https://github.com/user-attachments/assets/02e65512-1296-48db-9237-4c7ef45c7370)

On TheHive VM, installed dependencies, Java (TheHive dependency), Cassandra (database), Elasticsearch (search/indexing) and TheHive using the following commands:

![image](https://github.com/user-attachments/assets/e71856e0-46aa-4e98-9c1f-22835ef98fbc)

Successfully installed TheHive.

![image](https://github.com/user-attachments/assets/35aab89a-3d96-4d7a-b0a2-7e4439f3d5b2)

Configured Cassandra in TheHive VM. 

First, changed the cluser_name to "autolab" using the nano command to edit the yaml file.

![image](https://github.com/user-attachments/assets/d90718de-8b6a-413e-8c92-4f3b6122a497)

Changed the listen address to the public IP of TheHive VM.

![image](https://github.com/user-attachments/assets/5fc41027-1e86-4dfe-a527-78559e5458c6)

Changed the RPC address.

![image](https://github.com/user-attachments/assets/651eed1c-b6c1-4c72-bc9e-70035f58bfe8)

Changed the seed address.

![image](https://github.com/user-attachments/assets/0a7d4e15-bbce-4c17-8daf-9d1fde902b5d)

Stopped the Cassandra service and removed old installation files that came with the package.

![image](https://github.com/user-attachments/assets/7ef5a285-5aee-4722-9023-d91b542a2cd4)

Started Cassandra and ensured the service is running correctly.

![image](https://github.com/user-attachments/assets/22200bad-191e-46ec-8fab-ef2cfc9bd6d1)

Configured Elasticsearch to manage data indices (querying data).

![image](https://github.com/user-attachments/assets/ba7910e6-d90a-47cf-bdee-b975ccceb2db)

Removed the comments (#) for cluster.name and node.name, changing the default value to cluster.name: thehive and left node.name as default.

![image](https://github.com/user-attachments/assets/ae7598b6-bd40-42a8-8aae-95a0bd2f7d50)

Removed the comments for network.host, http.port and cluster.intial_master_nodes.

Changed the default value to TheHive VM's IP for network.host. Removed "node-2" from the cluster.initial_master_nodes and left http.port to default value.

![image](https://github.com/user-attachments/assets/14e2d79e-a8cf-4b3b-a38d-b3a54059fee7)

Started and enabled Elasticsearch:

![image](https://github.com/user-attachments/assets/4ced8808-f712-4e8b-bf06-c2e2192e4cd7)

Changed ownership to "thehive" user and group from "root" in order to ensure access for the configuration of TheHive.

![image](https://github.com/user-attachments/assets/b0ec6cf5-cef0-4403-9dd3-45c33737600c)

Configured TheHive configuration file.

![image](https://github.com/user-attachments/assets/c27f056b-bd04-472c-bd54-2806b17c138c)

Changed the hostname and application.baseUrl values to TheHive VM's IP, and the cluster-name to "autolab" (same as the cluster defined in Cassandra).

![image](https://github.com/user-attachments/assets/4f6eaa43-db27-4477-b741-3c0fb39ff83f)

Started and enabled TheHive.

![image](https://github.com/user-attachments/assets/4a1bee77-50a3-46e0-8bec-12cb883f041d)

Successfully accessed TheHive using the default credentials.

Note: To access TheHive, the VM's IP must be used with HTTP and not HTTPS.

![image](https://github.com/user-attachments/assets/5c25dc05-a267-4430-ac88-6968e4791a98)

![image](https://github.com/user-attachments/assets/1c0c5103-c71f-4c7f-a80d-156c5e682705)

Added an agent to Wazuh.

![image](https://github.com/user-attachments/assets/08a33a30-df79-4c07-8c6f-19838ac4a503)


Used the IP of the WazuhVM and assigned it a custom name.

![image](https://github.com/user-attachments/assets/6db5e51f-b82f-4f6a-9afb-19d895fa13ca)

Copied the following command over to a Windows 10 VM hosted locally to install the agent:

![image](https://github.com/user-attachments/assets/71b3118a-ea08-4e4c-b631-edf24605f59a)

![image](https://github.com/user-attachments/assets/fd00a3c4-b5d7-48fb-9ff0-4735eefbeb84)

![image](https://github.com/user-attachments/assets/25031244-34bb-4119-b9a9-38496f353c8a)

The agent is now available in Wazuh.

![image](https://github.com/user-attachments/assets/3c845b04-ef49-4dc3-b7c5-42efacf0ebe4)

Configured the "ossec.conf" file on the Windows 10 VM to ingest Sysmon logs in Wazuh.

![image](https://github.com/user-attachments/assets/1ae53556-4ba7-4017-b19d-7fd2e8d86770)

Copied the Sysmon name found in Event Viewer to the ossec.conf file.

![image](https://github.com/user-attachments/assets/730aa0ea-43c7-4521-af6f-cce2aceb7ff7)

![image](https://github.com/user-attachments/assets/f36c542f-4a64-4559-8f36-54670a46b553)

Removed the Application, Security and System locations for ingestion purposes. Application was removed by pasting the Sysmon name over it.

![image](https://github.com/user-attachments/assets/c07e6266-3b38-4309-9ba9-2d9cd6682bf1)

Restarted Wazuh to apply the changes.

![image](https://github.com/user-attachments/assets/3856ce65-fc63-483d-bcde-6416de3b7f90)

Successfully set up Wazuh.

![image](https://github.com/user-attachments/assets/334e53da-e289-4eb2-b67b-fd439b893767)

Set up the Windows Security Exclusions to ignore the C folder in order to conduct a Mimikatz attack and generate telemtry.

![image](https://github.com/user-attachments/assets/d70d83cd-d032-48aa-8f48-3dd56b89ea13)

Downloaded Mimikatz from the following link: https://github.com/gentilkiwi/mimikatz/releases/tag/2.2.0-20220919

![image](https://github.com/user-attachments/assets/53b97a16-0582-4943-aa95-da1c51c48d34)

Extracted the Mimikatz zip and ran it in PowerShell.

![image](https://github.com/user-attachments/assets/d27dbe56-a743-4988-9bbd-1478787be2b5)

Edited the ossec file on the Wazuh server VM to ingest all logs in order to see the Mimikatz execution. Before editing, a backup file was created.

![image](https://github.com/user-attachments/assets/2480aa61-2bfc-4714-a451-c8e5794fc84f)

Changed the following settings to "yes".

![image](https://github.com/user-attachments/assets/f7666c12-a657-437c-9402-1949e5333a06)

Changed the filebeat.modules value to "true" in the filebeat file in order for Wazuh to start ingesting the logs.

![image](https://github.com/user-attachments/assets/e9d37baf-69ae-4831-a1e8-d1cba2e03eed)

![image](https://github.com/user-attachments/assets/249537a5-05c4-4789-8533-26e2d27b0219)

In Wazuh -> Stack Management -> Index Patterns, created an index for all archives to be able to search all the logs.

![image](https://github.com/user-attachments/assets/d96ea443-cf2a-4470-aa86-7f76a4bbd6e5)

![image](https://github.com/user-attachments/assets/1327fdbe-833e-4f57-b517-eed30b9225b8)

![image](https://github.com/user-attachments/assets/4242477f-ddf2-483f-987f-733bd9ac3eb9)

Successfully set up the "wazuh-archives**" index.

![image](https://github.com/user-attachments/assets/fd73b134-49f5-4b5d-82b6-8457d83aa509)

Re-ran Mimikatz and 2 logs appeared in Wazuh.

![image](https://github.com/user-attachments/assets/9e5dc409-7847-4422-bb4b-7fc7e30a13f1)

Created a rule in Wazuh -> Management -> Rules -> Rules Files by copying and modifying the following rule:

![image](https://github.com/user-attachments/assets/0f309d8e-b708-4296-bf27-638ea9fe2834)

![image](https://github.com/user-attachments/assets/c4a69b3c-9999-4c5f-9fc0-4d37fd7d9488)

![image](https://github.com/user-attachments/assets/b44a87a2-eb2f-4ddd-95aa-91122a5c3915)

Created the rule by editing the local_rules.xml file in Custom Rules with the following, assigning it the MITRE id of T1003 (logon detected):

![image](https://github.com/user-attachments/assets/df57152e-0776-42f6-b441-a9d92b08d0e0)

To test the new rule, the "mimikatz" executable was renamed to "youareawesome".

![image](https://github.com/user-attachments/assets/956474a3-9e14-4869-ad3c-da37b8c67089)

![image](https://github.com/user-attachments/assets/2a3878bb-7028-4a80-b70e-ee9a53cf1928)

Mimikatz alert is successfully displayed in Wazuh.

![image](https://github.com/user-attachments/assets/92fd5ec7-9418-4ad0-9975-958902b15532)

![image](https://github.com/user-attachments/assets/8ce7662c-d795-4f9d-bc41-0e279aea0a96)

To start automating processes, a new workflow was created in Shuffle.

![image](https://github.com/user-attachments/assets/d0861040-7a29-47ef-ac81-ed82f885c567)

Added a Webhook and renamed it to Wazuh-Alerts. The Webhook URI will be copied into the ossec config of the Wazuh Server VM.

![image](https://github.com/user-attachments/assets/b7ee7ad4-9b0f-4740-b5c4-9611a80770a4)

In the "Change Me" icon, added the $exec argument.

![image](https://github.com/user-attachments/assets/da8dc03b-460d-49d0-bb84-5fc4f8cc3ba8)

Configured Wazuh to connect to Shuffle by adding an integration tag in the ossec configuration file. Added the Webhook URI from Shuffle and the rule ID created earlier in Wazuh (100002 for detecting Mimikatz).

![image](https://github.com/user-attachments/assets/83811803-adf3-4115-8fe6-4678f80ea183)

![image](https://github.com/user-attachments/assets/c2c46475-996c-4368-9edc-15b8ed6993c0)

The information generated in Wazuh is successfully displayed in Shuffle.

![image](https://github.com/user-attachments/assets/2bbe9cb5-5f18-4d74-93eb-65fcccc55919)

Configured Shuffle to send the hash values received from Wazuh to Virus Total.

First, changed the Find Actions to "Regex capture group" and added the following Input Data:

![image](https://github.com/user-attachments/assets/292e0c90-c043-4942-b10e-2888b937cd6a)

In order to write the Regex, used ChatGPT to get the command based on the following hash from the Webhook result:

![image](https://github.com/user-attachments/assets/cbce1ae6-07c8-4241-bb1c-49f5b98515ff)

![image](https://github.com/user-attachments/assets/c69feec7-026b-41d6-bcb9-a3eccc6ff281)

![image](https://github.com/user-attachments/assets/e20be0ac-da99-45b9-b7c1-811416fab8d9)

The SHA256 value is successfully parsed out to Shuffle:

![image](https://github.com/user-attachments/assets/b3162b4b-2ebe-40a3-909b-a4bb3491c442)

Renamed the "Change_me" element to "SHA256 Regex"

![image](https://github.com/user-attachments/assets/231d92c7-84b5-4f56-bb0e-1deb0cf12ec3)

To be able to send the SHA256 value to Virus Total, first the API key was copied over to Shuffle:

![image](https://github.com/user-attachments/assets/884fdd16-8c2f-4353-b0a2-b15187407249)

![image](https://github.com/user-attachments/assets/378c362c-21ea-4712-b3a8-d3d2efe38fcb)

Changed the Virustotal settings to "Get a hash report" and added the earlier Regex command under Id:

![image](https://github.com/user-attachments/assets/46640f05-5a71-4991-8ccc-0479ef2abf91)

Virus Total successfully returned results.

![image](https://github.com/user-attachments/assets/052339c0-6137-4351-80ed-23a80652d1a3)

65 scans detected the file as malicious.

![image](https://github.com/user-attachments/assets/85abb9d5-e15f-4bca-905a-d04418c4722f)

Created a new organization named "Autolab" in TheHive and two users, Bobby (normal) and SOAR (service):

![image](https://github.com/user-attachments/assets/8ebf58dc-74e5-4e5f-8b64-96745eb59675)

![image](https://github.com/user-attachments/assets/875209e0-8193-4aa2-a45a-ef28df5e260e)

Created an API key for the SOAR user:

![image](https://github.com/user-attachments/assets/468028dc-5524-46a6-a4fb-9c2a468aba26)

Copied the API and TheHive address to Shuffle to authenticate with the service:

![image](https://github.com/user-attachments/assets/6cd11320-a99a-4f10-bec5-b83e8374cda9)

Edited TheHive app on Shuffle with the following JSON:

![image](https://github.com/user-attachments/assets/9652a497-4328-409f-8a86-6d8cd855461c)

![image](https://github.com/user-attachments/assets/a56fa625-6c4e-4832-99ee-181c4d09309b)

In Digital Ocean, added a custom inbound rule to allow connection to port 9000 in order for TheHive to integrate with Shuffle:

![image](https://github.com/user-attachments/assets/505d5693-e717-4654-9589-6866a97f72de)

After running the workflow in Shuffle, TheHive successfully generated the alerts:

![image](https://github.com/user-attachments/assets/2551b8e9-81d8-4b98-85c3-e01d7f24dc33)

![image](https://github.com/user-attachments/assets/997c5e29-cd84-422b-9397-e1c370c087f0)

Added the email app and edited it accordingly:

![image](https://github.com/user-attachments/assets/03d0aa87-50fd-4c11-ae2e-973d048bff2c)

![image](https://github.com/user-attachments/assets/88e2069c-f822-4706-969d-d9a4bc58a942)

Received the automated email from Shuffle:

![image](https://github.com/user-attachments/assets/3077300c-499a-4ada-bb24-03afb5025558)


