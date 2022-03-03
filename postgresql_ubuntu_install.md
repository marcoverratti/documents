# PostgreSQL Ubuntu 20.04 Install

## 1. Install PostgreSQL Ubuntu 20.04
Update apt list first:

```
$ sudo apt update
```

Install postgresql:
```
$ sudo apt-get -y install postgresql
```

Run postgresql:
```
$ sudo service postgresql start
```

## 2. Create user:
Login to postgres:
```
$ sudo -u postgres psql
```

Create user:
```
postgres=# alter user <userName> password ‘<password>’
```

Exit with `\q`:
```
postgres=# \q
```

## 3. PgAdmin4 Ubuntu Install
Install the public key for the pgAdmin4 repository:
```
$ sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add
```
<img src="https://i.ibb.co/jT3t56Z/Untitled.png"></aimg>

Add the pgAdmin4 repository:
```
$ sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
```

Install pgAdmin (96.4 MB):
```
$ sudo apt install pgadmin4
```

(Option) Run the web setup script:
```
$ sudo /usr/pgadmin4/bin/setup-web.sh
```