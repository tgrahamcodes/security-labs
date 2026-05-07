# Active Directory Attack Lab

## Overview

This repository documents a simulated Active Directory penetration testing lab built to demonstrate common techniques used to compromise enterprise Windows environments.

The project focuses on credential attacks, Active Directory enumeration, privilege escalation, and lateral movement techniques.

&nbsp;

## Lab Environment

| System            | Operating System    | Role                        | IP Address     |
|-------------------|---------------------|-----------------------------|----------------|
| Domain Controller | Windows Server 2022 | Active Directory / DNS      | 192.168.91.129 |
| Workstation       | Windows 11 Pro      | Domain User Host            | 192.168.91.130 |
| Attacker          | Parrot Security OS  | Penetration Testing Machine | 192.168.91.128 |

##### Domain -  corp.local
##### Network - 192.168.91.0/24
&nbsp;

## Attack Techniques Demonstrated

| Attack                          | Description of the Attack                                |
|---------------------------------|----------------------------------------------------------|
| LLMNR Poisoning                 | Capturing NTLM authentication hashes                     |
| Kerberoasting                   | Extracting Kerberos service tickets for offline cracking |
| BloodHound Privilege Escalation | Identifying attack paths in Active Directory             |
| Pass-the-Hash                   | Authenticating with captured NTLM hashes                 |

### Additional Attacks:

| Attack                | Description                                              |
|-----------------------|----------------------------------------------------------|
| AS-REP Roasting       | Extracting authentication responses without pre-auth     |
| SMB Share Enumeration | Discovering accessible network shares                    |
| DCSync                | Extracting domain credential hashes                      |
| Golden Ticket         | Forging Kerberos tickets using the krbtgt hash           |

&nbsp;

## Attack Walkthrough

| Attack | Writeup |
|--------|---------|
| LLMNR Poisoning | [View](individual-attacks/LLMNR-Poisoning.md) |
| Kerberoasting | [View](individual-attacks/Kerberoasting.md) |
| AS-REP Roasting | [View](individual-attacks/AS-REP-roasting.md) |
| BloodHound | [View](individual-attacks/Bloodhound.md) |
| Pass-the-Hash | [View](individual-attacks/Pass-the-Hash.md) |
| DCSync | [View](individual-attacks/DCSync.md) |
| Golden Ticket | [View](individual-attacks/golden-ticket.md) |
| SMB Share Enumeration | [View](individual-attacks/smb-enumeration.md) |


&nbsp;

# Example Attack Evidence

### Captured NTLM Hash (LLMNR Poisoning)
<img src="screenshots/responder2.png" width="600">

### Kerberoasting Hash
<img src="screenshots/kerberoasted.png" width="600">

### BloodHound Attack Path
<img src="screenshots/bloodhound-map.png" width="600">

## Tools Used

| Tool | Purpose |
|------|------|
| Responder | LLMNR/NBT-NS poisoning and credential capture |
| Hashcat | Offline password cracking |
| CrackMapExec | Active Directory enumeration |
| BloodHound | Privilege escalation analysis |
| Impacket | Kerberos attacks and pass-the-hash |


## Detection Opportunities

Possible detection indicators include:

- abnormal Kerberos ticket requests
- repeated authentication failures
- unusual LLMNR broadcast activity
- suspicious SMB authentication attempts
- privilege escalation events


## Mitigation Strategies

Common defensive measures include:

- disabling LLMNR and NBT-NS
- enforcing SMB signing
- strong password policies
- multi-factor authentication
- least privilege access control
- Active Directory security auditing


## Disclaimer

This lab was conducted in an isolated virtual environment for educational and defensive security research purposes only.
