# Backdoor Write-Up

Easy

Tags: 
`PHP`
`Wordpress`
`Backdoor`

## Intro

WordPress 5.8.1
CVE-2022-21663

## Exploit

### 1. Port scanning

```
nmap -sV <target IP>
```
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
```

### 2. WPScan

```
wpscan --url http://10.10.11.125 --api-token <api-token>
```
```
[+] WordPress version 5.8.1 identified (Insecure, released on 2021-09-09).
 | Found By: Rss Generator (Passive Detection)
 |  - http://10.10.11.125/index.php/feed/, <generator>https://wordpress.org/?v=5.8.1</generator>
 |  - http://10.10.11.125/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.8.1</generator>
 |
 | [!] 7 vulnerabilities identified:
 |
 | [!] Title: WordPress < 5.8.2 - Expired DST Root CA X3 Certificate
 |     Fixed in: 5.8.2
 |
 | [!] Title: WordPress < 5.8.3 - SQL Injection via WP_Query
 |     Fixed in: 5.8.3
 |
 | [!] Title: WordPress < 5.8.3 - Author+ Stored XSS via Post Slugs
 |     Fixed in: 5.8.3
 |
 | [!] Title: WordPress 4.1-5.8.2 - SQL Injection via WP_Meta_Query
 |     Fixed in: 5.8.3
 |
 | [!] Title: WordPress < 5.8.3 - Super Admin Object Injection in Multisites
 |     Fixed in: 5.8.3
 |
 | [!] Title: WordPress < 5.9.2 - Prototype Pollution in jQuery
 |     Fixed in: 5.8.4
 |
 | [!] Title: WordPress < 5.9.2 / Gutenberg < 12.7.2 - Prototype Pollution via Gutenberg’s wordpress/url package
 |     Fixed in: 5.8.4
```

Scan plugin

```
wpscan --url http://10.10.11.125 --api-token aJR9HQ9PUjLaef94kAqFYIuXTbrEfalI9TGLDQ0aJ8k --enumerate p,u --plugins-detection aggressive
```
```
[i] Plugin(s) Identified:

[+] akismet
 | Location: http://10.10.11.125/wp-content/plugins/akismet/
 | Latest Version: 4.2.3
 | Last Updated: 2022-04-25T17:31:00.000Z
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - http://10.10.11.125/wp-content/plugins/akismet/, status: 403
 |
 | [!] 1 vulnerability identified:
 |
 | [!] Title: Akismet 2.5.0-3.1.4 - Unauthenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 3.1.5
 |
 | The version could not be determined.
```

[ebook plugins](https://www.exploit-db.com/exploits/39575)

http://10.10.11.125/wp-content/plugins

![](/img/Machine-retired-backdoor.png)