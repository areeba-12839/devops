thor@jumphost ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:kVmUhvUfGbME6YAYsdO3EHHucz4YUbyBQw1zLcTrnTI.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
[tony@stapp01 ~]$ sudo yum install -y iptables iptables-services

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
CentOS Stream   30 kB/s | 6.7 kB     00:00    
CentOS Stream   11 MB/s | 8.8 MB     00:00    
CentOS Stream   30 kB/s | 6.8 kB     00:00    
CentOS Stream   37 MB/s |  26 MB     00:00    
CentOS Stream   31 kB/s | 7.3 kB     00:00    
CentOS Stream   22 kB/s |  20 kB     00:00    
Docker CE Stab  37 kB/s | 2.0 kB     00:00    
Docker CE Stab 455 kB/s |  65 kB     00:00    
Extra Packages  43 kB/s | 9.7 kB     00:00    
Extra Packages  24 MB/s |  20 MB     00:00    
Extra Packages 4.2 kB/s | 993  B     00:00    
Extra Packages  95 kB/s |  22 kB     00:00    
Extra Packages 283 kB/s | 259 kB     00:00    
Package iptables-legacy-1.8.10-11.1.el9.x86_64 is already installed.
Dependencies resolved.
===============================================
 Package     Arch   Version         Repo  Size
===============================================
Installing:
 iptables-services
             noarch 1.8.10-11.1.el9 epel  17 k

Transaction Summary
===============================================
Install  1 Package

Total download size: 17 k
Installed size: 27 k
Downloading Packages:
iptables-servi  79 kB/s |  17 kB     00:00    
-----------------------------------------------
Total           37 kB/s |  17 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Installing       : iptables-services-1   1/1 
  Running scriptlet: iptables-services-1   1/1 
  Verifying        : iptables-services-1   1/1 

Installed:
  iptables-services-1.8.10-11.1.el9.noarch     

Complete!
[tony@stapp01 ~]$ sudo systemctl start iptables[tony@stapp01 ~]$ sudo systemctl enable iptables
Created symlink /etc/systemd/system/multi-user.target.wants/iptables.service → /usr/lib/systemd/system/iptables.service.
[tony@stapp01 ~]$ getent hosts stlb01
172.16.238.14   stlb01
[tony@stapp01 ~]$ sudo iptables -F
[tony@stapp01 ~]$ sudo iptables -I INPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT
[tony@stapp01 ~]$ sudo iptables -I INPUT 2 -p tcp --dport 22 -j ACCEPT
[tony@stapp01 ~]$ sudo iptables -I INPUT 3 -p tcp -s 172.16.238.14 --dport 8086 -j ACCEPT
[tony@stapp01 ~]$ sudo iptables -A INPUT -p tcp --dport 8086 -j DROP
[tony@stapp01 ~]$ sudo iptables -A INPUT -i lo -j ACCEPT
[tony@stapp01 ~]$ sudo iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited
[tony@stapp01 ~]$ sudo iptables -L -n --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
5    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
6    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo iptables -D INPUT 5
[tony@stapp01 ~]$ sudo iptables -L -n --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
5    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
[tony@stapp01 ~]$ sudo service iptables save
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]
[tony@stapp01 ~]$ ssh steve@stapp02
The authenticity of host 'stapp02 (172.16.238.11)' can't be established.
ED25519 key fingerprint is SHA256:Or67RH/VPADSFAtjoJmNCC0MKVPFqvgg27TtYjup5+4.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp02' (ED25519) to the list of known hosts.
steve@stapp02's password: 
[steve@stapp02 ~]$ sudo yum install -y iptables iptables-services

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve: 
CentOS Stream   25 kB/s | 6.7 kB     00:00    
CentOS Stream  6.3 MB/s | 8.8 MB     00:01    
CentOS Stream   40 kB/s | 6.8 kB     00:00    
CentOS Stream  3.5 MB/s |  26 MB     00:07    
CentOS Stream   40 kB/s | 7.3 kB     00:00    
CentOS Stream   54 kB/s |  20 kB     00:00    
Docker CE Stab  16 kB/s | 2.0 kB     00:00    
Docker CE Stab 369 kB/s |  65 kB     00:00    
Extra Packages  53 kB/s | 9.7 kB     00:00    
Extra Packages  26 MB/s |  20 MB     00:00    
Extra Packages 6.6 kB/s | 993  B     00:00    
Extra Packages 134 kB/s |  22 kB     00:00    
Extra Packages 354 kB/s | 259 kB     00:00    
Package iptables-legacy-1.8.10-11.1.el9.x86_64 is already installed.
Dependencies resolved.
===============================================
 Package     Arch   Version         Repo  Size
