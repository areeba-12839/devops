thor@jumphost ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:jaagAPTwIRpuaR/MMvNEWvqmOXV1mtVCp2ZAI/VU3Ig.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
[tony@stapp01 ~]$ sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
CentOS Stream 9 - BaseOS                                  48 kB/s | 7.3 kB     00:00    
CentOS Stream 9 - BaseOS                                  18 MB/s | 8.8 MB     00:00    
CentOS Stream 9 - AppStream                               39 kB/s | 7.5 kB     00:00    
CentOS Stream 9 - AppStream                              1.9 MB/s |  25 MB     00:13    
CentOS Stream 9 - Extras packages                         30 kB/s | 8.0 kB     00:00    
CentOS Stream 9 - Extras packages                         22 kB/s |  19 kB     00:00    
Extra Packages for Enterprise Linux 9 - x86_64           179 kB/s |  34 kB     00:00    
Extra Packages for Enterprise Linux 9 - x86_64            16 MB/s |  20 MB     00:01    
Extra Packages for Enterprise Linux 9 openh264 (From Cis 4.6 kB/s | 993  B     00:00    
Extra Packages for Enterprise Linux 9 - Next - x86_64    120 kB/s |  24 kB     00:00    
Dependencies resolved.
=========================================================================================
 Package                        Architecture  Version                Repository     Size
=========================================================================================
Installing:
 policycoreutils                x86_64        3.6-3.el9              baseos        239 k
 selinux-policy                 noarch        38.1.65-1.el9          baseos         42 k
 selinux-policy-targeted        noarch        38.1.65-1.el9          baseos        6.9 M
Installing dependencies:
 diffutils                      x86_64        3.7-12.el9             baseos        397 k
 libselinux-utils               x86_64        3.6-3.el9              baseos        190 k
 rpm-plugin-selinux             x86_64        4.16.1.3-38.el9        baseos         16 k

Transaction Summary
=========================================================================================
Install  6 Packages

Total download size: 7.8 M
Installed size: 21 M
Downloading Packages:
(1/6): libselinux-utils-3.6-3.el9.x86_64.rpm             648 kB/s | 190 kB     00:00    
(2/6): diffutils-3.7-12.el9.x86_64.rpm                   1.2 MB/s | 397 kB     00:00    
(3/6): selinux-policy-38.1.65-1.el9.noarch.rpm           821 kB/s |  42 kB     00:00    
(4/6): rpm-plugin-selinux-4.16.1.3-38.el9.x86_64.rpm     138 kB/s |  16 kB     00:00    
(5/6): policycoreutils-3.6-3.el9.x86_64.rpm              555 kB/s | 239 kB     00:00    
(6/6): selinux-policy-targeted-38.1.65-1.el9.noarch.rpm   22 MB/s | 6.9 MB     00:00    
-----------------------------------------------------------------------------------------
Total                                                    9.0 MB/s | 7.8 MB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Running scriptlet: selinux-policy-targeted-38.1.65-1.el9.noarch                    1/1 
  Preparing        :                                                                 1/1 
  Installing       : libselinux-utils-3.6-3.el9.x86_64                               1/6 
  Installing       : diffutils-3.7-12.el9.x86_64                                     2/6 
  Installing       : policycoreutils-3.6-3.el9.x86_64                                3/6 
  Running scriptlet: policycoreutils-3.6-3.el9.x86_64                                3/6 
Created symlink /etc/systemd/system/sysinit.target.wants/selinux-autorelabel-mark.service → /usr/lib/systemd/system/selinux-autorelabel-mark.service.

  Installing       : selinux-policy-38.1.65-1.el9.noarch                             4/6 
  Running scriptlet: selinux-policy-38.1.65-1.el9.noarch                             4/6 
  Running scriptlet: selinux-policy-targeted-38.1.65-1.el9.noarch                    5/6 
  Installing       : selinux-policy-targeted-38.1.65-1.el9.noarch                    5/6 
  Running scriptlet: selinux-policy-targeted-38.1.65-1.el9.noarch                    5/6 
  Installing       : rpm-plugin-selinux-4.16.1.3-38.el9.x86_64                       6/6 
  Running scriptlet: selinux-policy-targeted-38.1.65-1.el9.noarch                    6/6 
  Running scriptlet: rpm-plugin-selinux-4.16.1.3-38.el9.x86_64                       6/6 
  Verifying        : diffutils-3.7-12.el9.x86_64                                     1/6 
  Verifying        : libselinux-utils-3.6-3.el9.x86_64                               2/6 
  Verifying        : policycoreutils-3.6-3.el9.x86_64                                3/6 
  Verifying        : rpm-plugin-selinux-4.16.1.3-38.el9.x86_64                       4/6 
  Verifying        : selinux-policy-38.1.65-1.el9.noarch                             5/6 
  Verifying        : selinux-policy-targeted-38.1.65-1.el9.noarch                    6/6 

Installed:
  diffutils-3.7-12.el9.x86_64            libselinux-utils-3.6-3.el9.x86_64              
  policycoreutils-3.6-3.el9.x86_64       rpm-plugin-selinux-4.16.1.3-38.el9.x86_64      
  selinux-policy-38.1.65-1.el9.noarch    selinux-policy-targeted-38.1.65-1.el9.noarch   

Complete!
[tony@stapp01 ~]$ getenforce
Disabled
[tony@stapp01 ~]$ sudo vi /etc/selinux/config
[tony@stapp01 ~]$ cat /etc/selinux/config | grep SELINUX=
# SELINUX= can take one of these three values:
# NOTE: Up to RHEL 8 release included, SELINUX=disabled would also
SELINUX=disabled
[tony@stapp01 ~]$ 