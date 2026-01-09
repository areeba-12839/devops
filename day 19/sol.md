thor@jumphost ~$ ls -F
demo/  media/
thor@jumphost ~$ mv beta media
mv: cannot stat 'beta': No such file or directory
thor@jumphost ~$ mv beta media
mv games demo
mv: cannot stat 'beta': No such file or directory
mv: cannot stat 'games': No such file or directory
thor@jumphost ~$ ^C
thor@jumphost ~$ scp -r media tony@stapp01:/tmp/
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:BYR+PJjpjRfztMkxdQ1aqp9o90zEy5BFNhpLcpPxW/g.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
index.html   100%  118   196.2KB/s   00:00    
thor@jumphost ~$ scp -r demo tony@stapp01:/tmp/tony@stapp01's password: 
index.html   100%  117   245.5KB/s   00:00    
thor@jumphost ~$ ssh tony@stapp01
tony@stapp01's password: 
[tony@stapp01 ~]$ scp -r media tony@stapp01:/tmp/
scp -r demo tony@stapp01:/tmp/
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:BYR+PJjpjRfztMkxdQ1aqp9o90zEy5BFNhpLcpPxW/g.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
stat local "media": No such file or directory
tony@stapp01's password: 
stat local "demo": No such file or directory
[tony@stapp01 ~]$ sudo -i

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[root@stapp01 ~]# yum install httpd -y
CentOS Stream   45 kB/s | 6.7 kB     00:00    
CentOS Stream   17 MB/s | 8.8 MB     00:00    
CentOS Stream   31 kB/s | 6.8 kB     00:00    
CentOS Stream   20 MB/s |  26 MB     00:01    
CentOS Stream   30 kB/s | 7.3 kB     00:00    
CentOS Stream   52 kB/s |  20 kB     00:00    
Extra Packages 145 kB/s |  32 kB     00:00    
Extra Packages  25 MB/s |  20 MB     00:00    
Extra Packages 6.1 kB/s | 993  B     00:00    
Extra Packages  94 kB/s |  21 kB     00:00    
Extra Packages 291 kB/s | 259 kB     00:00    
Dependencies resolved.
===============================================
 Package  Arch   Version       Repo       Size
===============================================
Installing:
 httpd    x86_64 2.4.62-10.el9 appstream  46 k
Installing dependencies:
 apr      x86_64 1.7.0-12.el9  appstream 123 k
 apr-util x86_64 1.6.1-23.el9  appstream  95 k
 apr-util-bdb
          x86_64 1.6.1-23.el9  appstream  13 k
 centos-logos-httpd
          noarch 90.8-3.el9    appstream 1.5 M
 httpd-core
          x86_64 2.4.62-10.el9 appstream 1.5 M
 httpd-filesystem
          noarch 2.4.62-10.el9 appstream  12 k
 httpd-tools
          x86_64 2.4.62-10.el9 appstream  81 k
 libbrotli
          x86_64 1.0.9-7.el9   baseos    313 k
 mailcap  noarch 2.1.49-5.el9  baseos     33 k
Installing weak dependencies:
 apr-util-openssl
          x86_64 1.6.1-23.el9  appstream  15 k
 mod_http2
          x86_64 2.0.26-5.el9  appstream 163 k
 mod_lua  x86_64 2.4.62-10.el9 appstream  58 k

Transaction Summary
===============================================
Install  13 Packages

