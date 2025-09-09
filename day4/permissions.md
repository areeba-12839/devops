[tony@stapp01 ~]$ steve
-bash: steve: command not found
[tony@stapp01 ~]$ sudo chmod a+x /tmp/xfusioncorp.sh

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[tony@stapp01 ~]$ ls -l /tmp/xfusioncorp.sh
---x--x--x 1 root root 40 Sep  9 16:54 /tmp/xfusioncorp.sh
[tony@stapp01 ~]$ sudo chmod 755 /tmp/xfusioncorp.sh
[tony@stapp01 ~]$ sudo chmod a+x /tmp/xfusioncorp.sh
[tony@stapp01 ~]$ sudo chmod 755 /tmp/xfusioncorp.sh
[tony@stapp01 ~]$ ls -l /tmp/xfusioncorp.sh
-rwxr-xr-x 1 root root 40 Sep  9 16:54 /tmp/xfusioncorp.sh
[tony@stapp01 ~]$ ls -l /tmp/xfusioncorp.sh
-rwxr-xr-x 1 root root 40 Sep  9 16:54 /tmp/xfusioncorp.sh
[tony@stapp01 ~]$ /tmp/xfusioncorp.sh
Welcome To KodeKloud
[tony@stapp01 ~]$ 