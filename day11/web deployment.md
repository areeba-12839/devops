Last login: Sun Oct 12 18:33:09 UTC 2025 on pts/0
thor@jumphost ~$ ssh tony@stapp01
tony@stapp01's password: 
Last login: Sun Oct 12 18:40:43 2025 from 172.16.238.3
[tony@stapp01 ~]$ sudo yum install -y tomcat tomcat-webapps tomcat-admin-webapps
[sudo] password for tony: 
Last metadata expiration check: 0:09:35 ago on Sun Oct 12 18:41:39 2025.
Package tomcat-1:9.0.87-6.el9.noarch is already installed.
Dependencies resolved.
===============================================
 Package Arch   Version        Repo       Size
===============================================
Installing:
 tomcat-admin-webapps
         noarch 1:9.0.87-6.el9 appstream  77 k
 tomcat-webapps
         noarch 1:9.0.87-6.el9 appstream  80 k

Transaction Summary
===============================================
Install  2 Packages

Total download size: 158 k
Installed size: 398 k
Downloading Packages:
(1/2): tomcat- 427 kB/s |  77 kB     00:00    
(2/2): tomcat- 433 kB/s |  80 kB     00:00    
-----------------------------------------------
Total          367 kB/s | 158 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Installing       : tomcat-webapps-1:9.   1/2 
  Installing       : tomcat-admin-webapp   2/2 
  Verifying        : tomcat-admin-webapp   1/2 
  Verifying        : tomcat-webapps-1:9.   2/2 

Installed:
  tomcat-admin-webapps-1:9.0.87-6.el9.noarch   
  tomcat-webapps-1:9.0.87-6.el9.noarch         

Complete!
[tony@stapp01 ~]$ tomcat version
Server version: Apache Tomcat/9.0.87
Server built:   Dec 14 1969 11:59:35 UTC
Server number:  9.0.87.0
OS Name:        Linux
OS Version:     5.15.0-1083-gcp
Architecture:   amd64
JVM Version:    1.8.0_462-b08
JVM Vendor:     Red Hat, Inc.
[tony@stapp01 ~]$ sudo vi /usr/share/tomcat/conf/server.xml
[tony@stapp01 ~]$ sudo systemctl start tomcat
[tony@stapp01 ~]$ sudo systemctl status tomcat
● tomcat.service - Apache Tomcat Web Application Container
     Loaded: loaded (/usr/lib/systemd/system/tomcat.service; disabled; preset: disabled)
     Active: active (running) since Sun 2025-10-12 18:46:49 UTC; 6min ago
   Main PID: 2791 (java)
      Tasks: 50 (limit: 411434)
     Memory: 158.1M
     CGroup: /docker/60f60923273a51c7d933cef3b9c0f62e7680affd0bd38320165061522ee73931/system.slice/tomcat.service
             └─2791 /usr/lib/jvm/jre/bin/java -Djavax.sql.DataSource.Factory=org.apache.commons.dbcp.BasicDataSourceFactory -classpath /usr/share/tomcat/bin/bootstrap.jar:/usr/share/tomcat/bin/tomcat-juli.jar: -Dcatalina.base=/usr/share/tomcat -Dcatalina.home=/usr/share/tomcat -Djava.endorsed.dirs= -Djava.io.tmpdir=/var/cache/tomcat/temp -Djava.util.logging.config.file=/usr/share/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Dsun.io.useCanonCaches=false org.apache.catalina.startup.Bootstrap start

