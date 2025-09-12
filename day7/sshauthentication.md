thor@jumphost ~$ ssh thor@jumphost
ssh: Could not resolve hostname jumphost: Name or service not known
thor@jumphost ~$ ^C
thor@jumphost ~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/thor/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/thor/.ssh/id_rsa
Your public key has been saved in /home/thor/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:HbLsBciPLRAbChmCPOcby3QmLQiFM9uow3juR06IIKY thor@jumphost.stratos.xfusioncorp.com
The key's randomart image is:
+---[RSA 3072]----+
|*=. o            |
|O+ o = .         |
|.** + o o .      |
|=o.* = = = .     |
|O.o.O o S o      |
|E.o+o  o .       |
| + +    .        |
|  . o            |
| ...             |
+----[SHA256]-----+
thor@jumphost ~$ ssh-copy-id tony@stapp01
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/thor/.ssh/id_rsa.pub"
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:+QiMWlUyLSHayP92uM/8vI2vSlpqgmu/h99w0z/vqs8.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
tony@stapp01's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'tony@stapp01'"
and check to make sure that only the key(s) you wanted were added.

thor@jumphost ~$ ssh-copy-id steve@stapp02
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/thor/.ssh/id_rsa.pub"
The authenticity of host 'stapp02 (172.16.238.11)' can't be established.
ED25519 key fingerprint is SHA256:Zsdu54tO9vva0IxZ9GWGASqEFf7Lc4+g58V/RSsfBqM.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
steve@stapp02's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'steve@stapp02'"
and check to make sure that only the key(s) you wanted were added.

thor@jumphost ~$ ssh-copy-id banner@stapp03
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/thor/.ssh/id_rsa.pub"
The authenticity of host 'stapp03 (172.16.238.12)' can't be established.
ED25519 key fingerprint is SHA256:Z8DH4dpYNvmClEvf3dzv3xvXmo+V3rkmon1/IHpdW8s.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
banner@stapp03's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'banner@stapp03'"
and check to make sure that only the key(s) you wanted were added.

thor@jumphost ~$ ssh tony@stapp01 "hostname"
stapp01.stratos.xfusioncorp.com
thor@jumphost ~$ ssh steve@stapp02 "hostname"
stapp02.stratos.xfusioncorp.com
thor@jumphost ~$ ssh banner@stapp03 "hostname"
stapp03.stratos.xfusioncorp.com
thor@jumphost ~$ ssh tony@stapp01 "sudo whoami"

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

sudo: a terminal is required to read the password; either use the -S option to read from standard input or configure an askpass helper
sudo: a password is required
thor@jumphost ~$ ssh steve@stapp02 "sudo whoami"

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

sudo: a terminal is required to read the password; either use the -S option to read from standard input or configure an askpass helper
sudo: a password is required
thor@jumphost ~$ ssh banner@stapp03 "sudo whoami"

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

sudo: a terminal is required to read the password; either use the -S option to read from standard input or configure an askpass helper
sudo: a password is required
thor@jumphost ~$ ^C
thor@jumphost ~$ ssh tony@stapp01
[tony@stapp01 ~]$ sudo visudo

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[tony@stapp01 ~]$ exit
logout
Connection to stapp01 closed.
thor@jumphost ~$ ssh tony@stapp01 "sudo whoami"
root
thor@jumphost ~$ ssh steve@stapp02
[steve@stapp02 ~]$ sudo visudo

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve: 
[steve@stapp02 ~]$ exit
logout
Connection to stapp02 closed.
thor@jumphost ~$ ssh steve@stapp02 "sudo whoami"
root
thor@jumphost ~$ ssh banner@stapp03
[banner@stapp03 ~]$ sudo visudo

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for banner: 
[banner@stapp03 ~]$ ssh banner@stapp03 "sudo whoami"
The authenticity of host 'stapp03 (172.16.238.12)' can't be established.
ED25519 key fingerprint is SHA256:Z8DH4dpYNvmClEvf3dzv3xvXmo+V3rkmon1/IHpdW8s.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? ^[[B^[[B^[[B^[[B^[[Bssh banner@stapp03 "sudo whoami"
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added 'stapp03' (ED25519) to the list of known hosts.
banner@stapp03's password: 
root
[banner@stapp03 ~]$ exit
logout
Connection to stapp03 closed.
thor@jumphost ~$ ssh banner@stapp03
Last login: Fri Sep 12 17:31:32 2025 from 172.16.238.3
[banner@stapp03 ~]$ sudo visudo
[banner@stapp03 ~]$ exit
logout
Connection to stapp03 closed.
thor@jumphost ~$ ssh banner@stapp03 "sudo whoami"
root
thor@jumphost ~$ 