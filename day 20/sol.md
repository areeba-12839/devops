thor@jumphost ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:urUctH4VUoRHBxisJQt6hm3zQ0knOk7XBDBjZsi5lk0.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
[tony@stapp01 ~]$ sudo -i

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[root@stapp01 ~]# dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm -y
CentOS Stream   31 kB/s | 6.7 kB     00:00    
CentOS Stream  7.2 MB/s | 8.8 MB     00:01    
CentOS Stream   36 kB/s | 6.8 kB     00:00    
CentOS Stream   35 MB/s |  26 MB     00:00    
CentOS Stream   31 kB/s | 7.3 kB     00:00    
CentOS Stream  2.7 kB/s |  20 kB     00:07    
Extra Packages 147 kB/s |  32 kB     00:00    
Extra Packages  30 MB/s |  20 MB     00:00    
Extra Packages 4.9 kB/s | 993  B     00:00    
Extra Packages  99 kB/s |  21 kB     00:00    
Extra Packages 389 kB/s | 259 kB     00:00    
epel-release-l  67 kB/s |  19 kB     00:00    
Dependencies resolved.
===============================================
 Package           Arch   Version  Repo   Size
===============================================
Upgrading:
 epel-next-release noarch 9-10.el9 epel  7.9 k
 epel-release      noarch 9-10.el9 @commandline
                                          19 k

Transaction Summary
===============================================
Upgrade  2 Packages

Total size: 26 k
Total download size: 7.9 k
Downloading Packages:
epel-next-rele  50 kB/s | 7.9 kB     00:00    
-----------------------------------------------
Total           19 kB/s | 7.9 kB     00:00     
Extra Packages 1.6 MB/s | 1.6 kB     00:00    
Importing GPG key 0x3228467C:
 Userid     : "Fedora (epel9) <epel@fedoraproject.org>"
 Fingerprint: FF8A D134 4597 106E CE81 3B91 8A38 72BF 3228 467C
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-9
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Upgrading        : epel-release-9-10.e   1/4 
  Running scriptlet: epel-release-9-10.e   1/4 
  Upgrading        : epel-next-release-9   2/4 
  Cleanup          : epel-next-release-9   3/4 
  Cleanup          : epel-release-9-7.el   4/4 
  Running scriptlet: epel-release-9-7.el   4/4 
  Verifying        : epel-next-release-9   1/4 
  Verifying        : epel-next-release-9   2/4 
  Verifying        : epel-release-9-10.e   3/4 
  Verifying        : epel-release-9-7.el   4/4 

Upgraded:
  epel-next-release-9-10.el9.noarch            
  epel-release-9-10.el9.noarch                 

Complete!
[root@stapp01 ~]# dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm -y
Last metadata expiration check: 0:00:16 ago on Fri Jan  9 18:57:39 2026.
remi-release-9  54 kB/s |  33 kB     00:00    
Dependencies resolved.
===============================================
 Package
      Arch   Version        Repository    Size
===============================================
Installing:
 remi-release
      noarch 9.7-4.el9.remi @commandline  33 k

Transaction Summary
===============================================
Install  1 Package

Total size: 33 k
Installed size: 35 k
Downloading Packages:
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Installing       : remi-release-9.7-4.   1/1 
  Verifying        : remi-release-9.7-4.   1/1 

Installed:
  remi-release-9.7-4.el9.remi.noarch           

Complete!
[root@stapp01 ~]# dnf module reset php -y
Remi's Modular 634 kB/s | 899 kB     00:01    
Safe Remi's RP 892 kB/s | 1.4 MB     00:01    
Last metadata expiration check: 0:00:01 ago on Fri Jan  9 18:58:37 2026.
Dependencies resolved.
Nothing to do.
Complete!
[root@stapp01 ~]# dnf module enable php:remi-8.2 -y
Last metadata expiration check: 0:00:40 ago on Fri Jan  9 18:58:37 2026.
Dependencies resolved.
===============================================
 Package   Arch     Version    Repo       Size
===============================================
Enabling module streams:
 php                remi-8.2                  

Transaction Summary
===============================================

Complete!
[root@stapp01 ~]# dnf install nginx php-fpm -y
Last metadata expiration check: 0:00:49 ago on Fri Jan  9 18:58:37 2026.
Dependencies resolved.
===============================================
 Package          Arch   Version
                            Repository    Size
===============================================
Installing:
 nginx            x86_64 2:1.20.1-26.el9
                            appstream     36 k
 php-fpm          x86_64 8.2.30-1.module_php.8.2.el9.remi
                            remi-modular 1.8 M
