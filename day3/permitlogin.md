thor@jumphost ~$ ssh tony@stapp01  
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:uq80T9I8ugcGQAhznbHWrn66RphyfjX7ltfwK3SfvEI.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
[tony@stapp01 ~]$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak.$(date +%F)

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[tony@stapp01 ~]$ sudo vi /etc/ssh/sshd_config
[tony@stapp01 ~]$ sudo systemctl restart sshd
[sudo] password for tony: 
[tony@stapp01 ~]$ sudo sshd -T | grep permitrootlogin
permitrootlogin no
[tony@stapp01 ~]$ sudo systemctl restart sshd
[tony@stapp01 ~]$ ssh steve@stapp02 
The authenticity of host 'stapp02 (172.16.238.11)' can't be established.
ED25519 key fingerprint is SHA256:zfeJ+iF2/fjDVZU9B/UCU4lJJ8frHwOu7RBBPTuVoRQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp02' (ED25519) to the list of known hosts.
steve@stapp02's password: 
[steve@stapp02 ~]$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak.$(date +%F)

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve: 
[steve@stapp02 ~]$ sudo vi /etc/ssh/sshd_config
[steve@stapp02 ~]$ sudo systemctl restart sshd
[steve@stapp02 ~]$ sudo sshd -T | grep permitrootlogin
permitrootlogin no
[steve@stapp02 ~]$ sudo systemctl restart sshd
[steve@stapp02 ~]$ ssh banner@stapp03
The authenticity of host 'stapp03 (172.16.238.12)' can't be established.
ED25519 key fingerprint is SHA256:WkU1mDllnyvFeiJ58x1jQkH2CWrBg40LtLdkcWkm7IE.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp03' (ED25519) to the list of known hosts.
banner@stapp03's password: 
Permission denied, please try again.
banner@stapp03's password: 
Permission denied, please try again.
banner@stapp03's password: 
banner@stapp03: Permission denied (publickey,gssapi-keyex,gssapi-with-mic,password).
[steve@stapp02 ~]$ ssh banner@stapp03
banner@stapp03's password: 
Last failed login: Mon Sep  8 09:32:27 UTC 2025 from 172.16.238.11 on ssh:notty
There were 3 failed login attempts since the last successful login.
[banner@stapp03 ~]$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak.$(date +%F)

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for banner: 
[banner@stapp03 ~]$ sudo vi /etc/ssh/sshd_config
[banner@stapp03 ~]$ sudo systemctl restart sshd
[banner@stapp03 ~]$ sudo sshd -T | grep permitrootlogin
permitrootlogin no
[banner@stapp03 ~]$ 