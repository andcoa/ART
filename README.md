# Atomic Red Team Lab

## Objective

Simulate real-world adversary techniques from the MITRE ATT&CK framework using Kali Linux and Atomic Red Team, generate and analyze telemetry data in Splunk, and identify visibility gaps in endpoint detection coverage within a Windows-Kali Linux lab environment.

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

Prepared the wordlist "rockyou.txt" file for use.

![image](https://github.com/user-attachments/assets/df778438-cd9f-47a3-a74d-2d8703aac07f)

Added the AD users passwords to the "passwords.txt" file.

![image](https://github.com/user-attachments/assets/70860ce5-a518-4a5f-9184-220bbe0e3e2a)

On the target Windows 10 VM, the two users were added as Remote Desktop Users.

![image](https://github.com/user-attachments/assets/f13282f3-15a9-4216-b26c-0e912f3e0a71)

Ran the following Hydra brute force command in Kali to execute the attack on the Windows 10 VM. The user's password was obtained successfully.

![image](https://github.com/user-attachments/assets/0fe08df7-e000-4f96-82f5-8abc6bdd8a6a)

The event code 4625 appears 21 times in Splunk, which means there were 21 failed attempts to login to the "tsmith" account. This coincides with the number of attempts the Hydra attack made to crack the password of the user "jsmith".

![image](https://github.com/user-attachments/assets/8d5f887b-e19e-484d-afe3-1064260db911)

All the events under code 4625 happened at the same time which strongly indicates it can be a brute force attack.

![image](https://github.com/user-attachments/assets/4d7e8fff-e685-494a-b0d6-fc225ddb6ef5)

There are seven events for code 4624 which stands for the account getting successfully logged in.

![image](https://github.com/user-attachments/assets/37aa9197-7544-4309-97a3-f37e6f5729ab)

While looking through the seven logs listed by the command above, one of them shows the details of the attacker Kali VM:

![image](https://github.com/user-attachments/assets/e729d3f8-cb8c-428f-a89d-08e9a13179fc)

To prepare for the installation of Atomic Red Team on the Windows 10 VM, the C:\ drive was added as an exclusion in Windows Security as Microsoft Defender would otherwise delete some of the files after the installation.

![image](https://github.com/user-attachments/assets/1b4a95a4-9d28-40e0-988f-22a7556e4252)

The following commands were executed to install Atomic Red Team:

![image](https://github.com/user-attachments/assets/3658001e-fd00-4dd3-9a85-8aaed5d20d9d)

![image](https://github.com/user-attachments/assets/35169cfc-7087-46e9-99d5-281dab87e0ef)

Ran the following Atomic Test command with the technique ID T1136.001 to generate telemtry based on creating a local account named "NewLocalUser":

![image](https://github.com/user-attachments/assets/bd32833b-aaa6-492b-afbf-91006f7539b9)

Splunk detected the generated telemetry:

![image](https://github.com/user-attachments/assets/7e89a5a0-fdd4-4356-ab5d-d08fdf78840e)

Ran another Atomic Test command with the technique ID T1059.001 to generate telemtry based on the Command and Scripting Interpreter vulnerability from MITRE.

![image](https://github.com/user-attachments/assets/c6366a3b-a633-44db-8790-638e51b0b771)

![image](https://github.com/user-attachments/assets/fabac38d-2b2a-4541-9ac7-8ef9ccb4a9a6)

Splunk detected the generated telemetry matching the Atomic Test results:

![image](https://github.com/user-attachments/assets/746b9bc5-3fd5-4a29-aec3-73c43131cdff)