Total download size: 3.9 M
Installed size: 9.5 M
Downloading Packages:
(1/13): mailca 238 kB/s |  33 kB     00:00    
(2/13): libbro 1.2 MB/s | 313 kB     00:00    
(3/13): apr-1. 268 kB/s | 123 kB     00:00    
(4/13): apr-ut 257 kB/s |  95 kB     00:00    
(5/13): apr-ut  50 kB/s |  13 kB     00:00    
(6/13): apr-ut  58 kB/s |  15 kB     00:00    
(7/13): httpd- 147 kB/s |  46 kB     00:00    
(8/13): centos 2.9 MB/s | 1.5 MB     00:00    
(9/13): httpd-  46 kB/s |  12 kB     00:00    
(10/13): httpd 2.9 MB/s | 1.5 MB     00:00    
(11/13): httpd 229 kB/s |  81 kB     00:00    
(12/13): mod_h 405 kB/s | 163 kB     00:00    
(13/13): mod_l 177 kB/s |  58 kB     00:00    
-----------------------------------------------
Total          2.1 MB/s | 3.9 MB     00:01     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Installing       : apr-1.7.0-12.el9.    1/13 
  Installing       : apr-util-bdb-1.6.    2/13 
  Installing       : apr-util-openssl-    3/13 
  Installing       : apr-util-1.6.1-23    4/13 
  Installing       : httpd-tools-2.4.6    5/13 
  Running scriptlet: httpd-filesystem-    6/13 
  Installing       : httpd-filesystem-    6/13 
  Installing       : centos-logos-http    7/13 
  Installing       : mailcap-2.1.49-5.    8/13 
  Installing       : httpd-core-2.4.62    9/13 
  Installing       : mod_lua-2.4.62-10   10/13 
  Installing       : libbrotli-1.0.9-7   11/13 
  Installing       : mod_http2-2.0.26-   12/13 
  Installing       : httpd-2.4.62-10.e   13/13 
  Running scriptlet: httpd-2.4.62-10.e   13/13 
  Verifying        : libbrotli-1.0.9-7    1/13 
  Verifying        : mailcap-2.1.49-5.    2/13 
  Verifying        : apr-1.7.0-12.el9.    3/13 
  Verifying        : apr-util-1.6.1-23    4/13 
  Verifying        : apr-util-bdb-1.6.    5/13 
  Verifying        : apr-util-openssl-    6/13 
  Verifying        : centos-logos-http    7/13 
  Verifying        : httpd-2.4.62-10.e    8/13 
  Verifying        : httpd-core-2.4.62    9/13 
  Verifying        : httpd-filesystem-   10/13 
  Verifying        : httpd-tools-2.4.6   11/13 
  Verifying        : mod_http2-2.0.26-   12/13 
  Verifying        : mod_lua-2.4.62-10   13/13 

Installed:
  apr-1.7.0-12.el9.x86_64                      
  apr-util-1.6.1-23.el9.x86_64                 
  apr-util-bdb-1.6.1-23.el9.x86_64             
  apr-util-openssl-1.6.1-23.el9.x86_64         
  centos-logos-httpd-90.8-3.el9.noarch         
  httpd-2.4.62-10.el9.x86_64                   
  httpd-core-2.4.62-10.el9.x86_64              
  httpd-filesystem-2.4.62-10.el9.noarch        
  httpd-tools-2.4.62-10.el9.x86_64             
  libbrotli-1.0.9-7.el9.x86_64                 
  mailcap-2.1.49-5.el9.noarch                  
  mod_http2-2.0.26-5.el9.x86_64                
  mod_lua-2.4.62-10.el9.x86_64                 

Complete!
[root@stapp01 ~]# sed -i 's/Listen 80/Listen 8082/g' /etc/httpd/conf/httpd.conf
[root@stapp01 ~]# mv /tmp/media /var/www/html/
[root@stapp01 ~]# mv /tmp/demo /var/www/html/
[root@stapp01 ~]# systemctl start httpd
[root@stapp01 ~]# systemctl enable httpd
Created symlink /etc/systemd/system/multi-user.target.wants/httpd.service → /usr/lib/systemd/system/httpd.service.
[root@stapp01 ~]# curl http://localhost:8082/media/
<!DOCTYPE html>
<html>
<body>

<h1>KodeKloud</h1>

<p>This is a sample page for our media website</p>

</body>
</html>[root@stapp01 ~]# curl http://localhost:8082/demo/
<!DOCTYPE html>
<html>
<body>

<h1>KodeKloud</h1>

<p>This is a sample page for our demo website</p>

</body>
[root@stapp01 ~]# 