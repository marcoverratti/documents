# Bashed Write-Up

Easy

Tags:
`Web Site Structure Discovery`
`Sudo Exploitation`
`Cronjob Abuse`

## Intro

1. Use dirb scan directory
2. `/scripts` be executed every minute

## Exploit

### Port scanning

```
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
```

### Scan directory

```
http://10.10.10.68/dev/phpbash.php
```

## Privilege Escalation

Run stable shell from `phpbash.php`

### List user's privileges or check a specific command

```
sudo -l
```

Change user

```
sudo -u scriptmanager bash
```

### Exploring directories

`/scripts` dir is owned by the `scriptmanager`

```
scriptmanager@bashed:/$ ls -la
```

```
drwxrwxr--   2 scriptmanager scriptmanager  4096 May 10 00:17 scripts
```

### Find cron job

all scripts in `/scripts` are executed every minute ???

`wget` shell to `/scripts`