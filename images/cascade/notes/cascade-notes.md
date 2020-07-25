# Cascade

### Nmap

- 53/tcp    open  domain        Microsoft DNS 6.1.7601 (1DB15D39) (Windows Server 2008 R2 SP1)
  | dns-nsid: 
  |_  bind.version: Microsoft DNS 6.1.7601 (1DB15D39)
- 88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2020-07-05 22:09:45Z)
- 135/tcp   open  msrpc         Microsoft Windows RPC
- 139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
- 389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: cascade.local, Site: Default-First-Site-Name)
- 445/tcp   open  microsoft-ds?
- 636/tcp   open  tcpwrapped
- 3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: cascade.local, Site: Default-First-Site-Name)
- 3269/tcp  open  tcpwrapped
- 5985/tcp wsman
- 49154/tcp open  msrpc         Microsoft Windows RPC
- 49155/tcp open  msrpc         Microsoft Windows RPC
- 49157/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
- 49158/tcp open  msrpc         Microsoft Windows RPC
- 49165/tcp open  msrpc         Microsoft Windows RPC

### Users

- administrator
- user:[CascGuest] rid:[0x1f5]                                                                                                                                                                              
- user:[arksvc] rid:[0x452]                                                                                                                                                                                 
- user:[s.smith] rid:[0x453]                                                                                                                                                                                 
- user:[r.thompson] rid:[0x455]                                                                                                                                                                              
- user:[util] rid:[0x457]                                                                                                                                                                                    
- user:[j.wakefield] rid:[0x45c]                                                                                                                                                                             
- user:[s.hickson] rid:[0x461]                                                                                                                                                                               
- user:[j.goodhand] rid:[0x462]                                                                                                                                                                              
- user:[a.turnbull] rid:[0x464]                                                                                                                                                                              
- user:[e.crowe] rid:[0x467]                                                                                                                                                                                 
- user:[b.hanson] rid:[0x468]                                                                                                                                                                                
- user:[d.burman] rid:[0x469]                                                                                                                                                                                
- user:[BackupSvc] rid:[0x46a]                                                                                                                                                                               
- user:[j.allen] rid:[0x46e]                                                                                                                                                                                 
- user:[i.croft] rid:[0x46f]
- krbtgt
- util

### Creds

- r.thompson:rY4n5eva
- s.smith:st333ve2
- ArkSvc: encrypted pwd: BQO5l5Kj9MdErXx6Q6AGOw== decrypted: w3lc0meFr31nd
- Administrator:baCT3r1aN00dles base64:YmFDVDNyMWFOMDBkbGVz

### PrivEsc

- C:\Windows\system32\IEEtwCollector.exe /V possible unquoted service path
- Use powershell to find deleted AD objects
- find deleted users
  - Get-ADObject -ldapFilter:"(msDS-LastKnownRDN=*)" -IncludeDeletedObjects
  - Find user by name
    - Get-ADObject -Filter {displayName -eq "TempAdmin"}  -IncludeDeletedObjects
    - View All properties of the user 
      - Get-ADObject -Filter {displayName -eq "TempAdmin"}  -IncludeDeletedObjects -Properties *

