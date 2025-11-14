### Introduction

SSH (Secure Shell) log files contain valuable information about remote access to servers, including login attempts, commands executed, and session details. Analyzing SSH logs using Splunk SIEM enables security professionals to monitor access to critical systems, detect anomalies, and identify potential security threats.


### Uploading Sample SSH Log Files to Splunk SIEM

- Navigate to Settings > Add Data.
- Select Upload as the data input method.
  
<img width="1529" height="651" alt="Screenshot 2025-11-14 123315" src="https://github.com/user-attachments/assets/11cdbfc1-aab5-4378-a051-9b1b564697ea" />


<img width="1489" height="461" alt="Screenshot 2025-11-14 123941" src="https://github.com/user-attachments/assets/c95cc93b-c291-4d16-8a28-6a79ae9a7901" />


<img width="744" height="215" alt="image" src="https://github.com/user-attachments/assets/82c28deb-97bd-4099-82cd-1f95efccee46" />

<img width="1833" height="894" alt="image" src="https://github.com/user-attachments/assets/1408f65c-e60a-4dd0-adb7-48b599dd9481" />

### Analyze SSH Activity Patterns

- Identify top users or source IP addresses accessing the SSH server:

index="splunk-ds-index" sourcetype="csv" source="SSH.csv"
| top limit=10 user src_ip

<img width="1876" height="701" alt="image" src="https://github.com/user-attachments/assets/56fcb8b9-82eb-4939-ba76-e769dd33476d" />

<img width="1544" height="646" alt="image" src="https://github.com/user-attachments/assets/4f071e29-0278-4bd0-83f8-0c914d1d9351" />


- Analyze successful vs. failed SSH login attempts:

index="splunk-ds-index" sourcetype="csv" source="SSH.csv"
| where action != "undetermined"
| stats count by action

<img width="1752" height="734" alt="image" src="https://github.com/user-attachments/assets/5abddd24-faa6-402e-a2cc-c7847026070c" />

#### Monitor User Behavior

- Identify src_ip with multiple failed login attempts:

index="splunk-ds-index" sourcetype="csv" source="SSH.csv"
| search action="failure"
| top limit=10 src_ip

<img width="1441" height="725" alt="image" src="https://github.com/user-attachments/assets/836390e8-7f58-43c7-8ed5-0cb94b73ea25" />


<img width="1432" height="774" alt="image" src="https://github.com/user-attachments/assets/d4e1684f-e888-4953-a637-75209ad5f4db" />

### Conclusion after Analyzing
Analyzing SSH log files using Splunk SIEM, provides valuable insights into remote access to servers within a network. By monitoring SSH events, detecting anomalies, and correlating with other logs, organizations can enhance their security posture and protect against unauthorized access and potential security threats.