Installing dependencies:
 centos-logos-httpd
                  noarch 90.8-3.el9
                            appstream    1.5 M
 httpd-filesystem noarch 2.4.62-10.el9
                            appstream     12 k
 nginx-core       x86_64 2:1.20.1-26.el9
                            appstream    571 k
 nginx-filesystem noarch 2:1.20.1-26.el9
                            appstream    9.3 k
 php-common       x86_64 8.2.30-1.module_php.8.2.el9.remi
                            remi-modular 853 k

Transaction Summary
===============================================
Install  7 Packages

Total download size: 4.8 M
Installed size: 28 M
Downloading Packages:
(1/7): httpd-f 107 kB/s |  12 kB     00:00    
(2/7): nginx-1 249 kB/s |  36 kB     00:00    
(3/7): nginx-f 264 kB/s | 9.3 kB     00:00    
(4/7): nginx-c 3.2 MB/s | 571 kB     00:00    
(5/7): centos- 4.8 MB/s | 1.5 MB     00:00    
(6/7): php-com 886 kB/s | 853 kB     00:00    
(7/7): php-fpm 1.7 MB/s | 1.8 MB     00:01    
-----------------------------------------------
Total          2.5 MB/s | 4.8 MB     00:01     
Remi's Modular 3.0 MB/s | 3.1 kB     00:00    
Importing GPG key 0x478F8947:
 Userid     : "Remi's RPM repository (https://rpms.remirepo.net/) <remi@remirepo.net>"
 Fingerprint: B1AB F71E 14C9 D748 97E1 98A8 B195 27F1 478F 8947
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-remi.el9
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Running scriptlet: nginx-filesystem-2:   1/7 
  Installing       : nginx-filesystem-2:   1/7 
  Installing       : nginx-core-2:1.20.1   2/7 
  Running scriptlet: php-common-8.2.30-1   3/7 
  Installing       : php-common-8.2.30-1   3/7 
  Running scriptlet: httpd-filesystem-2.   4/7 
  Installing       : httpd-filesystem-2.   4/7 
  Installing       : centos-logos-httpd-   5/7 
  Installing       : nginx-2:1.20.1-26.e   6/7 
  Running scriptlet: nginx-2:1.20.1-26.e   6/7 
  Installing       : php-fpm-8.2.30-1.mo   7/7 
  Running scriptlet: php-fpm-8.2.30-1.mo   7/7 
  Verifying        : centos-logos-httpd-   1/7 
  Verifying        : httpd-filesystem-2.   2/7 
  Verifying        : nginx-2:1.20.1-26.e   3/7 
  Verifying        : nginx-core-2:1.20.1   4/7 
  Verifying        : nginx-filesystem-2:   5/7 
  Verifying        : php-common-8.2.30-1   6/7 
  Verifying        : php-fpm-8.2.30-1.mo   7/7 

Installed:
  centos-logos-httpd-90.8-3.el9.noarch         
  httpd-filesystem-2.4.62-10.el9.noarch        
  nginx-2:1.20.1-26.el9.x86_64                 
  nginx-core-2:1.20.1-26.el9.x86_64            
  nginx-filesystem-2:1.20.1-26.el9.noarch      
  php-common-8.2.30-1.module_php.8.2.el9.remi.x86_64
  php-fpm-8.2.30-1.module_php.8.2.el9.remi.x86_64

Complete!
[root@stapp01 ~]# vi /etc/php-fpm.d/www.conf
[root@stapp01 ~]# mkdir -p /var/run/php-fpm
[root@stapp01 ~]# chown nginx:nginx /var/run/php-fpm
[root@stapp01 ~]# vi /etc/nginx/conf.d/nautilus.conf
[root@stapp01 ~]# systemctl enable --now nginx
Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /usr/lib/systemd/system/nginx.service.
[root@stapp01 ~]# systemctl enable --now php-fpm
Created symlink /etc/systemd/system/multi-user.target.wants/php-fpm.service → /usr/lib/systemd/system/php-fpm.service.
[root@stapp01 ~]# systemctl status php-fpm
● php-fpm.service - The PHP FastCGI Process Manager
     Loaded: loaded (/usr/lib/systemd/system/php-fpm.service; enabled; preset: disabled)
     Active: active (running) since Fri 2026-01-09 19:06:17 UTC; 18s ago
   Main PID: 3551 (php-fpm)
     Status: "Processes active: 0, idle: 5, Requests: 0, slow: 0, Traffic: 0.00req/sec"
      Tasks: 6 (limit: 411434)
     Memory: 27.3M
     CGroup: /docker/9ddc5e8cf7f4a0eb1dadd6410a05e1ae22c32f4a610a40f733ed31ba5e472921/system.slice/php-fpm.service
             ├─3551 "php-fpm: master process (/etc/php-fpm.conf)"
             ├─3785 "php-fpm: pool www"
             ├─3786 "php-fpm: pool www"
             ├─3787 "php-fpm: pool www"
             ├─3788 "php-fpm: pool www"
             └─3789 "php-fpm: pool www"