Oct 12 18:51:22 stapp01.stratos.xfusioncorp.com server[2791]: 12-Oct-2025 18:51:22.170 INFO [Catalina-utility-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/manager]
Oct 12 18:51:22 stapp01.stratos.xfusioncorp.com server[2791]: 12-Oct-2025 18:51:22.564 INFO [Catalina-utility-1] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 18:51:22 stapp01.stratos.xfusioncorp.com server[2791]: 12-Oct-2025 18:51:22.569 INFO [Catalina-utility-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/manager] has finished in [399] ms
Oct 12 18:51:22 stapp01.stratos.xfusioncorp.com server[2791]: 12-Oct-2025 18:51:22.569 INFO [Catalina-utility-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/host-manager]
Oct 12 18:51:22 stapp01.stratos.xfusioncorp.com server[2791]: 12-Oct-2025 18:51:22.853 INFO [Catalina-utility-1] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 18:51:22 stapp01.stratos.xfusioncorp.com server[2791]: 12-Oct-2025 18:51:22.854 INFO [Catalina-utility-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/host-manager] has finished in [285] ms
Oct 12 18:52:46 stapp01.stratos.xfusioncorp.com systemd[1]: tomcat.service: Trying to enqueue job tomcat.service/start/replace
Oct 12 18:52:46 stapp01.stratos.xfusioncorp.com systemd[1]: tomcat.service: Installed new job tomcat.service/start as 497
Oct 12 18:52:46 stapp01.stratos.xfusioncorp.com systemd[1]: tomcat.service: Enqueued job tomcat.service/start as 497
Oct 12 18:52:46 stapp01.stratos.xfusioncorp.com systemd[1]: tomcat.service: Job 497 tomcat.service/start finished, result=done
[tony@stapp01 ~]$ sudo systemctl enable tomcat
Created symlink /etc/systemd/system/multi-user.target.wants/tomcat.service → /usr/lib/systemd/system/tomcat.service.
[tony@stapp01 ~]$ scp /tmp/ROOT.war tony@stapp01:/usr/share/tomcat/webapps/
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:Id/D8/2OPZY5LSo7SBbs83jdjSnySFoHpVjNctern7w.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
stat local "/tmp/ROOT.war": No such file or directory
[tony@stapp01 ~]$ ssh tony@stapp01
tony@stapp01's password: 
Last login: Sun Oct 12 18:50:51 2025 from 172.16.238.3
[tony@stapp01 ~]$ ls -l /usr/share/tomcat/webapps/
total 12
drwxr-xr-x 3 tomcat tomcat 4096 Oct 12 18:51 ROOT
drwxr-xr-x 6 root   tomcat 4096 Oct 12 18:51 host-manager
drwxr-xr-x 6 root   tomcat 4096 Oct 12 18:51 manager
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo rm -rf /usr/share/tomcat/webapps/ROOT
[sudo] password for tony: 
[tony@stapp01 ~]$ sudo cp /tmp/ROOT.war /usr/share/tomcat/webapps/
cp: cannot stat '/tmp/ROOT.war': No such file or directory
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ scp /tmp/ROOT.war tony@stapp01:/tmp/
tony@stapp01's password: 
Permission denied, please try again.
tony@stapp01's password: 
Permission denied, please try again.
tony@stapp01's password: 
stat local "/tmp/ROOT.war": No such file or directory
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ exit
logout
Connection to stapp01 closed.
[tony@stapp01 ~]$ exitt
-bash: exitt: command not found
[tony@stapp01 ~]$ exit
logout
Connection to stapp01 closed.
thor@jumphost ~$ scp /tmp/ROOT.war tony@stapp01:/tmp/
tony@stapp01's password: 
ROOT.war     100% 4529     7.2MB/s   00:00    
thor@jumphost ~$ ssh tony@stapp01
tony@stapp01's password: 
Last failed login: Sun Oct 12 18:57:35 UTC 2025 from 172.16.238.10 on ssh:notty
There were 2 failed login attempts since the last successful login.
Last login: Sun Oct 12 18:55:06 2025 from 172.16.238.10
[tony@stapp01 ~]$ ls -l /tmp/
total 32
-rw-r--r-- 1 tony   tony   4529 Oct 12 18:59 ROOT.war
drwxr-xr-x 2 root   root   4096 Oct 12 18:41 hsperfdata_root
drwxr-xr-x 2 tomcat tomcat 4096 Oct 12 18:46 hsperfdata_tomcat
drwxr-xr-x 2 tony   tony   4096 Oct 12 18:51 hsperfdata_tony
drwx------ 3 root   root   4096 Oct 12 18:32 systemd-private-1cfc9a0df6b146b88f830562b7948054-dbus-broker.service-O0rzbU
drwx------ 3 root   root   4096 Oct 12 18:59 systemd-private-1cfc9a0df6b146b88f830562b7948054-systemd-hostnamed.service-TGbcbs
drwx------ 3 root   root   4096 Oct 12 18:32 systemd-private-1cfc9a0df6b146b88f830562b7948054-systemd-logind.service-NOZD4U
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo cp /tmp/ROOT.war /usr/share/tomcat/webapps/
[sudo] password for tony: 
sudo: timed out reading password
sudo: a password is required
[tony@stapp01 ~]$ sudo cp /tmp/ROOT.war /usr/share/tomcat/webapps/
[sudo] password for tony: 
[tony@stapp01 ~]$ sudo systemctl restart tomcat 
[tony@stapp01 ~]$ sudo systemctl status tomcat
● tomcat.service - Apache Tomcat Web Application Container
     Loaded: loaded (/usr/lib/systemd/system/tomcat.service; enabled; preset: disabled)
     Active: active (running) since Sun 2025-10-12 19:05:45 UTC; 7s ago
   Main PID: 4661 (java)
      Tasks: 50 (limit: 411434)
     Memory: 224.8M
     CGroup: /docker/60f60923273a51c7d933cef3b9c0f62e7680affd0bd38320165061522ee73931/system.slice/tomcat.service
             └─4661 /usr/lib/jvm/jre/bin/java -Djavax.sql.DataSource.Factory=org.apache.commons.dbcp.BasicDataSourceFactory -classpath /usr/share/tomcat/bin/bootstrap.jar:/usr/share/tomcat/bin/tomcat-juli.jar: -Dcatalina.base=/usr/share/tomcat -Dcatalina.home=/usr/share/tomcat -Djava.endorsed.dirs= -Djava.io.tmpdir=/var/cache/tomcat/temp -Djava.util.logging.config.file=/usr/share/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Dsun.io.useCanonCaches=false org.apache.catalina.startup.Bootstrap start

