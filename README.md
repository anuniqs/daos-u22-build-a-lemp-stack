### U22, LEMP —( L ) Linux

`anup@ubuntu-22041-100-anuniqsTV:~$ cat /etc/os-release`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo apt-get update`

<br>

### U22, LEMP —( E , engine-x ) NGINX

#### Installation,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo apt-cache policy nginx`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo apt install nginx-full `

`anup@ubuntu-22041-100-anuniqsTV:~$ dpkg -l | grep -i "nginx"`


#### Version,

`anup@ubuntu-22041-100-anuniqsTV:~$ nginx -v`


#### Service Control,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo systemctl status nginx.service `

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo systemctl enable nginx.service `


#### Logs,

`anup@ubuntu-22041-100-anuniqsTV:~$ ls -ltr /var/log/nginx/`


#### Port, 80, 443, and Process,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo lsof -i -P -n | grep LISTEN`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo netstat -tulpn | grep LISTEN`

`anup@ubuntu-22041-100-anuniqsTV:~$ ps -aux | grep -i "nginx"`


#### Directory,

Installation : `/usr/sbin/nginx`

Work directory : `/var/www/html/`

Configurations : `/etc/nginx/`


#### Firewall,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ufw status`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ufw enable `

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ufw allow 80`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ufw allow 443`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ufw app list`


#### Access Web Interface,

`anup@ubuntu-22041-100-anuniqsTV:~$ telnet 192.168.56.100 80`

`anup@ubuntu-22041-100-anuniqsTV:~$ curl -Is http://192.168.56.100 | head -1`

http://192.168.56.100/