===============================================
Installing:
 iptables-services
             noarch 1.8.10-11.1.el9 epel  17 k

Transaction Summary
===============================================
Install  1 Package

Total download size: 17 k
Installed size: 27 k
Downloading Packages:
iptables-servi  85 kB/s |  17 kB     00:00    
-----------------------------------------------
Total           39 kB/s |  17 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Installing       : iptables-services-1   1/1 
  Running scriptlet: iptables-services-1   1/1 
  Verifying        : iptables-services-1   1/1 

Installed:
  iptables-services-1.8.10-11.1.el9.noarch     

Complete!
[steve@stapp02 ~]$ sudo systemctl start iptables
[steve@stapp02 ~]$ sudo systemctl enable iptables
Created symlink /etc/systemd/system/multi-user.target.wants/iptables.service → /usr/lib/systemd/system/iptables.service.
[steve@stapp02 ~]$ getent hosts stlb01
172.16.238.14   stlb01
[steve@stapp02 ~]$ sudo iptables -F
[steve@stapp02 ~]$ sudo iptables -I INPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT
[steve@stapp02 ~]$ sudo iptables -I INPUT 2 -p tcp --dport 22 -j ACCEPT
[steve@stapp02 ~]$ sudo iptables -I INPUT 3 -p tcp -s 172.16.238.14 --dport 8086 -j ACCEPT
[steve@stapp02 ~]$ sudo iptables -A INPUT -p tcp --dport 8086 -j DROP
[steve@stapp02 ~]$ sudo iptables -A INPUT -i lo -j ACCEPT
[steve@stapp02 ~]$ sudo iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited
[steve@stapp02 ~]$ sudo iptables -L -n --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
5    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
6    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
[steve@stapp02 ~]$ sudo service iptables save
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]
[steve@stapp02 ~]$ ssh banner@stapp03
The authenticity of host 'stapp03 (172.16.238.12)' can't be established.
ED25519 key fingerprint is SHA256:evpf772UmzN4gHKgBBvcz+1eqL2ZlHHvrKh4DNTBMQc.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp03' (ED25519) to the list of known hosts.
banner@stapp03's password: 
[banner@stapp03 ~]$ sudo yum install -y iptables iptables-services

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for banner: 
CentOS Stream   26 kB/s | 6.7 kB     00:00    
CentOS Stream   11 MB/s | 8.8 MB     00:00    
CentOS Stream   34 kB/s | 6.8 kB     00:00    
CentOS Stream   29 MB/s |  26 MB     00:00    
CentOS Stream   23 kB/s | 7.3 kB     00:00    
CentOS Stream   55 kB/s |  20 kB     00:00    
Docker CE Stab  24 kB/s | 2.0 kB     00:00    
Docker CE Stab 323 kB/s |  65 kB     00:00    
Extra Packages  40 kB/s | 9.7 kB     00:00    
Extra Packages  16 MB/s |  20 MB     00:01    
Extra Packages 4.4 kB/s | 993  B     00:00    
Extra Packages  71 kB/s |  22 kB     00:00    
Extra Packages 501 kB/s | 259 kB     00:00    
Package iptables-legacy-1.8.10-11.1.el9.x86_64 is already installed.
Dependencies resolved.
===============================================
 Package     Arch   Version         Repo  Size