Oct 12 19:05:48 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:48.946 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.054 INFO [main] org.apache.catalina.startup.HostConfig.deployWAR Deployment of web application archive [/var/lib/tomcat/webapps/ROOT.war] has finished in [1,198] ms
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.055 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/manager]
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.465 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.469 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/manager] has finished in [415] ms
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.469 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/host-manager]
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.745 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.746 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/host-manager] has finished in [277] ms
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.749 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"]
Oct 12 19:05:49 stapp01.stratos.xfusioncorp.com server[4661]: 12-Oct-2025 19:05:49.757 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in [2004] milliseconds
[tony@stapp01 ~]$ curl http://localhost:3000
curl: (7) Failed to connect to localhost port 3000: Connection refused
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo vi /usr/share/tomcat/conf/server.xml
[tony@stapp01 ~]$ sudo systemctl restart tomcat 
[tony@stapp01 ~]$ sudo systemctl status tomcat
● tomcat.service - Apache Tomcat Web Application Container
     Loaded: loaded (/usr/lib/systemd/system/tomcat.service; enabled; preset: disabled)
     Active: active (running) since Sun 2025-10-12 19:08:11 UTC; 6s ago
   Main PID: 4868 (java)
      Tasks: 50 (limit: 411434)
     Memory: 189.7M
     CGroup: /docker/60f60923273a51c7d933cef3b9c0f62e7680affd0bd38320165061522ee73931/system.slice/tomcat.service
             └─4868 /usr/lib/jvm/jre/bin/java -Djavax.sql.DataSource.Factory=org.apache.commons.dbcp.BasicDataSourceFactory -classpath /usr/share/tomcat/bin/bootstrap.jar:/usr/share/tomcat/bin/tomcat-juli.jar: -Dcatalina.base=/usr/share/tomcat -Dcatalina.home=/usr/share/tomcat -Djava.endorsed.dirs= -Djava.io.tmpdir=/var/cache/tomcat/temp -Djava.util.logging.config.file=/usr/share/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Dsun.io.useCanonCaches=false org.apache.catalina.startup.Bootstrap start

