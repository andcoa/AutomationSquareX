# SOC Automation Lab

## Objective

Build a functional SOC automation lab integrating SquareX for browser-based threat containment, Wazuh for endpoint detection and telemetry collection, Gmail for phishing analysis, TheHive for case management and Digital Ocean as the cloud provider, demonstrating end-to-end alert triage and secure investigation workflows.

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
- 
## Steps

Build a logical diagram using Draw.io to map out the data flow:

![image](https://github.com/user-attachments/assets/63c1d6c4-1405-4175-ae02-412a3508dd2c)
