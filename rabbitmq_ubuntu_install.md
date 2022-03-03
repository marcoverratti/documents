# RabbitMQ Ubuntu Install

## 1. Install RabbitMQ Server Ubuntu 22.04|20.04|18.04
Update apt list first:

```
$ sudo apt update
```

Then install ```rabbitmq-server``` package:
```
$ sudo apt install rabbitmq-server
```

After installation, RabbitMQ service is started and enabled to start on boot. To check the status, run:
```
$ systemctl status rabbitmq-server.service
```
<img src='https://i.ibb.co/mcFNNgb/Untitled.png'></img>

## 2. Enable the RabbitMQ Management Dashboard
```
$ sudo rabbitmq-plugins enable rabbitmq_management
```
The Web service should be listening on TCP port 15672
```
$ sudo ss -tunelp | grep 15672
```
<img src="https://i.ibb.co/zJhw9JQ/Untitled.png"></img>
### Create an admin user
```
$ sudo rabbitmqctl add_user <UserName> <StrongPassword>
$ sudo rabbitmqctl set_user_tags <UserName> administrator
```
Login with this admin username and the password assigned.

# References
[Install RabbitMQ Server on Ubuntu 22.04|20.04|18.04](https://computingforgeeks.com/how-to-install-latest-rabbitmq-server-on-ubuntu-linux/)

More in [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/)