Oct 12 19:08:14 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:14.942 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:08:14 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:14.966 INFO [main] org.apache.catalina.startup.HostConfig.deployWAR Deployment of web application archive [/var/lib/tomcat/webapps/ROOT.war] has finished in [1,507] ms
Oct 12 19:08:14 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:14.967 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/manager]
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.470 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.475 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/manager] has finished in [508] ms
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.475 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/host-manager]
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.755 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.757 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/host-manager] has finished in [282] ms
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.760 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"]
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.769 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in [2427] milliseconds
[tony@stapp01 ~]$ curl http://localhost:3000
curl: (7) Failed to connect to localhost port 3000: Connection refused
[tony@stapp01 ~]$ sudo systemctl status tomcat
● tomcat.service - Apache Tomcat Web Application Container
     Loaded: loaded (/usr/lib/systemd/system/tomcat.service; enabled; preset: disabled)
     Active: active (running) since Sun 2025-10-12 19:08:11 UTC; 1min 5s ago
   Main PID: 4868 (java)
      Tasks: 50 (limit: 411434)
     Memory: 184.7M
     CGroup: /docker/60f60923273a51c7d933cef3b9c0f62e7680affd0bd38320165061522ee73931/system.slice/tomcat.service
             └─4868 /usr/lib/jvm/jre/bin/java -Djavax.sql.DataSource.Factory=org.apache.commons.dbcp.BasicDataSourceFactory -classpath /usr/share/tomcat/bin/bootstrap.jar:/usr/share/tomcat/bin/tomcat-juli.jar: -Dcatalina.base=/usr/share/tomcat -Dcatalina.home=/usr/share/tomcat -Djava.endorsed.dirs= -Djava.io.tmpdir=/var/cache/tomcat/temp -Djava.util.logging.config.file=/usr/share/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Dsun.io.useCanonCaches=false org.apache.catalina.startup.Bootstrap start

Oct 12 19:08:14 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:14.942 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:08:14 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:14.966 INFO [main] org.apache.catalina.startup.HostConfig.deployWAR Deployment of web application archive [/var/lib/tomcat/webapps/ROOT.war] has finished in [1,507] ms
Oct 12 19:08:14 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:14.967 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/manager]
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.470 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.475 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/manager] has finished in [508] ms
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.475 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/host-manager]
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.755 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.757 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/host-manager] has finished in [282] ms
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.760 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"]
Oct 12 19:08:15 stapp01.stratos.xfusioncorp.com server[4868]: 12-Oct-2025 19:08:15.769 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in [2427] milliseconds
[tony@stapp01 ~]$ sudo systemctl start tomcat
[tony@stapp01 ~]$ sudo netstat -tulnp | grep java
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      4868/java           
tcp        0      0 127.0.0.1:8005          0.0.0.0:*               LISTEN      4868/java           
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo vi /usr/share/tomcat/conf/server.xml
[tony@stapp01 ~]$ sudo systemctl restart tomcat 
[tony@stapp01 ~]$ sudo netstat -tulnp | grep java
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN      5165/java           
tcp        0      0 127.0.0.1:8005          0.0.0.0:*               LISTEN      5165/java           
[tony@stapp01 ~]$ curl http://localhost:3000
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>SampleWebApp</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <h2>Welcome to xFusionCorp Industries!</h2>
        <br>
    
    </body>
</html>
[tony@stapp01 ~]$ sudo systemctl status tomcat
● tomcat.service - Apache Tomcat Web Application Container
     Loaded: loaded (/usr/lib/systemd/system/tomcat.service; enabled; preset: disabled)
     Active: active (running) since Sun 2025-10-12 19:11:31 UTC; 1min 2s ago
   Main PID: 5165 (java)
      Tasks: 50 (limit: 411434)
     Memory: 215.7M
     CGroup: /docker/60f60923273a51c7d933cef3b9c0f62e7680affd0bd38320165061522ee73931/system.slice/tomcat.service
             └─5165 /usr/lib/jvm/jre/bin/java -Djavax.sql.DataSource.Factory=org.apache.commons.dbcp.BasicDataSourceFactory -classpath /usr/share/tomcat/bin/bootstrap.jar:/usr/share/tomcat/bin/tomcat-juli.jar: -Dcatalina.base=/usr/share/tomcat -Dcatalina.home=/usr/share/tomcat -Djava.endorsed.dirs= -Djava.io.tmpdir=/var/cache/tomcat/temp -Djava.util.logging.config.file=/usr/share/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Dsun.io.useCanonCaches=false org.apache.catalina.startup.Bootstrap start

