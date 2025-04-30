# Atomic Red Team Lab

## Objective

Simulate real-world adversary techniques from the MITRE ATT&CK framework using Atomic Red Team, generate and analyze telemetry data in Splunk, and identify visibility gaps in endpoint detection coverage within a Windows-Kali Linux lab environment.

## Skills Learned

- Detection Engineering – Recognizing and analyzing visibility gaps in endpoint detection coverage using Splunk and Atomic Red Team.
- Threat Simulation – Executing MITRE ATT&CK techniques using Atomic Red Team to simulate real-world adversary behavior.
- Log Analysis – Investigating telemetry from simulated attacks using Splunk to verify detection and event generation.
- Security Monitoring – Correlating attack behavior with MITRE ATT&CK tactics and techniques for proactive alert development.
- Blue Teaming – Validating and improving defensive posture by identifying blind spots in endpoint monitoring.

## Tools Used

- Kali Linux: Perform a brute force attack onto the AD users.
- Atomic Red Team: Adversary emulation framework.
- Splunk: Security Information and Event Management (SIEM).
- Windows Defender: Host-based detection of threats.
- MITRE ATT&CK: Adversarial tactics and technique framework.

## Steps

This lab is a continuation of the [Active Directory project](https://github.com/andcoa/ActiveDirectory/blob/main/README.md)

Network diagram:

![image](https://github.com/user-attachments/assets/fc271426-2238-4d33-b08b-7d9344dbe9bf)

Updated Kali VM's IPv4 settings to match the network diagram in the AD lab.

![image](https://github.com/user-attachments/assets/da707a22-d1c8-4184-a177-c137c6c7d050)

Ran the following command to update & upgrade the Kali repositories:

![image](https://github.com/user-attachments/assets/3f940886-c274-456e-93be-105edab38585)

Started setting up the attack by creating a new directory named "AD-Project".

![image](https://github.com/user-attachments/assets/3e6af0a1-6394-4447-a5dc-f57a3d68577b)