Jan 09 19:06:17 stapp01.stratos.xfusioncorp.com systemd[1]: Started The PHP FastCGI Process Manager.
Jan 09 19:06:26 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Changed dead -> running
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Failed to reset devices.allow/devices.deny: Operation not permitted
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Failed to set 'trusted.invocation_id' xattr on control group /docker/9ddc5e8cf7f4a0eb1dadd6410a05e1ae22c32f4a610a40f733ed31ba5e472921/system.slice/php-fpm.service, ignoring: Operation not permitted
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Failed to remove 'trusted.delegate' xattr flag on control group /docker/9ddc5e8cf7f4a0eb1dadd6410a05e1ae22c32f4a610a40f733ed31ba5e472921/system.slice/php-fpm.service, ignoring: Operation not permitted
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Trying to enqueue job php-fpm.service/start/replace
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Installed new job php-fpm.service/start as 280
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Enqueued job php-fpm.service/start as 280
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Job 280 php-fpm.service/start finished, result=done
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: php-fpm.service: Got notification message from PID 3551 (READY=1, STATUS=Processes active: 0, idle: 5, Requests: 0, slow: 0, Traffic: 0.00req/sec)
[root@stapp01 ~]# systemctl status nginx
● nginx.service - The nginx HTTP and reverse proxy server
     Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: disabled)
    Drop-In: /etc/systemd/system/nginx.service.d
             └─php-fpm.conf
     Active: active (running) since Fri 2026-01-09 19:06:17 UTC; 26s ago
   Main PID: 3572 (nginx)
      Tasks: 17 (limit: 411434)
     Memory: 18.9M
     CGroup: /docker/9ddc5e8cf7f4a0eb1dadd6410a05e1ae22c32f4a610a40f733ed31ba5e472921/system.slice/nginx.service
             ├─3572 "nginx: master process /usr/sbin/nginx"
             ├─3573 "nginx: worker process"
             ├─3574 "nginx: worker process"
             ├─3575 "nginx: worker process"
             ├─3576 "nginx: worker process"
             ├─3577 "nginx: worker process"
             ├─3578 "nginx: worker process"
             ├─3579 "nginx: worker process"
             ├─3580 "nginx: worker process"
             ├─3581 "nginx: worker process"
             ├─3582 "nginx: worker process"
             ├─3583 "nginx: worker process"
             ├─3584 "nginx: worker process"
             ├─3585 "nginx: worker process"
             ├─3586 "nginx: worker process"
             ├─3587 "nginx: worker process"
             └─3588 "nginx: worker process"

Jan 09 19:06:17 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: New main PID 3572 belongs to service, we are happy.
Jan 09 19:06:17 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Main PID loaded: 3572
Jan 09 19:06:17 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Changed start -> running
Jan 09 19:06:17 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Job 239 nginx.service/start finished, result=done
Jan 09 19:06:17 stapp01.stratos.xfusioncorp.com systemd[1]: Started The nginx HTTP and reverse proxy server.
Jan 09 19:06:17 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Failed to send unit change signal for nginx.service: Connection reset by peer
Jan 09 19:06:26 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Changed dead -> running
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Failed to reset devices.allow/devices.deny: Operation not permitted
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Failed to set 'trusted.invocation_id' xattr on control group /docker/9ddc5e8cf7f4a0eb1dadd6410a05e1ae22c32f4a610a40f733ed31ba5e472921/system.slice/nginx.service, ignoring: Operation not permitted
Jan 09 19:06:27 stapp01.stratos.xfusioncorp.com systemd[1]: nginx.service: Failed to remove 'trusted.delegate' xattr flag on control group /docker/9ddc5e8cf7f4a0eb1dadd6410a05e1ae22c32f4a610a40f733ed31ba5e472921/system.slice/nginx.service, ignoring: Operation not permitted
[root@stapp01 ~]# exit
logout
[tony@stapp01 ~]$ exit
logout
Connection to stapp01 closed.
thor@jumphost ~$ curl http://stapp01:8092/index.php
Welcome to xFusionCorp Industries!thor@jumphost ~$ ^C
thor@jumphost ~$ 