Oct 12 19:11:34 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:34.456 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:11:34 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:34.562 INFO [main] org.apache.catalina.startup.HostConfig.deployWAR Deployment of web application archive [/var/lib/tomcat/webapps/ROOT.war] has finished in [1,279] ms
Oct 12 19:11:34 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:34.562 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/manager]
Oct 12 19:11:34 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:34.972 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.041 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/manager] has finished in [479] ms
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.042 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/host-manager]
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.351 INFO [main] org.apache.jasper.servlet.TldScanner.scanJars At least one JAR was scanned for TLDs yet contained no TLDs. Enable debug logging for this logger for a complete list of JARs that were scanned but no TLDs were found in them. Skipping unneeded JARs during scanning can improve startup time and JSP compilation time.
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.353 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/host-manager] has finished in [312] ms
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.356 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-3000"]
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.366 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in [2207] milliseconds
[tony@stapp01 ~]$ ls -l /usr/share/tomcat/webapps/
total 20
drwxr-xr-x 4 tomcat tomcat 4096 Oct 12 19:05 ROOT
-rw-r--r-- 1 root   root   4529 Oct 12 19:05 ROOT.war
drwxr-xr-x 6 root   tomcat 4096 Oct 12 18:51 host-manager
drwxr-xr-x 6 root   tomcat 4096 Oct 12 18:51 manager
[tony@stapp01 ~]$ curl http://localhost:3000
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>SampleWebApp</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <h2>Welcome to xFusionCorp Industries!</h2>
        <br>
    
    </body>
</html>
[tony@stapp01 ~]$ sudo tail -n 20 /usr/share/tomcat/logs/catalina.out
tail: cannot open '/usr/share/tomcat/logs/catalina.out' for reading: No such file or directory
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo find / -type d -name "logs" 2>/dev/null | grep tomcat
[tony@stapp01 ~]$ sudo tail -n 20 /path/to/that/logs/catalina.out
tail: cannot open '/path/to/that/logs/catalina.out' for reading: No such file or directory
[tony@stapp01 ~]$ sudo tail -n 20 /var/log/tomcat/catalina.out
tail: cannot open '/var/log/tomcat/catalina.out' for reading: No such file or directory
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo systemctl cat tomcat | grep CATALINA_BASE
[tony@stapp01 ~]$ sudo systemctl status tomcat | grep -i catalina
             └─5165 /usr/lib/jvm/jre/bin/java -Djavax.sql.DataSource.Factory=org.apache.commons.dbcp.BasicDataSourceFactory -classpath /usr/share/tomcat/bin/bootstrap.jar:/usr/share/tomcat/bin/tomcat-juli.jar: -Dcatalina.base=/usr/share/tomcat -Dcatalina.home=/usr/share/tomcat -Djava.endorsed.dirs= -Djava.io.tmpdir=/var/cache/tomcat/temp -Djava.util.logging.config.file=/usr/share/tomcat/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Dsun.io.useCanonCaches=false org.apache.catalina.startup.Bootstrap start
Oct 12 19:11:34 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:34.562 INFO [main] org.apache.catalina.startup.HostConfig.deployWAR Deployment of web application archive [/var/lib/tomcat/webapps/ROOT.war] has finished in [1,279] ms
Oct 12 19:11:34 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:34.562 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/manager]
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.041 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/manager] has finished in [479] ms
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.042 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory [/var/lib/tomcat/webapps/host-manager]
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.353 INFO [main] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory [/var/lib/tomcat/webapps/host-manager] has finished in [312] ms
Oct 12 19:11:35 stapp01.stratos.xfusioncorp.com server[5165]: 12-Oct-2025 19:11:35.366 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in [2207] milliseconds
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ 