# This is to show the different shares on the network

SMB Share Enumeration is used to identify accessible network shares within the domain environment. Discovering these shares can reveal sensitive files, misconfigured permissions, and opportunites for potential lateral movement. 

```bash
impacket-smbclient corp.local/j.smith:Welcome1@192.168.91.129
```

---
&nbsp;

<img src="../screenshots/enum-shares.png" width=600 style="display:block; margin-bottom:10px;">

This list of different shares.

&nbsp;

---

<img src="../screenshots/enum-shares-2.png" width=600 style="display:block; margin-bottom:10px;">

The SYSVOL share being opened.

&nbsp;

---

& The shares just being explored more.

<img src="../screenshots/smb-list-shares.png" width=600 style="display:block; margin-bottom:10px;">

&nbsp;

---
