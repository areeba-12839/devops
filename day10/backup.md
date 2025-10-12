thor@jumphost ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:CtbqriS/3sa6ICRmkOpypVYv0VDP+e4qj4zDPalvfG4.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
[tony@stapp01 ~]$ mkdir -p /scripts
[tony@stapp01 ~]$ vi /scripts/blog_backup.sh

[1]+  Stopped                 vi /scripts/blog_backup.sh
[tony@stapp01 ~]$ vi /scripts/blog_backup.sh
[tony@stapp01 ~]$ chmod +x /scripts/blog_backup.sh
[tony@stapp01 ~]$ /scripts/blog_backup.sh
/scripts/blog_backup.sh: line 8: zip: command not found
The authenticity of host 'stbkp01 (172.16.238.16)' can't be established.
ED25519 key fingerprint is SHA256:2VtShyLnWH3HsZ6tbGgB1rKh8Gec6fIG4rSLOEB+5w0.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stbkp01' (ED25519) to the list of known hosts.
clint@stbkp01's password: 
stat local "/backup/xfusioncorp_blog.zip": No such file or directory
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo yum install -y zip

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
CentOS Stream   26 kB/s | 6.7 kB     00:00    
CentOS Stream  6.2 MB/s | 8.8 MB     00:01    
CentOS Stream   34 kB/s | 6.8 kB     00:00    
CentOS Stream  9.3 MB/s |  25 MB     00:02    
CentOS Stream   26 kB/s | 8.0 kB     00:00    
CentOS Stream   28 kB/s |  20 kB     00:00    
Docker CE Stab  20 kB/s | 2.0 kB     00:00    
Docker CE Stab 360 kB/s |  56 kB     00:00    
Extra Packages 122 kB/s |  34 kB     00:00    
Extra Packages  16 MB/s |  20 MB     00:01    
Extra Packages 3.0 kB/s | 993  B     00:00    
Extra Packages  98 kB/s |  23 kB     00:00    
Dependencies resolved.
===============================================
 Package Arch     Version       Repo      Size
===============================================
Installing:
 zip     x86_64   3.0-35.el9    baseos   266 k
Installing dependencies:
 unzip   x86_64   6.0-59.el9    baseos   182 k

Transaction Summary
===============================================
Install  2 Packages

Total download size: 447 k
Installed size: 1.1 M
Downloading Packages:
(1/2): unzip-6 891 kB/s | 182 kB     00:00    
(2/2): zip-3.0 1.2 MB/s | 266 kB     00:00    
-----------------------------------------------
Total          1.0 MB/s | 447 kB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Installing       : unzip-6.0-59.el9.x8   1/2 
  Installing       : zip-3.0-35.el9.x86_   2/2 
  Running scriptlet: zip-3.0-35.el9.x86_   2/2 
  Verifying        : unzip-6.0-59.el9.x8   1/2 
  Verifying        : zip-3.0-35.el9.x86_   2/2 

Installed:
  unzip-6.0-59.el9.x86_64                      
[tony@stapp01 ~]$ thor@jumphost ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:CtbqriS/3sa6ICRmkOpypVYv0VDP+e4qj4zDPalvfG4.
This key is not known by any other namesh
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: og/.gitkeep (stored 0%)
[tony@stapp01 ~]$ mkdir -p /scripts
[tony@stapp01 ~]$ vi /scripts/blog_backup.sh  
[tony@stapp01 ~]$ ^C
[1]+  Stopped                 vi /scripts/blog_backup.sh
[tony@stapp01 ~]$ vi /scripts/blog_backup.sh8.10)' can't be established.
[tony@stapp01 ~]$ chmod +x /scripts/blog_backup.shkOpypVYv0VDP+e4qj4zDPalvfG4.
[tony@stapp01 ~]$ /scripts/blog_backup.sh
/scripts/blog_backup.sh: line 8: zip: command not foundingerprint])? yes
The authenticity of host 'stbkp01 (172.16.238.16)' can't be established.s.
ED25519 key fingerprint is SHA256:2VtShyLnWH3HsZ6tbGgB1rKh8Gec6fIG4rSLOEB+5w0.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stbkp01' (ED25519) to the list of known hosts.
clint@stbkp01's password:     vi /scripts/blog_backup.sh
stat local "/backup/xfusioncorp_blog.zip": No such file or directory
[tony@stapp01 ~]$ ^Cmod +x /scripts/blog_backup.sh
[tony@stapp01 ~]$ sudo yum install -y zip
/scripts/blog_backup.sh: line 8: zip: command not found
We trust you have received the usual lecture from the local Systemished.
Administrator. It usually boils down to these three things:Gec6fIG4rSLOEB+5w0.
This key is not known by any other names
    #1) Respect the privacy of others.ecting (y
    #2) Think before you type.
