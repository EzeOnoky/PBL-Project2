# PBL-Project2
Darey.io project based learning PBL2

# WEB STACK IMPLEMENTATION (LEMP STACK)
We implemented a similar stack as was done in Project 1, but with an alternative Web Server – APACHE, which is also very popular and widely used by many websites in the Internet. Note - Previous project involved the implementation of Web Stacks - LAMP.

LAMP (Linux, Apache, MySQL, PHP or Python, or Perl) is one of the Web stack Technologies which the DevOps Engineer uses as a set of frameworks and tools used to develop a software products(software, websites, applications).

Other technologies stacks used together by a DevOps Engineer for a specific technology product include...

- LAMP (Linux, Apache, MySQL, PHP or Python, or Perl) 
- LEMP (Linux, Nginx, MySQL, PHP or Python, or Perl) 
- MERN (MongoDB, ExpressJS, ReactJS, NodeJS) 
- MEAN (MongoDB, ExpressJS, AngularJS, NodeJS)

So we go right into deploying Web solutions using LEMP stacks, Apache web server was used earlier to build a website, I will used NGINX web server software for deploying the LEMP stack

#  INSTALLING THE NGINX WEB SERVER

![2_1](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/4dc3ddf3-005a-4922-88b3-6199b1e253bf)

So we launch our Instance, To download the nginx web server, we first update the server's package.

`sudo apt update`

After the update, we then go ahead to install the nginx web server by running:

`sudo apt install nginx`

we click on "y" to confirm installation.

To verify that nginx was downloaded and installed successfully, we run:

$ sudo systemctl status nginx

if it shows "green" and "running", then it was successfully installed.

![2_2](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/3335af5a-2812-4f7e-8836-f424b4964718)

We then go to our instance and set the inbound rules and save

![2_3](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/ee2286ec-5dd3-4748-a1ec-c4b75669483b)

To test how our nginx server responds to requests from the internet, we open our browser and use this url:

`http://<Public-IP-Address>:80`

![2_4](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/80912167-82f6-4e79-a314-b351d53abec7)

# SETTING UP MYSQL DATABASE

Now that we have our webserver up and running, we need a Database Management System(DBMS).

To install Mysql server, we run the command:

`sudo apt install mysql-server`

we click on "y" to confirm installation.

When installation is done, we log in by running the command:

`sudo mysql`

This will connect to the MySQL server as the administrative database user root:

![2_5](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/16f88748-765c-4511-a249-bcbb8f384571)

We run a security script that comes pre-installed with MySQL. This script will remove some insecure default settings and lock down access to your database system. Before running the script you will set a password for the root user, using "mysql_native_password" as default authentication method. We choose a user’s password as "PassWord.1".

`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

![2_6](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/050d4df1-c5ce-4adf-90e9-4e830f64617a)

We "exit" the mysql and start the script by running the command:

`sudo mysql_secure_installation`

This will ask for password, create password you would want and go ahead and type "yes" to all subsequent prompts.

When we are done, we test if we can log into the mysql by runnimg the command:

`sudo mysql -p`

there will be a prompt for you to put in the password you created earlier.

![2_7](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/4960e02d-0e34-428f-876c-78cfc047f8ed)

Let us create a database named "example_database" and a user named "example_user", but you can replace these names with different values.

![2_8](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/1f934a05-4966-4f77-be9d-bf25fc07489b)

We then create the new user (example_user) and grant full priviledges on the database we just created by running the command:

`CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY '<new-password>';`

we replace **"new-password"** by the new password we created earlier.

To give this user permission over the datatbase, we run the command:

`GRANT ALL ON example_database.* TO 'example_user'@'%';`

then **"exit"**.

![2_9](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/ab25bc95-927b-410f-8731-6596e3c6e762)

we log into the mysql again with custom user credentials to test if the permissions were granted by running the command:

$ sudo mysql -u example_user -p

we put in our password at the prompt.

![2_10](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/f9b6249a-d1c2-4468-a2b0-3319cf490e2a)

Next, we run the command:

`SHOW DATABASES;`

![2_11](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/d77ce512-093f-471a-8705-6ac5edd5ac27)

# SETTING UP PHP

We have the nginx server running for the web server and the mysql to handle the database. we need to install PHP to handle the codes. To install PHP, we run the command:

`sudo apt install php-fpm php-mysql`

we type "y" at the prompt and click__"ENTER"__.

# CONFIGURING NGINX TO USE PHP PROCESSOR

To set up the nginx to use the PHP processor, we first create a root web directory by creating a directory in **"/var/www/"**

`sudo mkdir /var/www/projectLEMP`

next we assign ownership to the directory

`sudo chown -R $USER:$USER /var/www/projectLEMP`

![2_12](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/abb8666c-8c5a-4ebe-a691-eb561d172e5c)

create and open a new configuration file in nginx"s **sites-available**

`sudo nano /etc/nginx/sites-available/projectLEMP`

paste in the following:

```
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```

we click **"CTRL+"x"** and then **"y"** then **"ENTER"**

![2_13](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/8499bf45-d1ab-4f7c-9a9e-890bcbba2b0d)

in the above the **php 7.4** version, Make sure to specify the version of the PHP. To check the PHP version we use the command:

`php -v`

To activate the configuration, we link to the configuration file in Nginx’s sites-enabled directory:

`sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`

This will instruct the nginx to use the configuration next time it is loaded. We then run the command:

`sudo nginx -t`

we will see the following:

**nginx: the configuration file /etc/nginx/nginx.conf syntax is ok nginx: configuration file /etc/nginx/nginx.conf test is successful**

If it displays any errors, we go back and review the configurations.

To disable the default nginx host that is currently configured to listen on port 80

`sudo unlink /etc/nginx/sites-enabled/default`

we reload nginx by running the command:

`sudo systemctl reload nginx`

![2_14](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/0693c32a-827a-41eb-b797-32ff1c446212)

The new website is now active, but the web root **"/var/www/projectLEMP"** is still empty.

We create an "index.html" in the **"/var/www/projectLEMP"** directory:

```
sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html
```

We go to the browser and try to open the URL using IP address

`http://<Public-IP-Address>:80`

