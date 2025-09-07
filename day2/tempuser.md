thor@jumphost ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:LrYKS3bDF7KuYFKddb636UadVmmzp4ar0cmxAh8g+eI.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
Connection closed by 172.16.238.10 port 22
thor@jumphost ~$ sudo useradd -e 2024-02-17 james

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for thor: 
Sorry, try again.
[sudo] password for thor: 
Sorry, try again.
[sudo] password for thor: 
sudo: 2 incorrect password attempts
thor@jumphost ~$ ssh tony@stapp01
tony@stapp01's password: 
[tony@stapp01 ~]$ sudo useradd -e 2024-02-17 james

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[tony@stapp01 ~]$ sudo chage -l james
Last password change                                    : Sep 07, 2025
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : Feb 17, 2024
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ 