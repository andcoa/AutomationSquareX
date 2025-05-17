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

Configured Cassandra in TheHive VM. First, changed the cluser_name to "autolab" using the nano command to edit the yaml file.

![image](https://github.com/user-attachments/assets/d90718de-8b6a-413e-8c92-4f3b6122a497)

Changed the listen address to the public IP of TheHive VM.

![image](https://github.com/user-attachments/assets/ce03b5d0-eb5d-4c78-8625-d0b748d07887)

Changed the RPC address.

![image](https://github.com/user-attachments/assets/651eed1c-b6c1-4c72-bc9e-70035f58bfe8)

