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


<br>

### U22, LEMP —( M ) MySQL

#### Installation,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo apt-cache policy mysql-server`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo apt-get install mysql-server`

`anup@ubuntu-22041-100-anuniqsTV:~$ dpkg -l | grep -i "mysql-server"`


#### Version,

`anup@ubuntu-22041-100-anuniqsTV:~$ mysql -V`


#### Service Control,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo systemctl status mysql.service `

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo systemctl enable mysql.service `


#### Securing the MariaDB Server,

    1!vQxy@KczdAHh

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo mysql_secure_installation`

#### For any error, kill process and do below,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo pkill -f mysql_secure_installation`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo mysql`

    mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by '1!vQxy@KczdAHh';
    
    mysql> exit


#### Logs,

`anup@ubuntu-22041-100-anuniqsTV:~$ ls -ltr /var/log/mysql/`



#### Port, 3306, and Process,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo lsof -i -P -n | grep LISTEN`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo netstat -tulpn | grep LISTEN`

`anup@ubuntu-22041-100-anuniqsTV:~$ ps -aux | grep -i "mysql"`


#### Directory,

Configuration, `anup@ubuntu-22041-100-anuniqsTV:~$ ls -ltr /etc/mysql/`



#### Firewall,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ufw allow 3306`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ufw app list`



`anup@ubuntu-22041-100-anuniqsTV:~$ sudo mysql -u root -p -h localhost , 1!vQxy@KczdAHh`

    mysql> show databases; 
    
    mysql> SELECT User, Host, plugin FROM mysql.user;

#### Create bookstore databse,

    mysql> CREATE DATABASE bookstore;
    
    mysql> use bookstore;

#### Create books table,

    CREATE TABLE books (
    isbn CHAR(20) PRIMARY KEY,
    title VARCHAR(50),
    author_id INT,
    publisher_id INT,
    year_pub CHAR(4),
    description TEXT );

<br>

    mysql> DESCRIBE books;

<br>

    INSERT INTO books
    (title, author_id, isbn, year_pub)
    VALUES('The Castle', '1', '0805211063', '1998');

<br>

    mysql> select * from books;

<br>

    INSERT INTO books
    (title, author_id, isbn, year_pub)
    VALUES('The Trial', '1', '0805210407', '1995'),
    ('The Metamorphosis', '1', '0553213695', '1995'),
    ('America', '1', '0805210644', '1995');

<br>

    mysql> select * from books;

<br>

#### Create authors table,

    CREATE TABLE authors 
    (author_id INT AUTO_INCREMENT PRIMARY KEY,
    name_last VARCHAR(50),
    name_first VARCHAR(50), country VARCHAR(50) );

<br>

    mysql> DESCRIBE authors;

<br>

    INSERT INTO authors
    (name_last, name_first)
    VALUES('Kafka', 'Franz');



#### Create a user,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo mysql -u root -p -h localhost`

    mysql> CREATE USER 'anuniqs'@'%' IDENTIFIED WITH mysql_native_password BY 'aBkJwU@@Cmc9B';
    
    mysql> GRANT ALL ON bookstore.* TO 'anuniqs'@'%';
    
    mysql> FLUSH PRIVILEGES;
    
    mysql> exit



#### Login as anup,

`anup@ubuntu-22041-100-anuniqsTV:~$ mysql -u anuniqs -p`

    mysql> show databases;
    mysql> use bookstore;
    mysql> show tables;
    mysql> exit

<br>
<br>

### U22, LEMP —( P ) PHP

#### Installation,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo apt-cache policy php`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo apt install php8.1-fpm php-mysql`

`anup@ubuntu-22041-100-anuniqsTV:~$ dpkg -l | grep -i "php"`

#### Version,

`anup@ubuntu-22041-100-anuniqsTV:~$ php -v`

#### Logs,

By default, /var/log/nginx/error.log  , But this can be configured in /etc/php5/apache2/php.ini.

`anup@ubuntu-22041-100-anuniqsTV:~$ ls /var/log/nginx/error.log `

#### Directory,

`anup@ubuntu-22041-100-anuniqsTV:~$ ls -ltr /etc/php/8.1/`

#### Nginx Server Blocks,

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo mkdir /var/www/anuniqstv.lemp.ek`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo chown -R $USER:$USER /var/www/anuniqstv.lemp.ek/`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo nano /etc/nginx/sites-available/anuniqstv.lemp.ek`

    server {
        listen 80;
        server_name anuniqstv.lemp.ek www.anuniqstv.lemp.ek;
        root /var/www/anuniqstv.lemp.ek;
    
        index index.html index.htm index.php;
    
        location / {
            try_files $uri $uri/ =404;
        }
    
        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
         }
    
        location ~ /\.ht {
            deny all;
        }
    
    }

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo ln -s /etc/nginx/sites-available/anuniqstv.lemp.ek /etc/nginx/sites-enabled/`

`anup@ubuntu-22041-100-anuniqsTV:~$ ls -ltr /etc/nginx/sites-enabled/`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo unlink /etc/nginx/sites-enabled/default`

For future link again , sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo nginx -t`

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo systemctl reload nginx.service `

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo systemctl status nginx.service `



`anup@ubuntu-22041-100-anuniqsTV:~$ nano /var/www/anuniqstv.lemp.ek/index.html`

http://192.168.56.100/

### Test PHP

`anup@ubuntu-22041-100-anuniqsTV:~$ nano /var/www/anuniqstv.lemp.ek/info.php`


    <?php
    phpinfo();

http://192.168.56.100/info.php

#### Test DB

`anup@ubuntu-22041-100-anuniqsTV:~$ sudo mysql -u root -p -h localhost` , `1!vQxy@KczdAHh`

    mysql> anup@ubuntu-22041-100-anuniqsTV:~$ sudo mysql -u root -p -h localhost^C
    
    mysql> CREATE USER 'lampuser'@'%' IDENTIFIED WITH mysql_native_password BY 'aBkJwU@@Cmc9B';
    
    mysql> GRANT ALL ON lampdb.* TO 'lampuser'@'%';
    
    mysql> exit

`anup@ubuntu-22041-100-anuniqsTV:~$ mysql -u lampuser -p , aBkJwU@@Cmc9B`

    mysql> SHOW DATABASES;

<br>

    CREATE TABLE lampdb.lamptable (
    	item_id INT AUTO_INCREMENT,
    	content VARCHAR(255),
    	PRIMARY KEY(item_id)
    );

<br>

    mysql> describe lampdb.lamptable;
    
    mysql> INSERT INTO lampdb.lamptable (content) VALUES ("Lamp data ek");
    
    mysql> INSERT INTO lampdb.lamptable (content) VALUES ("Lamp data dui");
    
    mysql> INSERT INTO lampdb.lamptable (content) VALUES ("Lamp data tin");
    
    mysql> INSERT INTO lampdb.lamptable (content) VALUES ("Lamp data char");

<br>

    mysql> select * from lampdb.lamptable;
    
    mysql> exit

`anup@ubuntu-22041-100-anuniqsTV:~$ nano /var/www/anuniqstv.lemp.ek/lampdata.php`

    <?php
    $user = "lampuser";
    $password = "aBkJwU@@Cmc9B";
    $database = "lampdb";
    $table = "lamptable";
    
    try {
      $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
      echo "<h2>TODO</h2><ol>"; 
      foreach($db->query("SELECT content FROM $table") as $row) {
        echo "<li>" . $row['content'] . "</li>";
      }
      echo "</ol>";
    } catch (PDOException $e) {
        print "Error!: " . $e->getMessage() . "<br/>";
        die();
    }

http://192.168.56.100/lampdata.php