[tony@stapp01 ~]$  588     3.3MB/s   00:00    %)%)y.
-bash: thor@jumphost: command not found
-bash: The: command not found
-bash: [tony@stapp01: command not found
-bash: [tony@stapp01: command not found
-bash: [1]+: command not found
-bash: [tony@stapp01: command not found
-bash: [tony@stapp01: command not found
-bash: [tony@stapp01: command not found
-bash: /scripts/blog_backup.sh:: No such file or directory
-bash: The: command not found
stat: cannot statx 'local': No such file or directory
stat: cannot statx '/backup/xfusioncorp_blog.zip:': No such file or directory
stat: cannot statx 'No': No such file or directory
stat: cannot statx 'such': No such file or directory
stat: cannot statx 'file': No such file or directory
stat: cannot statx 'or': No such file or directory
stat: cannot statx 'directory': No such file or directory
-bash: [tony@stapp01: command not found
-bash: [tony@stapp01: command not found
-bash: We: command not found
-bash: Administrator.: command not found
-bash: [sudo]: command not found
-bash: 6.7: command not found
-bash: CentOS: command not found
-bash: CentOS: command not found
-bash: 8.8: command not found
-bash: CentOS: command not found
-bash: 6.8: command not found
-bash: CentOS: command not found
-bash: 25: command not found
-bash: CentOS: command not found
-bash: 8.0: command not found
-bash: CentOS: command not found
-bash: 20: command not found
-bash: 2.0: command not found
-bash: Docker: command not found
-bash: Docker: command not found
-bash: 56: command not found
-bash: 34: command not found
-bash: Extra: command not found
-bash: Extra: command not found
-bash: 20: command not found
-bash: Extra: command not found
-bash: 993: command not found
-bash: Extra: command not found
-bash: 23: command not found
-bash: Dependencies: command not found
-bash: ===============================================: command not found
-bash: Package: command not found
-bash: ===============================================: command not found
-bash: Installing:: command not found
        zip warning: name not matched: 3.0-35.el9
        zip warning: name not matched: baseos
        zip warning: name not matched: 266
        zip warning: name not matched: k

zip error: Nothing to do! (x86_64.zip)
-bash: Installing: command not found
unzip:  cannot find or open x86_64, x86_64.zip or x86_64.ZIP.
-bash: Transaction: command not found
-bash: ===============================================: command not found
-bash: Install: command not found
-bash: Total: command not found
-bash: Installed: command not found
-bash: Downloading: command not found
-bash: syntax error near unexpected token `:'
-bash: syntax error near unexpected token `:'
-bash: -----------------------------------------------: command not found
-bash: Total: command not found
-bash: 447: command not found
-bash: Running: command not found
-bash: Transaction: command not found
-bash: Running: command not found
-bash: Transaction: command not found
-bash: Running: command not found
-bash: Preparing: command not found
-bash: Installing: command not found
-bash: Installing: command not found
-bash: Running: command not found
-bash: Verifying: command not found
-bash: Verifying: command not found
-bash: Installed:: command not found
-bash: unzip-6.0-59.el9.x86_64: command not found
-bash: zip-3.0-35.el9.x86_64: command not found
-bash: Complete!: command not found
-bash: [tony@stapp01: command not found
-bash: syntax error near unexpected token `('
-bash: syntax error near unexpected token `('
-bash: syntax error near unexpected token `('
> 
> ^C
[tony@stapp01 ~]$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/tony/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/tony/.ssh/id_rsa
Your public key has been saved in /home/tony/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:9LU39UcCaXCbjnu2RapQkaQIveYykWfNWKBLw3u9wbg tony@stapp01.stratos.xfusioncorp.com
The key's randomart image is:
+---[RSA 3072]----+
|    ....  o.o.   |
|   . o...o oo+   |
|    =..*o o.+ . o|
|   .o+*=o. = . +.|
|    o*o S + o + o|
|    o... + . + ..|
|     oE o . + .  |
|         . + o   |
|          . .    |
+----[SHA256]-----+
[tony@stapp01 ~]$ ssh-copy-id clint@stbkp01
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/tony/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
clint@stbkp01's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'clint@stbkp01'"
and check to make sure that only the key(s) you wanted were added.

[tony@stapp01 ~]$ ssh clint@stbkp01
[clint@stbkp01 ~]$ exit
logout
Connection to stbkp01 closed.
[tony@stapp01 ~]$ /scripts/blog_backup.sh
updating: var/www/html/blog/ (stored 0%)
updating: var/www/html/blog/index.html (stored 0%)
updating: var/www/html/blog/.gitkeep (stored 0%)
xfusioncorp_ 100%  588     1.4MB/s   00:00    
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ ssh clint@stbkp01
Last login: Sun Oct 12 18:27:58 2025 from 172.16.238.10
[clint@stbkp01 ~]$ ls -l /backup/
total 4
-rw-r--r-- 1 clint clint 588 Oct 12 18:28 xfusioncorp_blog.zip
[clint@stbkp01 ~]$ ^C
[clint@stbkp01 ~]$ 