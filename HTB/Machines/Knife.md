# Knife Write-Up

Easy

Tags: 


## Intro

1. 

## Exploit

### Port scanning

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
```

Exploit Title: PHP 8.1.0-dev - 'User-Agentt' Remote Code Execution

[PoC php-8.1.0 backdoor rce github](https://github.com/flast101/php-8.1.0-dev-backdoor-rce)