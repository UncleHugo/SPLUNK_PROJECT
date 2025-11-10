# Failed Logon Analysis Summary

The table and dasboard below captures the recorded failed logon attempts detected on the monitored Windows endpoint.
Each row represents a single authentication failure, showing who attempted to log in, where the attempt came from, which host registered the event, and when it occurred.
By correlating the User and Source Network Address, we can identify suspicious activity such as repeated login attempts from unfamiliar IPs, brute-force patterns, or lateral movement attempts across the network.
The Host field helps trace which specific system or domain controller logged the event, while the Timestamp provides chronological context for incident reconstruction.

This dataset was extracted and visualized using Splunk’s search and filtering capabilities, leveraging the EventCode=4625 (Windows failed logon) events.

index="splunk-ds-index" source="WinEventLog:Security" "EventCode=4625"

<img width="1707" height="871" alt="image" src="https://github.com/user-attachments/assets/6032c045-b13d-4a8c-9bf5-4408748a2b96" />

## Creating a Dasboard

<img width="1684" height="851" alt="image" src="https://github.com/user-attachments/assets/9a9145d8-68e6-4998-827f-f4ced167b1b0" />