===============================================
Installing:
 iptables-services
             noarch 1.8.10-11.1.el9 epel  17 k

Transaction Summary
===============================================
Install  1 Package

Total download size: 17 k
Installed size: 27 k
Downloading Packages:
iptables-servi  82 kB/s |  17 kB     00:00    
-----------------------------------------------
Total           43 kB/s |  17 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Installing       : iptables-services-1   1/1 
  Running scriptlet: iptables-services-1   1/1 
  Verifying        : iptables-services-1   1/1 

Installed:
  iptables-services-1.8.10-11.1.el9.noarch     

Complete!
[banner@stapp03 ~]$ sudo systemctl start iptables
[banner@stapp03 ~]$ sudo systemctl enable iptables
Created symlink /etc/systemd/system/multi-user.target.wants/iptables.service → /usr/lib/systemd/system/iptables.service.
[banner@stapp03 ~]$ getent hosts stlb01
172.16.238.14   stlb01
[banner@stapp03 ~]$ sudo iptables -F
[banner@stapp03 ~]$ sudo iptables -I INPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT
[banner@stapp03 ~]$ sudo iptables -I INPUT 2 -p tcp --dport 22 -j ACCEPT
[banner@stapp03 ~]$ sudo iptables -I INPUT 2 -p tcp --dport 22 -j ACCEPT
[banner@stapp03 ~]$ sudo iptables -I INPUT 3 -p tcp -s 172.16.238.14 --dport 8086 -j ACCEPT
[banner@stapp03 ~]$ sudo iptables -A INPUT -p tcp --dport 8086 -j DROP
[banner@stapp03 ~]$ sudo iptables -A INPUT -i lo -j ACCEPT
[banner@stapp03 ~]$ sudo iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited
[banner@stapp03 ~]$ sudo iptables -L -n --line-numbers
sudo iptables -L -n --line-numbers
sudo iptables -L -n --line-numbers
sudo iptables -L -n --line-numbers
sudo iptables -L -n --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
5    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
6    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
7    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
5    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
6    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
7    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
5    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
6    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
7    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
5    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
6    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
7    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
5    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
6    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
7    REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
[banner@stapp03 ~]$ sudo service iptables save
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]
[banner@stapp03 ~]$ ^C
[banner@stapp03 ~]$ sudo iptables -D INPUT 4
[banner@stapp03 ~]$ sudo iptables -D INPUT 6
[banner@stapp03 ~]$ sudo iptables -L -n --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
3    ACCEPT     tcp  --  172.16.238.14        0.0.0.0/0            tcp dpt:8086
4    DROP       tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8086
5    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         
[banner@stapp03 ~]$ sudo service iptables save
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]
[banner@stapp03 ~]$ ssh steve@stapp02
The authenticity of host 'stapp02 (172.16.238.11)' can't be established.
ED25519 key fingerprint is SHA256:Or67RH/VPADSFAtjoJmNCC0MKVPFqvgg27TtYjup5+4.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes 
Warning: Permanently added 'stapp02' (ED25519) to the list of known hosts.
steve@stapp02's password: 
Last login: Wed Dec 31 14:03:20 2025 from 172.16.238.10
[steve@stapp02 ~]$ sudo iptables -D INPUT 5
[sudo] password for steve: 
Sorry, try again.
[sudo] password for steve: 
[steve@stapp02 ~]$ sudo service iptables save
iptables: Saving firewall rules to /etc/sysconfig/iptables: [  OK  ]
[steve@stapp02 ~]$ ^C
[steve@stapp02 ~]$ ^C
[steve@stapp02 ~]$ ^C
[steve@stapp02 ~]$ ^C
[steve@stapp02 ~]$ 