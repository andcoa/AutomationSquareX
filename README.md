# SOC Automation Lab

## Objective

Build a functional SOC automation lab integrating SquareX for browser-based threat containment, Wazuh for endpoint detection and telemetry collection, Gmail for phishing analysis, TheHive for case management and Digital Ocean as the cloud provider for hosting the EDR, demonstrating end-to-end alert triage and secure investigation workflows.

## Skills Learned

- **Secure Phishing Analysis**: Used SquareX to isolate and analyze suspicious emails without exposing the host system or alerting the sender.
- **Disposable File Viewing**: Opened attachments and documents in a privacy-enhanced container to prevent malware execution and data leakage.
- **Alert Triage Workflow**: Integrated email-based alerts into TheHive to simulate real-world incident response cases.
- **Browser-Based Threat Containment**: Explored web-based threats using SquareX containers that leave no forensic artifacts or logs.
- **Endpoint Detection & Telemetry**: Deployed Wazuh agents to collect security telemetry from endpoints for monitoring and correlation.

## Tools Used

- **SquareX**: Browser extension for privacy-enhanced browsing and disposable file analysis.
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

On TheHive VM, installed dependencies, Java, Cassandra, Elasticsearch and TheHive using the following commands:

![image](https://github.com/user-attachments/assets/e71856e0-46aa-4e98-9c1f-22835ef98fbc)

Example of the Java commands, repeated the same for the rest.

![image](https://github.com/user-attachments/assets/102da442-d1b7-413e-8a61-05d731a43679)

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

Successfully set up the "wazuh-archives**" index

![image](https://github.com/user-attachments/assets/fd73b134-49f5-4b5d-82b6-8457d83aa509)


