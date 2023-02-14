# WEB STACK IMPLEMENTATION (LEMP STACK)

In this project I will implement a similar stack as was done in Project 1, but with an alternative Web Server – NGINX, which is also very popular and widely used by many websites in the Internet. Note Pls - Previous project involved the implementation of Web Stacks - LAMP. 

LAMP (Linux, Apache, MySQL, PHP or Python, or Perl) is one of the Web stack Technologies which the DevOps Engineer uses as a set of frameworks and tools used to develop a software products(software, websites, applications).

Other technologies stacks used together by a DevOps Engineer for a specific technology product include...

LAMP (Linux, Apache, MySQL, PHP or Python, or Perl)
LEMP (Linux, Nginx, MySQL, PHP or Python, or Perl)
MERN (MongoDB, ExpressJS, ReactJS, NodeJS)
MEAN (MongoDB, ExpressJS, AngularJS, NodeJS

So we go right into deploying Web solutions using LEMP stacks, Apache web server was used earlier to build a website, I will used NGINX web server software for deploying the LEMP stack

## STEP 1 – INSTALLING THE NGINX WEB SERVER
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Try the new cross-platform PowerShell https://aka.ms/pscore6
PS C:\Users\EZEPC\Desktop> cd .\DevOps\
PS C:\Users\EZEPC\Desktop\DevOps> ssh -i "EZE_PBL2.pem" ubuntu@ec2-54-157-97-240.compute-1.amazonaws.com
The authenticity of host 'ec2-54-157-97-240.compute-1.amazonaws.com (54.157.97.240)' can't be established.
ECDSA key fingerprint is SHA256:afRnrqyGAwF9NLkJlAQSvjtjoiR5rPGxEfyfzhuo3BY.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'ec2-54-157-97-240.compute-1.amazonaws.com,54.157.97.240' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-1028-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Tue Feb 14 09:40:04 UTC 2023

  System load:  0.080078125       Processes:             95
  Usage of /:   20.0% of 7.57GB   Users logged in:       0
  Memory usage: 19%               IPv4 address for eth0: 172.31.4.14
  Swap usage:   0%

 * Introducing Expanded Security Maintenance for Applications.
   Receive updates to over 25,000 software packages with your
   Ubuntu Pro subscription. Free for personal use.

     https://ubuntu.com/aws/pro

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ip-172-31-4-14:~$ ls
ubuntu@ip-172-31-4-14:~$ sudo apt update
Hit:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Get:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB]
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Get:5 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages [14.1 MB]
Get:6 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/universe Translation-en [5652 kB]
Get:7 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [624 kB]
Get:8 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/universe amd64 c-n-f Metadata [286 kB]
Get:9 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages [217 kB]
Get:10 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/multiverse Translation-en [112 kB]
Get:11 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/multiverse amd64 c-n-f Metadata [8372 B]
Get:12 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [886 kB]
Get:13 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [194 kB]
Get:14 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [13.5 kB]
Get:15 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [609 kB]
Get:16 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [93.5 kB]
Get:17 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [805 kB]
Get:18 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [144 kB]
Get:19 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [15.4 kB]
Get:20 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [9340 B]
Get:21 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/multiverse Translation-en [3168 B]
Get:22 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [456 B]
Get:23 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/main amd64 Packages [40.7 kB]
Get:24 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/main Translation-en [9800 B]
Get:25 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/main amd64 c-n-f Metadata [392 B]
Get:26 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/restricted amd64 c-n-f Metadata [116 B]
Get:27 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [19.5 kB]
Get:28 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/universe Translation-en [13.8 kB]
Get:29 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 c-n-f Metadata [392 B]
Get:30 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-backports/multiverse amd64 c-n-f Metadata [116 B]
Get:31 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [131 kB]
Get:32 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [8360 B]
Get:33 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [550 kB]
Get:34 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [84.7 kB]
Get:35 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [639 kB]
Get:36 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [87.9 kB]
Get:37 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [11.3 kB]
Get:38 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 Packages [4960 B]
Get:39 http://security.ubuntu.com/ubuntu jammy-security/multiverse Translation-en [996 B]
Get:40 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 c-n-f Metadata [240 B]
Fetched 25.7 MB in 5s (5700 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
ubuntu@ip-172-31-4-14:~$ sudo apt install nginx
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  fontconfig-config fonts-dejavu-core libdeflate0 libfontconfig1 libgd3 libjbig0 libjpeg-turbo8 libjpeg8
  libnginx-mod-http-geoip2 libnginx-mod-http-image-filter libnginx-mod-http-xslt-filter libnginx-mod-mail
  libnginx-mod-stream libnginx-mod-stream-geoip2 libtiff5 libwebp7 libxpm4 nginx-common nginx-core
Suggested packages:
  libgd-tools fcgiwrap nginx-doc ssl-cert
The following NEW packages will be installed:
  fontconfig-config fonts-dejavu-core libdeflate0 libfontconfig1 libgd3 libjbig0 libjpeg-turbo8 libjpeg8
  libnginx-mod-http-geoip2 libnginx-mod-http-image-filter libnginx-mod-http-xslt-filter libnginx-mod-mail
  libnginx-mod-stream libnginx-mod-stream-geoip2 libtiff5 libwebp7 libxpm4 nginx nginx-common nginx-core
0 upgraded, 20 newly installed, 0 to remove and 5 not upgraded.
Need to get 2689 kB of archives.
After this operation, 8335 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 fonts-dejavu-core all 2.37-2build1 [1041 kB]
Get:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 fontconfig-config all 2.13.1-4.2ubuntu5 [29.1 kB]
Get:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libdeflate0 amd64 1.10-2 [70.9 kB]
Get:4 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libfontconfig1 amd64 2.13.1-4.2ubuntu5 [131 kB]
Get:5 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libjpeg-turbo8 amd64 2.1.2-0ubuntu1 [134 kB]
Get:6 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libjpeg8 amd64 8c-2ubuntu10 [2264 B]
Get:7 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libjbig0 amd64 2.1-3.1ubuntu0.22.04.1 [29.2 kB]
Get:8 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libwebp7 amd64 1.2.2-2 [206 kB]
Get:9 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtiff5 amd64 4.3.0-6ubuntu0.3 [183 kB]
Get:10 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libxpm4 amd64 1:3.5.12-1ubuntu0.22.04.1 [36.4 kB]
Get:11 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libgd3 amd64 2.3.0-2ubuntu2 [129 kB]
Get:12 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 nginx-common all 1.18.0-6ubuntu14.3 [40.0 kB]
Get:13 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnginx-mod-http-geoip2 amd64 1.18.0-6ubuntu14.3 [11.9 kB]
Get:14 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnginx-mod-http-image-filter amd64 1.18.0-6ubuntu14.3 [15.4 kB]
Get:15 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnginx-mod-http-xslt-filter amd64 1.18.0-6ubuntu14.3 [13.7 kB]
Get:16 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnginx-mod-mail amd64 1.18.0-6ubuntu14.3 [45.7 kB]
Get:17 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnginx-mod-stream amd64 1.18.0-6ubuntu14.3 [72.8 kB]
Get:18 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnginx-mod-stream-geoip2 amd64 1.18.0-6ubuntu14.3 [10.1 kB]
Get:19 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 nginx-core amd64 1.18.0-6ubuntu14.3 [482 kB]
Get:20 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 nginx amd64 1.18.0-6ubuntu14.3 [3882 B]
Fetched 2689 kB in 0s (29.5 MB/s)
Preconfiguring packages ...
Selecting previously unselected package fonts-dejavu-core.
(Reading database ... 63605 files and directories currently installed.)
Preparing to unpack .../00-fonts-dejavu-core_2.37-2build1_all.deb ...
Unpacking fonts-dejavu-core (2.37-2build1) ...
Selecting previously unselected package fontconfig-config.
Preparing to unpack .../01-fontconfig-config_2.13.1-4.2ubuntu5_all.deb ...
Unpacking fontconfig-config (2.13.1-4.2ubuntu5) ...
Selecting previously unselected package libdeflate0:amd64.
Preparing to unpack .../02-libdeflate0_1.10-2_amd64.deb ...
Unpacking libdeflate0:amd64 (1.10-2) ...
Selecting previously unselected package libfontconfig1:amd64.
Preparing to unpack .../03-libfontconfig1_2.13.1-4.2ubuntu5_amd64.deb ...
Unpacking libfontconfig1:amd64 (2.13.1-4.2ubuntu5) ...
Selecting previously unselected package libjpeg-turbo8:amd64.
Preparing to unpack .../04-libjpeg-turbo8_2.1.2-0ubuntu1_amd64.deb ...
Unpacking libjpeg-turbo8:amd64 (2.1.2-0ubuntu1) ...
Selecting previously unselected package libjpeg8:amd64.
Preparing to unpack .../05-libjpeg8_8c-2ubuntu10_amd64.deb ...
Unpacking libjpeg8:amd64 (8c-2ubuntu10) ...
Selecting previously unselected package libjbig0:amd64.
Preparing to unpack .../06-libjbig0_2.1-3.1ubuntu0.22.04.1_amd64.deb ...
Unpacking libjbig0:amd64 (2.1-3.1ubuntu0.22.04.1) ...
Selecting previously unselected package libwebp7:amd64.
Preparing to unpack .../07-libwebp7_1.2.2-2_amd64.deb ...
Unpacking libwebp7:amd64 (1.2.2-2) ...
Selecting previously unselected package libtiff5:amd64.
Preparing to unpack .../08-libtiff5_4.3.0-6ubuntu0.3_amd64.deb ...
Unpacking libtiff5:amd64 (4.3.0-6ubuntu0.3) ...
Selecting previously unselected package libxpm4:amd64.
Preparing to unpack .../09-libxpm4_1%3a3.5.12-1ubuntu0.22.04.1_amd64.deb ...
Unpacking libxpm4:amd64 (1:3.5.12-1ubuntu0.22.04.1) ...
Selecting previously unselected package libgd3:amd64.
Preparing to unpack .../10-libgd3_2.3.0-2ubuntu2_amd64.deb ...
Unpacking libgd3:amd64 (2.3.0-2ubuntu2) ...
Selecting previously unselected package nginx-common.
Preparing to unpack .../11-nginx-common_1.18.0-6ubuntu14.3_all.deb ...
Unpacking nginx-common (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package libnginx-mod-http-geoip2.
Preparing to unpack .../12-libnginx-mod-http-geoip2_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking libnginx-mod-http-geoip2 (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package libnginx-mod-http-image-filter.
Preparing to unpack .../13-libnginx-mod-http-image-filter_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking libnginx-mod-http-image-filter (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package libnginx-mod-http-xslt-filter.
Preparing to unpack .../14-libnginx-mod-http-xslt-filter_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking libnginx-mod-http-xslt-filter (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package libnginx-mod-mail.
Preparing to unpack .../15-libnginx-mod-mail_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking libnginx-mod-mail (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package libnginx-mod-stream.
Preparing to unpack .../16-libnginx-mod-stream_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking libnginx-mod-stream (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package libnginx-mod-stream-geoip2.
Preparing to unpack .../17-libnginx-mod-stream-geoip2_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking libnginx-mod-stream-geoip2 (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package nginx-core.
Preparing to unpack .../18-nginx-core_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking nginx-core (1.18.0-6ubuntu14.3) ...
Selecting previously unselected package nginx.
Preparing to unpack .../19-nginx_1.18.0-6ubuntu14.3_amd64.deb ...
Unpacking nginx (1.18.0-6ubuntu14.3) ...
Setting up libxpm4:amd64 (1:3.5.12-1ubuntu0.22.04.1) ...
Setting up libdeflate0:amd64 (1.10-2) ...
Setting up nginx-common (1.18.0-6ubuntu14.3) ...
Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
Setting up libjbig0:amd64 (2.1-3.1ubuntu0.22.04.1) ...
Setting up libnginx-mod-http-xslt-filter (1.18.0-6ubuntu14.3) ...
Setting up fonts-dejavu-core (2.37-2build1) ...
Setting up libjpeg-turbo8:amd64 (2.1.2-0ubuntu1) ...
Setting up libwebp7:amd64 (1.2.2-2) ...
Setting up libnginx-mod-http-geoip2 (1.18.0-6ubuntu14.3) ...
Setting up libjpeg8:amd64 (8c-2ubuntu10) ...
Setting up libnginx-mod-mail (1.18.0-6ubuntu14.3) ...
Setting up fontconfig-config (2.13.1-4.2ubuntu5) ...
Setting up libnginx-mod-stream (1.18.0-6ubuntu14.3) ...
Setting up libtiff5:amd64 (4.3.0-6ubuntu0.3) ...
Setting up libfontconfig1:amd64 (2.13.1-4.2ubuntu5) ...
Setting up libnginx-mod-stream-geoip2 (1.18.0-6ubuntu14.3) ...
Setting up libgd3:amd64 (2.3.0-2ubuntu2) ...
Setting up libnginx-mod-http-image-filter (1.18.0-6ubuntu14.3) ...
Setting up nginx-core (1.18.0-6ubuntu14.3) ...
 * Upgrading binary nginx                                                                                        [ OK ]
Setting up nginx (1.18.0-6ubuntu14.3) ...
Processing triggers for ufw (0.36.1-4build1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Scanning processes...
Scanning linux images...

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
ubuntu@ip-172-31-4-14:~$ sudo systemctl status nginx
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-02-14 09:42:41 UTC; 24s ago
       Docs: man:nginx(8)
    Process: 2173 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
    Process: 2174 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Main PID: 2267 (nginx)
      Tasks: 2 (limit: 1143)
     Memory: 4.6M
        CPU: 25ms
     CGroup: /system.slice/nginx.service
             ├─2267 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
             └─2270 "nginx: worker process" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" >

Feb 14 09:42:41 ip-172-31-4-14 systemd[1]: Starting A high performance web server and a reverse proxy server...
Feb 14 09:42:41 ip-172-31-4-14 systemd[1]: Started A high performance web server and a reverse proxy server.
ubuntu@ip-172-31-4-14:~$ curl http://localhost:80
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
ubuntu@ip-172-31-4-14:~$ curl http://127.0.0.1:80
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
ubuntu@ip-172-31-4-14:~$ curl -s http://169.254.169.254/latest/meta-data/public-ipv4
54.157.97.240ubuntu@ip-172-31-4-14:~$

## Picture Confirmation
![PBL2_Picture1](https://user-images.githubusercontent.com/122687798/218700674-e9e9dfa1-cbf7-48be-8a4e-17714c71843b.JPG)


## STEP 2 — INSTALLING MYSQL

Now that I have a web server up and running, I need to install a Database Management System (DBMS) to be able to store and manage data for my site in a relational database. MySQL is a popular relational database management system used within PHP environments, so i will proceed to use it on this project.

ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$ sudo apt install mysql-server
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libcgi-fast-perl libcgi-pm-perl libclone-perl libencode-locale-perl libevent-pthreads-2.1-7 libfcgi-bin libfcgi-perl
  libfcgi0ldbl libhtml-parser-perl libhtml-tagset-perl libhtml-template-perl libhttp-date-perl libhttp-message-perl
  libio-html-perl liblwp-mediatypes-perl libmecab2 libprotobuf-lite23 libtimedate-perl liburi-perl mecab-ipadic
  mecab-ipadic-utf8 mecab-utils mysql-client-8.0 mysql-client-core-8.0 mysql-common mysql-server-8.0
  mysql-server-core-8.0
Suggested packages:
  libdata-dump-perl libipc-sharedcache-perl libbusiness-isbn-perl libwww-perl mailx tinyca
The following NEW packages will be installed:
  libcgi-fast-perl libcgi-pm-perl libclone-perl libencode-locale-perl libevent-pthreads-2.1-7 libfcgi-bin libfcgi-perl
  libfcgi0ldbl libhtml-parser-perl libhtml-tagset-perl libhtml-template-perl libhttp-date-perl libhttp-message-perl
  libio-html-perl liblwp-mediatypes-perl libmecab2 libprotobuf-lite23 libtimedate-perl liburi-perl mecab-ipadic
  mecab-ipadic-utf8 mecab-utils mysql-client-8.0 mysql-client-core-8.0 mysql-common mysql-server mysql-server-8.0
  mysql-server-core-8.0
0 upgraded, 28 newly installed, 0 to remove and 5 not upgraded.
Need to get 29.5 MB of archives.
After this operation, 242 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 mysql-common all 5.8+1.0.8 [7212 B]
Get:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 mysql-client-core-8.0 amd64 8.0.32-0ubuntu0.22.04.2 [2677 kB]
Get:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 mysql-client-8.0 amd64 8.0.32-0ubuntu0.22.04.2 [22.7 kB]
Get:4 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libevent-pthreads-2.1-7 amd64 2.1.12-stable-1build3 [7642 B]
Get:5 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libmecab2 amd64 0.996-14build9 [199 kB]
Get:6 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libprotobuf-lite23 amd64 3.12.4-1ubuntu7 [208 kB]
Get:7 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 mysql-server-core-8.0 amd64 8.0.32-0ubuntu0.22.04.2 [17.5 MB]
Get:8 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 mysql-server-8.0 amd64 8.0.32-0ubuntu0.22.04.2 [1427 kB]
Get:9 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libhtml-tagset-perl all 3.20-4 [12.5 kB]
Get:10 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 liburi-perl all 5.10-1 [78.8 kB]
Get:11 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libhtml-parser-perl amd64 3.76-1build2 [88.4 kB]
Get:12 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libcgi-pm-perl all 4.54-1 [188 kB]
Get:13 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libfcgi0ldbl amd64 2.4.2-2build2 [28.0 kB]
Get:14 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libfcgi-perl amd64 0.82+ds-1build1 [22.8 kB]
Get:15 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libcgi-fast-perl all 1:2.15-1 [10.5 kB]
Get:16 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libclone-perl amd64 0.45-1build3 [11.0 kB]
Get:17 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libencode-locale-perl all 1.05-1.1 [11.8 kB]
Get:18 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libfcgi-bin amd64 2.4.2-2build2 [11.2 kB]
Get:19 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libhtml-template-perl all 2.97-1.1 [59.1 kB]
Get:20 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libtimedate-perl all 2.3300-2 [34.0 kB]
Get:21 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libhttp-date-perl all 6.05-1 [9920 B]
Get:22 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libio-html-perl all 1.004-2 [15.4 kB]
Get:23 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 liblwp-mediatypes-perl all 6.04-1 [19.5 kB]
Get:24 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 libhttp-message-perl all 6.36-1 [76.8 kB]
Get:25 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 mecab-utils amd64 0.996-14build9 [4850 B]
Get:26 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 mecab-ipadic all 2.7.0-20070801+main-3 [6718 kB]
Get:27 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 mecab-ipadic-utf8 all 2.7.0-20070801+main-3 [4384 B]
Get:28 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 mysql-server all 8.0.32-0ubuntu0.22.04.2 [9458 B]
Fetched 29.5 MB in 1s (27.6 MB/s)
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 63847 files and directories currently installed.)
Preparing to unpack .../0-mysql-common_5.8+1.0.8_all.deb ...
Unpacking mysql-common (5.8+1.0.8) ...
Selecting previously unselected package mysql-client-core-8.0.
Preparing to unpack .../1-mysql-client-core-8.0_8.0.32-0ubuntu0.22.04.2_amd64.deb ...
Unpacking mysql-client-core-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Selecting previously unselected package mysql-client-8.0.
Preparing to unpack .../2-mysql-client-8.0_8.0.32-0ubuntu0.22.04.2_amd64.deb ...
Unpacking mysql-client-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Selecting previously unselected package libevent-pthreads-2.1-7:amd64.
Preparing to unpack .../3-libevent-pthreads-2.1-7_2.1.12-stable-1build3_amd64.deb ...
Unpacking libevent-pthreads-2.1-7:amd64 (2.1.12-stable-1build3) ...
Selecting previously unselected package libmecab2:amd64.
Preparing to unpack .../4-libmecab2_0.996-14build9_amd64.deb ...
Unpacking libmecab2:amd64 (0.996-14build9) ...
Selecting previously unselected package libprotobuf-lite23:amd64.
Preparing to unpack .../5-libprotobuf-lite23_3.12.4-1ubuntu7_amd64.deb ...
Unpacking libprotobuf-lite23:amd64 (3.12.4-1ubuntu7) ...
Selecting previously unselected package mysql-server-core-8.0.
Preparing to unpack .../6-mysql-server-core-8.0_8.0.32-0ubuntu0.22.04.2_amd64.deb ...
Unpacking mysql-server-core-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Setting up mysql-common (5.8+1.0.8) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mysql-server-8.0.
(Reading database ... 64061 files and directories currently installed.)
Preparing to unpack .../00-mysql-server-8.0_8.0.32-0ubuntu0.22.04.2_amd64.deb ...
Unpacking mysql-server-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Selecting previously unselected package libhtml-tagset-perl.
Preparing to unpack .../01-libhtml-tagset-perl_3.20-4_all.deb ...
Unpacking libhtml-tagset-perl (3.20-4) ...
Selecting previously unselected package liburi-perl.
Preparing to unpack .../02-liburi-perl_5.10-1_all.deb ...
Unpacking liburi-perl (5.10-1) ...
Selecting previously unselected package libhtml-parser-perl:amd64.
Preparing to unpack .../03-libhtml-parser-perl_3.76-1build2_amd64.deb ...
Unpacking libhtml-parser-perl:amd64 (3.76-1build2) ...
Selecting previously unselected package libcgi-pm-perl.
Preparing to unpack .../04-libcgi-pm-perl_4.54-1_all.deb ...
Unpacking libcgi-pm-perl (4.54-1) ...
Selecting previously unselected package libfcgi0ldbl:amd64.
Preparing to unpack .../05-libfcgi0ldbl_2.4.2-2build2_amd64.deb ...
Unpacking libfcgi0ldbl:amd64 (2.4.2-2build2) ...
Selecting previously unselected package libfcgi-perl:amd64.
Preparing to unpack .../06-libfcgi-perl_0.82+ds-1build1_amd64.deb ...
Unpacking libfcgi-perl:amd64 (0.82+ds-1build1) ...
Selecting previously unselected package libcgi-fast-perl.
Preparing to unpack .../07-libcgi-fast-perl_1%3a2.15-1_all.deb ...
Unpacking libcgi-fast-perl (1:2.15-1) ...
Selecting previously unselected package libclone-perl.
Preparing to unpack .../08-libclone-perl_0.45-1build3_amd64.deb ...
Unpacking libclone-perl (0.45-1build3) ...
Selecting previously unselected package libencode-locale-perl.
Preparing to unpack .../09-libencode-locale-perl_1.05-1.1_all.deb ...
Unpacking libencode-locale-perl (1.05-1.1) ...
Selecting previously unselected package libfcgi-bin.
Preparing to unpack .../10-libfcgi-bin_2.4.2-2build2_amd64.deb ...
Unpacking libfcgi-bin (2.4.2-2build2) ...
Selecting previously unselected package libhtml-template-perl.
Preparing to unpack .../11-libhtml-template-perl_2.97-1.1_all.deb ...
Unpacking libhtml-template-perl (2.97-1.1) ...
Selecting previously unselected package libtimedate-perl.
Preparing to unpack .../12-libtimedate-perl_2.3300-2_all.deb ...
Unpacking libtimedate-perl (2.3300-2) ...
Selecting previously unselected package libhttp-date-perl.
Preparing to unpack .../13-libhttp-date-perl_6.05-1_all.deb ...
Unpacking libhttp-date-perl (6.05-1) ...
Selecting previously unselected package libio-html-perl.
Preparing to unpack .../14-libio-html-perl_1.004-2_all.deb ...
Unpacking libio-html-perl (1.004-2) ...
Selecting previously unselected package liblwp-mediatypes-perl.
Preparing to unpack .../15-liblwp-mediatypes-perl_6.04-1_all.deb ...
Unpacking liblwp-mediatypes-perl (6.04-1) ...
Selecting previously unselected package libhttp-message-perl.
Preparing to unpack .../16-libhttp-message-perl_6.36-1_all.deb ...
Unpacking libhttp-message-perl (6.36-1) ...
Selecting previously unselected package mecab-utils.
Preparing to unpack .../17-mecab-utils_0.996-14build9_amd64.deb ...
Unpacking mecab-utils (0.996-14build9) ...
Selecting previously unselected package mecab-ipadic.
Preparing to unpack .../18-mecab-ipadic_2.7.0-20070801+main-3_all.deb ...
Unpacking mecab-ipadic (2.7.0-20070801+main-3) ...
Selecting previously unselected package mecab-ipadic-utf8.
Preparing to unpack .../19-mecab-ipadic-utf8_2.7.0-20070801+main-3_all.deb ...
Unpacking mecab-ipadic-utf8 (2.7.0-20070801+main-3) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../20-mysql-server_8.0.32-0ubuntu0.22.04.2_all.deb ...
Unpacking mysql-server (8.0.32-0ubuntu0.22.04.2) ...
Setting up libmecab2:amd64 (0.996-14build9) ...
Setting up mysql-client-core-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Setting up libfcgi0ldbl:amd64 (2.4.2-2build2) ...
Setting up libclone-perl (0.45-1build3) ...
Setting up libhtml-tagset-perl (3.20-4) ...
Setting up liblwp-mediatypes-perl (6.04-1) ...
Setting up libfcgi-bin (2.4.2-2build2) ...
Setting up libencode-locale-perl (1.05-1.1) ...
Setting up libprotobuf-lite23:amd64 (3.12.4-1ubuntu7) ...
Setting up mecab-utils (0.996-14build9) ...
Setting up libio-html-perl (1.004-2) ...
Setting up libtimedate-perl (2.3300-2) ...
Setting up mysql-client-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Setting up libfcgi-perl:amd64 (0.82+ds-1build1) ...
Setting up liburi-perl (5.10-1) ...
Setting up libevent-pthreads-2.1-7:amd64 (2.1.12-stable-1build3) ...
Setting up libhttp-date-perl (6.05-1) ...
Setting up mecab-ipadic (2.7.0-20070801+main-3) ...
Compiling IPA dictionary for Mecab.  This takes long time...
reading /usr/share/mecab/dic/ipadic/unk.def ... 40
emitting double-array: 100% |###########################################|
/usr/share/mecab/dic/ipadic/model.def is not found. skipped.
reading /usr/share/mecab/dic/ipadic/Suffix.csv ... 1393
reading /usr/share/mecab/dic/ipadic/Noun.others.csv ... 151
reading /usr/share/mecab/dic/ipadic/Interjection.csv ... 252
reading /usr/share/mecab/dic/ipadic/Others.csv ... 2
reading /usr/share/mecab/dic/ipadic/Noun.place.csv ... 72999
reading /usr/share/mecab/dic/ipadic/Symbol.csv ... 208
reading /usr/share/mecab/dic/ipadic/Adnominal.csv ... 135
reading /usr/share/mecab/dic/ipadic/Noun.adjv.csv ... 3328
reading /usr/share/mecab/dic/ipadic/Noun.proper.csv ... 27328
reading /usr/share/mecab/dic/ipadic/Noun.org.csv ... 16668
reading /usr/share/mecab/dic/ipadic/Verb.csv ... 130750
reading /usr/share/mecab/dic/ipadic/Noun.verbal.csv ... 12146
reading /usr/share/mecab/dic/ipadic/Auxil.csv ... 199
reading /usr/share/mecab/dic/ipadic/Postp-col.csv ... 91
reading /usr/share/mecab/dic/ipadic/Noun.number.csv ... 42
reading /usr/share/mecab/dic/ipadic/Noun.demonst.csv ... 120
reading /usr/share/mecab/dic/ipadic/Noun.adverbal.csv ... 795
reading /usr/share/mecab/dic/ipadic/Adj.csv ... 27210
reading /usr/share/mecab/dic/ipadic/Filler.csv ... 19
reading /usr/share/mecab/dic/ipadic/Noun.csv ... 60477
reading /usr/share/mecab/dic/ipadic/Noun.name.csv ... 34202
reading /usr/share/mecab/dic/ipadic/Postp.csv ... 146
reading /usr/share/mecab/dic/ipadic/Conjunction.csv ... 171
reading /usr/share/mecab/dic/ipadic/Adverb.csv ... 3032
reading /usr/share/mecab/dic/ipadic/Prefix.csv ... 221
reading /usr/share/mecab/dic/ipadic/Noun.nai.csv ... 42
emitting double-array: 100% |###########################################|
reading /usr/share/mecab/dic/ipadic/matrix.def ... 1316x1316
emitting matrix      : 100% |###########################################|

done!
update-alternatives: using /var/lib/mecab/dic/ipadic to provide /var/lib/mecab/dic/debian (mecab-dictionary) in auto mode
Setting up mysql-server-core-8.0 (8.0.32-0ubuntu0.22.04.2) ...
Setting up mecab-ipadic-utf8 (2.7.0-20070801+main-3) ...
Compiling IPA dictionary for Mecab.  This takes long time...
reading /usr/share/mecab/dic/ipadic/unk.def ... 40
emitting double-array: 100% |###########################################|
/usr/share/mecab/dic/ipadic/model.def is not found. skipped.
reading /usr/share/mecab/dic/ipadic/Suffix.csv ... 1393
reading /usr/share/mecab/dic/ipadic/Noun.others.csv ... 151
reading /usr/share/mecab/dic/ipadic/Interjection.csv ... 252
reading /usr/share/mecab/dic/ipadic/Others.csv ... 2
reading /usr/share/mecab/dic/ipadic/Noun.place.csv ... 72999
reading /usr/share/mecab/dic/ipadic/Symbol.csv ... 208
reading /usr/share/mecab/dic/ipadic/Adnominal.csv ... 135
reading /usr/share/mecab/dic/ipadic/Noun.adjv.csv ... 3328
reading /usr/share/mecab/dic/ipadic/Noun.proper.csv ... 27328
reading /usr/share/mecab/dic/ipadic/Noun.org.csv ... 16668
reading /usr/share/mecab/dic/ipadic/Verb.csv ... 130750
reading /usr/share/mecab/dic/ipadic/Noun.verbal.csv ... 12146
reading /usr/share/mecab/dic/ipadic/Auxil.csv ... 199
reading /usr/share/mecab/dic/ipadic/Postp-col.csv ... 91
reading /usr/share/mecab/dic/ipadic/Noun.number.csv ... 42
reading /usr/share/mecab/dic/ipadic/Noun.demonst.csv ... 120
reading /usr/share/mecab/dic/ipadic/Noun.adverbal.csv ... 795
reading /usr/share/mecab/dic/ipadic/Adj.csv ... 27210
reading /usr/share/mecab/dic/ipadic/Filler.csv ... 19
reading /usr/share/mecab/dic/ipadic/Noun.csv ... 60477
reading /usr/share/mecab/dic/ipadic/Noun.name.csv ... 34202
reading /usr/share/mecab/dic/ipadic/Postp.csv ... 146
reading /usr/share/mecab/dic/ipadic/Conjunction.csv ... 171
reading /usr/share/mecab/dic/ipadic/Adverb.csv ... 3032
reading /usr/share/mecab/dic/ipadic/Prefix.csv ... 221
reading /usr/share/mecab/dic/ipadic/Noun.nai.csv ... 42
emitting double-array: 100% |###########################################|
reading /usr/share/mecab/dic/ipadic/matrix.def ... 1316x1316
emitting matrix      : 100% |###########################################|

done!
update-alternatives: using /var/lib/mecab/dic/ipadic-utf8 to provide /var/lib/mecab/dic/debian (mecab-dictionary) in auto mode
Setting up libhtml-parser-perl:amd64 (3.76-1build2) ...
Setting up libhttp-message-perl (6.36-1) ...
Setting up mysql-server-8.0 (8.0.32-0ubuntu0.22.04.2) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 2880
Created symlink /etc/systemd/system/multi-user.target.wants/mysql.service → /lib/systemd/system/mysql.service.
Setting up libcgi-pm-perl (4.54-1) ...
Setting up libhtml-template-perl (2.97-1.1) ...
Setting up mysql-server (8.0.32-0ubuntu0.22.04.2) ...
Setting up libcgi-fast-perl (1:2.15-1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Scanning processes...
Scanning linux images...

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
ubuntu@ip-172-31-4-14:~$ sudo mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.32-0ubuntu0.22.04.2 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
Query OK, 0 rows affected (0.01 sec)

mysql> exit
Bye
ubuntu@ip-172-31-4-14:~$ sudo mysql_secure_installation

Securing the MySQL server deployment.

Enter password for user root:

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: Y

There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary                  file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 0
Using existing password for root.

Estimated strength of the password: 100
Change the password for root ? ((Press y|Y for Yes, any other key for No) : G

 ... skipping.
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : F

 ... skipping.


Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : D

 ... skipping.
By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.


Remove test database and access to it? (Press y|Y for Yes, any other key for No) : R

 ... skipping.
Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : T

 ... skipping.
All done!
ubuntu@ip-172-31-4-14:~$ sudo mysql -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.0.32-0ubuntu0.22.04.2 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> exit
Bye
ubuntu@ip-172-31-4-14:~$

## STEP 3 – INSTALLING PHP

I have installed Nginx installed to serve my content and MySQL installed to store and manage my data. Now I can install PHP to process code and generate dynamic content for the web server.

While Apache embeds the PHP interpreter in each request, Nginx requires an external program to handle PHP processing and act as a bridge between the PHP interpreter itself and the web server. This allows for a better overall performance in most PHP-based websites, but it requires additional configuration.

I’ll need to install php-fpm, which stands for “PHP fastCGI process manager”, and tell Nginx to pass PHP requests to this software for processing. Additionally, I’ll need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. Core PHP packages will automatically be installed as dependencies.


ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$ sudo apt install php-fpm php-mysql
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  bzip2 mailcap mime-support php-common php8.1-cli php8.1-common php8.1-fpm php8.1-mysql php8.1-opcache
  php8.1-readline
Suggested packages:
  bzip2-doc php-pear
The following NEW packages will be installed:
  bzip2 mailcap mime-support php-common php-fpm php-mysql php8.1-cli php8.1-common php8.1-fpm php8.1-mysql
  php8.1-opcache php8.1-readline
0 upgraded, 12 newly installed, 0 to remove and 5 not upgraded.
Need to get 5388 kB of archives.
After this operation, 22.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 bzip2 amd64 1.0.8-5build1 [34.8 kB]
Get:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 mailcap all 3.70+nmu1ubuntu1 [23.8 kB]
Get:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 mime-support all 3.66 [3696 B]
Get:4 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 php-common all 2:92ubuntu1 [12.4 kB]
Get:5 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 php8.1-common amd64 8.1.2-1ubuntu2.10 [1126 kB]
Get:6 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 php8.1-opcache amd64 8.1.2-1ubuntu2.10 [365 kB]
Get:7 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 php8.1-readline amd64 8.1.2-1ubuntu2.10 [13.6 kB]
Get:8 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 php8.1-cli amd64 8.1.2-1ubuntu2.10 [1833 kB]
Get:9 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 php8.1-fpm amd64 8.1.2-1ubuntu2.10 [1840 kB]
Get:10 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/universe amd64 php-fpm all 2:8.1+92ubuntu1 [2838 B]
Get:11 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy-updates/main amd64 php8.1-mysql amd64 8.1.2-1ubuntu2.10 [130 kB]
Get:12 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 php-mysql all 2:8.1+92ubuntu1 [1834 B]
Fetched 5388 kB in 0s (43.9 MB/s)
Selecting previously unselected package bzip2.
(Reading database ... 64449 files and directories currently installed.)
Preparing to unpack .../00-bzip2_1.0.8-5build1_amd64.deb ...
Unpacking bzip2 (1.0.8-5build1) ...
Selecting previously unselected package mailcap.
Preparing to unpack .../01-mailcap_3.70+nmu1ubuntu1_all.deb ...
Unpacking mailcap (3.70+nmu1ubuntu1) ...
Selecting previously unselected package mime-support.
Preparing to unpack .../02-mime-support_3.66_all.deb ...
Unpacking mime-support (3.66) ...
Selecting previously unselected package php-common.
Preparing to unpack .../03-php-common_2%3a92ubuntu1_all.deb ...
Unpacking php-common (2:92ubuntu1) ...
Selecting previously unselected package php8.1-common.
Preparing to unpack .../04-php8.1-common_8.1.2-1ubuntu2.10_amd64.deb ...
Unpacking php8.1-common (8.1.2-1ubuntu2.10) ...
Selecting previously unselected package php8.1-opcache.
Preparing to unpack .../05-php8.1-opcache_8.1.2-1ubuntu2.10_amd64.deb ...
Unpacking php8.1-opcache (8.1.2-1ubuntu2.10) ...
Selecting previously unselected package php8.1-readline.
Preparing to unpack .../06-php8.1-readline_8.1.2-1ubuntu2.10_amd64.deb ...
Unpacking php8.1-readline (8.1.2-1ubuntu2.10) ...
Selecting previously unselected package php8.1-cli.
Preparing to unpack .../07-php8.1-cli_8.1.2-1ubuntu2.10_amd64.deb ...
Unpacking php8.1-cli (8.1.2-1ubuntu2.10) ...
Selecting previously unselected package php8.1-fpm.
Preparing to unpack .../08-php8.1-fpm_8.1.2-1ubuntu2.10_amd64.deb ...
Unpacking php8.1-fpm (8.1.2-1ubuntu2.10) ...
Selecting previously unselected package php-fpm.
Preparing to unpack .../09-php-fpm_2%3a8.1+92ubuntu1_all.deb ...
Unpacking php-fpm (2:8.1+92ubuntu1) ...
Selecting previously unselected package php8.1-mysql.
Preparing to unpack .../10-php8.1-mysql_8.1.2-1ubuntu2.10_amd64.deb ...
Unpacking php8.1-mysql (8.1.2-1ubuntu2.10) ...
Selecting previously unselected package php-mysql.
Preparing to unpack .../11-php-mysql_2%3a8.1+92ubuntu1_all.deb ...
Unpacking php-mysql (2:8.1+92ubuntu1) ...
Setting up php-common (2:92ubuntu1) ...
Created symlink /etc/systemd/system/timers.target.wants/phpsessionclean.timer → /lib/systemd/system/phpsessionclean.timer.
Setting up php8.1-common (8.1.2-1ubuntu2.10) ...

Creating config file /etc/php/8.1/mods-available/calendar.ini with new version

Creating config file /etc/php/8.1/mods-available/ctype.ini with new version

Creating config file /etc/php/8.1/mods-available/exif.ini with new version

Creating config file /etc/php/8.1/mods-available/fileinfo.ini with new version

Creating config file /etc/php/8.1/mods-available/ffi.ini with new version

Creating config file /etc/php/8.1/mods-available/ftp.ini with new version

Creating config file /etc/php/8.1/mods-available/gettext.ini with new version

Creating config file /etc/php/8.1/mods-available/iconv.ini with new version

Creating config file /etc/php/8.1/mods-available/pdo.ini with new version

Creating config file /etc/php/8.1/mods-available/phar.ini with new version

Creating config file /etc/php/8.1/mods-available/posix.ini with new version

Creating config file /etc/php/8.1/mods-available/shmop.ini with new version

Creating config file /etc/php/8.1/mods-available/sockets.ini with new version

Creating config file /etc/php/8.1/mods-available/sysvmsg.ini with new version

Creating config file /etc/php/8.1/mods-available/sysvsem.ini with new version

Creating config file /etc/php/8.1/mods-available/sysvshm.ini with new version

Creating config file /etc/php/8.1/mods-available/tokenizer.ini with new version
Setting up bzip2 (1.0.8-5build1) ...
Setting up php8.1-mysql (8.1.2-1ubuntu2.10) ...

Creating config file /etc/php/8.1/mods-available/mysqlnd.ini with new version

Creating config file /etc/php/8.1/mods-available/mysqli.ini with new version

Creating config file /etc/php/8.1/mods-available/pdo_mysql.ini with new version
Setting up php8.1-readline (8.1.2-1ubuntu2.10) ...

Creating config file /etc/php/8.1/mods-available/readline.ini with new version
Setting up mailcap (3.70+nmu1ubuntu1) ...
Setting up php8.1-opcache (8.1.2-1ubuntu2.10) ...

Creating config file /etc/php/8.1/mods-available/opcache.ini with new version
Setting up php-mysql (2:8.1+92ubuntu1) ...
Setting up mime-support (3.66) ...
Setting up php8.1-cli (8.1.2-1ubuntu2.10) ...
update-alternatives: using /usr/bin/php8.1 to provide /usr/bin/php (php) in auto mode
update-alternatives: using /usr/bin/phar8.1 to provide /usr/bin/phar (phar) in auto mode
update-alternatives: using /usr/bin/phar.phar8.1 to provide /usr/bin/phar.phar (phar.phar) in auto mode

Creating config file /etc/php/8.1/cli/php.ini with new version
Setting up php8.1-fpm (8.1.2-1ubuntu2.10) ...

Creating config file /etc/php/8.1/fpm/php.ini with new version
Created symlink /etc/systemd/system/multi-user.target.wants/php8.1-fpm.service → /lib/systemd/system/php8.1-fpm.service.
Setting up php-fpm (2:8.1+92ubuntu1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for php8.1-cli (8.1.2-1ubuntu2.10) ...
Processing triggers for php8.1-fpm (8.1.2-1ubuntu2.10) ...
Scanning processes...
Scanning linux images...

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
ubuntu@ip-172-31-4-14:~$


## STEP 4 — CONFIGURING NGINX TO USE PHP PROCESSOR

When using the Nginx web server, we can create server blocks (similar to virtual hosts in Apache) to encapsulate configuration details and host more than one domain on a single server. In this guide, I will use projectLEMP as an example domain name.

ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$ sudo mkdir /var/www/projectLEMP
ubuntu@ip-172-31-4-14:~$ sudo chown -R $USER:$USER /var/www/projectLEMP
ubuntu@ip-172-31-4-14:~$ sudo nano /etc/nginx/sites-available/projectLEMP
ubuntu@ip-172-31-4-14:~$ ubuntu@ip-172-31-4-14:~$ sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
ubuntu@ip-172-31-4-14:~$ sudo nginx -t
nginx: [emerg] unknown directive "i#/etc/nginx/sites-available/projectLEMP" in /etc/nginx/sites-enabled/projectLEMP:3
nginx: configuration file /etc/nginx/nginx.conf test failed
ubuntu@ip-172-31-4-14:~$ cat /etc/nginx/sites-available/projectLEMP
i#/etc/nginx/sites-available/projectLEMP

server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

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
ubuntu@ip-172-31-4-14:~$ sudo rm /etc/nginx/sites-available/projectLEMP
ubuntu@ip-172-31-4-14:~$ sudo nano /etc/nginx/sites-available/projectLEMP
ubuntu@ip-172-31-4-14:~$ sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
ln: failed to create symbolic link '/etc/nginx/sites-enabled/projectLEMP': File exists
ubuntu@ip-172-31-4-14:~$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
ubuntu@ip-172-31-4-14:~$ sudo unlink /etc/nginx/sites-enabled/default
ubuntu@ip-172-31-4-14:~$ sudo systemctl reload nginx
ubuntu@ip-172-31-4-14:~$ sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html
ubuntu@ip-172-31-4-14:~$

## Picture confirmation
![PBL2_Picture2](https://user-images.githubusercontent.com/122687798/218716879-3015b340-3fdc-44e3-92e0-a8a8b3ae7745.JPG)


## STEP 5 – TESTING PHP WITH NGINX

Now my LEMP stack is completely set up, At this point, the LAMP stack is completely installed and fully operational. I will proceed with testing it to validate that Nginx can correctly hand .php files off to your PHP processor.

ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$
ubuntu@ip-172-31-4-14:~$ sudo nano /var/www/projectLEMP/info.php
ubuntu@ip-172-31-4-14:~$ sudo rm /var/www/your_domain/info.php
rm: cannot remove '/var/www/your_domain/info.php': No such file or directory
ubuntu@ip-172-31-4-14:~$ http://54.157.97.240/info.php
-bash: http://54.157.97.240/info.php: No such file or directory
ubuntu@ip-172-31-4-14:~$ sudo rm /var/www/54.157.97.240/info.php
rm: cannot remove '/var/www/54.157.97.240/info.php': No such file or directory
ubuntu@ip-172-31-4-14:~$ sudo rm /var/www/projectLEMP/info.php
ubuntu@ip-172-31-4-14:~$

## Picture Confirmation
![PBL2_Picture3](https://user-images.githubusercontent.com/122687798/218721611-e88bea73-372a-4cf6-96f8-e5786106a0fd.JPG)

## Step 6 — Retrieving data from MySQL database with PHP

In this step, I will create a test database (DB) with simple "To do list" and configure access to it, so the Nginx website would be able to query data from the DB and display it.

ubuntu@ip-172-31-4-14:~$ sudo mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
ubuntu@ip-172-31-4-14:~$ sudo mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
ubuntu@ip-172-31-4-14:~$ sudo mysql -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 14
Server version: 8.0.32-0ubuntu0.22.04.2 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> mysql> CREATE DATABASE `example_database`;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql> CREATE DATABASE `example_database`' at line 1
mysql> CREATE DATABASE `example_database`;
Query OK, 1 row affected (0.01 sec)

mysql> CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
Query OK, 0 rows affected (0.03 sec)

mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';
Query OK, 0 rows affected (0.00 sec)

mysql> exit
Bye
ubuntu@ip-172-31-4-14:~$ mysql -u example_user -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 8.0.32-0ubuntu0.22.04.2 (Ubuntu)

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| example_database   |
| information_schema |
| performance_schema |
+--------------------+
3 rows in set (0.01 sec)

mysql> CREATE TABLE example_database.todo_list (
    -> mysql>     item_id INT AUTO_INCREMENT,
    -> mysql>     content VARCHAR(255),
    -> mysql>     PRIMARY KEY(item_id)
    -> mysql> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '>     item_id INT AUTO_INCREMENT,
mysql>     content VARCHAR(255),
mysql>     PR' at line 2
mysql> CREATE TABLE example_database.todo_list ( item_id INT AUTO_INCREMENT, content VARCHAR(255), PRIMARY KEY(item_id) );
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");
Query OK, 1 row affected (0.02 sec)

mysql> SELECT * FROM example_database.todo_list;SELECT * FROM example_database.todo_list;
+---------+-------------------------+
| item_id | content                 |
+---------+-------------------------+
|       1 | My first important item |
+---------+-------------------------+
1 row in set (0.00 sec)

+---------+-------------------------+
| item_id | content                 |
+---------+-------------------------+
|       1 | My first important item |
+---------+-------------------------+
1 row in set (0.00 sec)

mysql> exit;
Bye
ubuntu@ip-172-31-4-14:~$ nano /var/www/projectLEMP/todo_list.php
ubuntu@ip-172-31-4-14:~$

## Picture Confirmation

![PBL2_Picture4](https://user-images.githubusercontent.com/122687798/218726641-dcf6e71f-feea-4330-9cea-8f22380dc943.JPG)

