# Guilty Until Proven Innocent — Binary Triage Lab

**Author:** Tom Graham  
**Platform:** Parrot Security OS (bare metal)  
**Date:** May 2026
**Series:** Security Research Portfolio — tgraham.dev

**Disclaimer:** I know what all of these files contain. This is purely educational. None of the analyzed files have been included in this repository. Oh, and "my friend", does not exist. Hope you enjoy my work!

---

In cybersecurity, getting tools to test and use them effectively is crucial. This means a file from a friend that you would like to test in a safe environment should be treated like malware designed to attack you. At least that is my theory, and if you are downloading anything related to "great free tool to hack facebook", please restart your learning experience. What I mean is cyber is all about trust, and you DO have to trust SOMETHING. This lab will dive into getting a file from a friend and analyzing it by going through a checklist in order to determine the risk factor, and then testing this file in an extremely safe environment — VMs or Sandboxes.

The summaries of each case are below but please check out the full write-ups in the `case` directories. These summaries are available just to show the differences between the cases.

&nbsp;

---

## Case 01 — The Cure was The Impending Disease

**File Structure: How it was when tested. (Of course, files not included as it is illegal and unethical.)**
```
ZIP (1 detection)
└── RAR (2 detections, via-tor, INNO appended)
   ├── mbam-setup-2.2.0.1024.exe  <- The legitimate Malwarebytes installer
   └── Crack
      └── MBAMToolBox2.exe     <- The crack file which changes the hosts file and includes evasion techniques
```

**Scenario**: My friend downloaded and installed a popular security software that he claims is "forever". The goal is to figure out why, and what he means by "forever".

A working crack — and now we know why our friend thinks it is a "forever" version. The mechanism is clever: rather than patching the binary, it redirects Malwarebytes license validation servers to 127.0.0.1 via the Windows hosts file. 

- Not malicious to you as the user
- Malicious to Malwarebytes as the software vendor
- Impending Disease because its risky; it modifies a protected system file, actively evades analysis, and demands admin rights. A malicious actor could have bundled anything alongside it and you would have run it without hesitation because your friend said it was fine?!
- Still illegal and unethical to use pirated software.
- Pay the devs, coding is hard.
- Purely educational

[Full writeup](./case01/case01-Malwarebytes.md)

&nbsp;

---

## Case 02 — SUP3R SECURITY TOOLZ

**File Structure:**
```
hidd3nw4rez.tar.gz
├── Linux/
│   ├── metasploit-linux-x64-installer.run  <- legitimate installer
│   ├── patch.sh                            <- runs as root
│   └── license.rb                          <- hardcoded license bypass
└── Windows/
   ├── metasploit-windows-x64-installer.exe <- legitimate, signed by Rapid7
   └── Patch.bat                            <- Windows equivalent
```

**Scenario**: My friend listened to my explanation for the previous case and now thinks he is a h4x0r. He googled something along the lines of become the best hacker, along with how to hack facebook... shrug (another time). He now has downloaded and installed a popular security software that he says is acting bizarre. The goal is to figure out why, and again what he means...

A surgical Ruby patch against a $15,000/year exploitation framework. ZenEQ — the cracker — even left comments complaining about previous crackers methodology while cracking it himself. He also thanked Rapid7. The installer is legitimate and signed by Rapid7. The risk lives entirely in the patch files running as root inside a professional exploitation framework.

- Not malicious to you as the user
- Malicious to Rapid7 as the software vendor, which is not cool; We love Rapid7
- Risky — unknown Ruby code running as root inside Metasploit Pro is the security equivalent of handing someone your keys and asking them to only open the front door
- Still illegal and unethical to use pirated software.
- Pay the devs, coding is hard.
- Purely educational

[Full writeup](./case02/case02-MetasploitPro.md)

&nbsp;

---

## Case 03 — What is Federal Prison, Alec?

**File Structure:**
```
Cobalt Strike.zip
├── Server/
│   ├── TeamServerImage          <- 0 detections, legitimate binary
│   └── cobaltstrike.auth        <- license token
└── Client/
   └── cobaltstrike-client.jar  <- 45 detections
```

 **Scenario**: My friend, you know, the hacker... whose handle is Alec? — SUPER secret stuff! — is now extremely upset because he has no idea how to use Metasploit and he wants to point and click "just like windows", he says. The goal is to finish this lab, get a new friend, and inspect this program to see what is going on with it.

The most dangerous tool in the collection. The server binary is clean. The client JAR triggered 45 AV engines with specific Cobalt Strike family names, embedded Java exploits, and UAC bypass modules. Static analysis of the JAR confirmed all flagged components are documented Cobalt Strike features — the detections reflect the tool's offensive capabilities, not trojanization.

- Not malicious to you as the user
- Use in isolated lab environment only, if you know what you are actually doing.
- You know... my friend did end up using it, and is doing 30 years sharing a bunk with the author of Wannacry.
- Still illegal and unethical to use pirated software.
- Pay the devs, coding is hard.
- Purely educational

[Full writeup](./case03/case03-CobaltStrike.md)

&nbsp;

---