We should see the text from the **echo command**. This shows that the nginx site is working as expected.

# TESTING PHP WITH NGINX

The LEMP stack is completely setup. To test that the nginx can hand .php files to PHP processor, we create a file info.php in the **"/var/www/PROJECTLEMP"**

`sudo nano /var/www/projectLEMP/info.php`

and paste the following:

```
<?php
phpinfo();
```

![2_15](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/7d19e2b3-cd40-4841-aaa9-da517375bd75)

We can now access this by adding **info.php** to the URL on the browser

`http://<Public-IP-Address>/info.php`

We should see a web page containing information about PHP

![2_16](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/01b408f9-92eb-4f12-92a4-3f93260c42b9)

To create a test table, we log into the mysql:

`mysql -u example_user -p`

We log in using our password.

Next, we run the command:

`SHOW DATABASES;`

This will give the following output

```
 Output
+--------------------+
| Database           |
+--------------------+
| example_database   |
| information_schema |
+--------------------+
2 rows in set (0.000 sec)
```

Next, we create a test table named todo_list.php

```
mysql> CREATE TABLE example_database.todo_list (
mysql>     item_id INT AUTO_INCREMENT,
mysql>     content VARCHAR(255),
mysql>     PRIMARY KEY(item_id)
mysql> );
```

we insert a few rows using the command, NOTE: click on ENTER after each command line

```
mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");
mysql> INSERT INTO example_database.todo_list (content) VALUES ("another important item");
mysql> INSERT INTO example_database.todo_list (content) VALUES ("just another important item");
mysql> INSERT INTO example_database.todo_list (content) VALUES ("an important item");
```

To confirm the values were succesfully stored in the table, we run the command:

`mysql>  SELECT * FROM example_database.todo_list;`

The following output will be displayed.

![2_17](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/9d3ff612-aa1e-45d9-8dc8-4eb7e8d5bbf9)


![2_18](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/b675b79b-68e8-4afe-95fa-732804791701)

Now we create a PHP script that will connect to mysql:

`vi /var/www/projectLEMP/todo_list.php`

we paste the following into the below file:

```
<?php
$user = "example_user";
$password = "password";
$database = "example_database";
$table = "todo_list";

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
```

in the **password = "password"** , we replace **password** with our own *password*

We save and close the file.


![2_19](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/679071ab-af8e-4f19-adcf-e9b76c0c7df6)

we can now access the page using:

`http://<Public-IP-Address>/info.php`

we should see this display

![2_20](https://github.com/EzeOnoky/Project-Base-Learning-2/assets/122687798/d45c2f99-13ba-4293-8d36-6986c8865a29)

That means your PHP environment is ready to connect and interact with your MySQL server.


# Congratulations EZE!
You have been able to build a flexible foundation for serving PHP websites and applications to visitors on your web site, using Nginx as web server and MySQL as database management system.








