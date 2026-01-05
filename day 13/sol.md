thor@jumphost ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ED25519 key fingerprint is SHA256:yHfHGhqXCBD4DoZFPnUf9hRwq0W6xDOIQFAWdsrsnEI.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01' (ED25519) to the list of known hosts.
tony@stapp01's password: 
[tony@stapp01 ~]$ sudo systemctl status httpd

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
● httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled; vendor preset: disabled)
   Active: failed (Result: exit-code) since Wed 2025-12-31 14:21:23 UTC; 3min 39s ago
     Docs: man:httpd(8)
           man:apachectl(8)
  Process: 789 ExecStop=/bin/kill -WINCH ${MAINPID} (code=exited, status=1/FAILURE)
  Process: 788 ExecStart=/usr/sbin/httpd $OPTIONS -DFOREGROUND (code=exited, status=1/FAILURE)
 Main PID: 788 (code=exited, status=1/FAILURE)

Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com httpd[788]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com httpd[788]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com httpd[788]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com httpd[788]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com kill[789]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
Hint: Some lines were ellipsized, use -l to show in full.
[tony@stapp01 ~]$ stapp01.stratos.xfusioncorp.com httpd[788]: ...
-bash: stapp01.stratos.xfusioncorp.com: command not found
[tony@stapp01 ~]$ Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
-bash: Dec: command not found
[tony@stapp01 ~]$ Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com kill[789]: ...
-bash: Dec: command not found
[tony@stapp01 ~]$ Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
-bash: Dec: command not found
[tony@stapp01 ~]$ Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
-bash: Dec: command not found
[tony@stapp01 ~]$ Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
-bash: Dec: command not found
[tony@stapp01 ~]$ Dec 31 14:21:23 stapp01.stratos.xfusioncorp.com systemd[1]: ...
-bash: Dec: command not found
[tony@stapp01 ~]$ sudo systemctl is-active httpd
failed
[tony@stapp01 ~]$ sudo vi /etc/httpd/conf/httpd.conf
[tony@stapp01 ~]$ sudo systemctl restart httpd
Job for httpd.service failed because the control process exited with error code. See "systemctl status httpd.service" and "journalctl -xe" for details.
[tony@stapp01 ~]$ sudo systemctl enable httpd
Created symlink from /etc/systemd/system/multi-user.target.wants/httpd.service to /usr/lib/systemd/system/httpd.service.
[tony@stapp01 ~]$ sudo systemctl is-active httpd
failed
[tony@stapp01 ~]$ sudo ss -lntp | grep 5004
LISTEN     0      10     127.0.0.1:5004                     *:*                   users:(("sendmail",pid=763,fd=4))
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ sudo systemctl stop sendmail
[tony@stapp01 ~]$ 
[tony@stapp01 ~]$ sudo systemctl disable sendmail
Removed symlink /etc/systemd/system/multi-user.target.wants/sm-client.service.
Removed symlink /etc/systemd/system/multi-user.target.wants/sendmail.service.
[tony@stapp01 ~]$ sudo ss -lntp | grep 5004
[tony@stapp01 ~]$ sudo systemctl restart httpd
[tony@stapp01 ~]$ sudo systemctl is-active httpd
active
[tony@stapp01 ~]$ sudo ss -lntp | grep 5004
LISTEN     0      511          *:5004                     *:*                   users:(("httpd",pid=1325,fd=3),("httpd",pid=1324,fd=3),("httpd",pid=1323,fd=3),("httpd",pid=1322,fd=3),("httpd",pid=1321,fd=3),("httpd",pid=1320,fd=3))
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ ^C
[tony@stapp01 ~]$ exit
logout
Connection to stapp01 closed.
thor@jumphost ~$ ssh steve@stapp02
The authenticity of host 'stapp02 (172.16.238.11)' can't be established.
ED25519 key fingerprint is SHA256:miJpTuIYNwvFsgBPec4zBi4tbWsWwUYha2bZzsejiHs.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp02' (ED25519) to the list of known hosts.
steve@stapp02's password: 
[steve@stapp02 ~]$ sudo systemctl status httpd
sudo ss -lntp | grep 5004

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve: 
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/h>
     Active: active (running) since Wed 2025-1>
       Docs: man:httpd.service(8)
   Main PID: 1671 (httpd)
     Status: "Total requests: 0; Idle/Busy wor>
      Tasks: 177 (limit: 411434)
     Memory: 19.9M
     CGroup: /docker/07072fd87a67d0448a9b591f4>
             ├─1671 /usr/sbin/httpd -DFOREGROU>
             ├─1678 /usr/sbin/httpd -DFOREGROU>
             ├─1679 /usr/sbin/httpd -DFOREGROU>
             ├─1680 /usr/sbin/httpd -DFOREGROU>
             └─1681 /usr/sbin/httpd -DFOREGROU>

Dec 31 14:35:03 stapp02.stratos.xfusioncorp.co>
Dec 31 14:35:13 stapp02.stratos.xfusioncorp.co>
Dec 31 14:35:23 stapp02.stratos.xfusioncorp.co>
Dec 31 14:35:33 stapp02.stratos.xfusioncorp.co>
Dec 31 14:35:43 stapp02.stratos.xfusioncorp.co>
Dec 31 14:35:53 stapp02.stratos.xfusioncorp.co>
Dec 31 14:36:03 stapp02.stratos.xfusioncorp.co>
Dec 31 14:36:13 stapp02.stratos.xfusioncorp.co>
Dec 31 14:36:23 stapp02.stratos.xfusioncorp.co>
Dec 31 14:36:33 stapp02.stratos.xfusioncorp.co>
LISTEN 0      511          0.0.0.0:5004       0.0.0.0:*    users:(("httpd",pid=1681,fd=3),("httpd",pid=1680,fd=3),("httpd",pid=1679,fd=3),("httpd",pid=1671,fd=3))
[steve@stapp02 ~]$ ^C
[steve@stapp02 ~]$ sudo systemctl status httpd
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/h>
     Active: active (running) since Wed 2025-1>
       Docs: man:httpd.service(8)
   Main PID: 1671 (httpd)
     Status: "Total requests: 0; Idle/Busy wor>
      Tasks: 177 (limit: 411434)
     Memory: 19.9M
     CGroup: /docker/07072fd87a67d0448a9b591f4>
             ├─1671 /usr/sbin/httpd -DFOREGROU>
             ├─1678 /usr/sbin/httpd -DFOREGROU>
             ├─1679 /usr/sbin/httpd -DFOREGROU>
             ├─1680 /usr/sbin/httpd -DFOREGROU>
             └─1681 /usr/sbin/httpd -DFOREGROU>

Dec 31 14:36:53 stapp02.stratos.xfusioncorp.co>
Dec 31 14:37:03 stapp02.stratos.xfusioncorp.co>
Dec 31 14:37:13 stapp02.stratos.xfusioncorp.co>
Dec 31 14:37:23 stapp02.stratos.xfusioncorp.co>
Dec 31 14:37:33 stapp02.stratos.xfusioncorp.co>
Dec 31 14:37:43 stapp02.stratos.xfusioncorp.co>
Dec 31 14:37:53 stapp02.stratos.xfusioncorp.co>
Dec 31 14:38:03 stapp02.stratos.xfusioncorp.co>
Dec 31 14:38:13 stapp02.stratos.xfusioncorp.co>
Dec 31 14:38:23 stapp02.stratos.xfusioncorp.co>
[steve@stapp02 ~]$ sudo ss -lntp | grep 5004
LISTEN 0      511          0.0.0.0:5004       0.0.0.0:*    users:(("httpd",pid=1681,fd=3),("httpd",pid=1680,fd=3),("httpd",pid=1679,fd=3),("httpd",pid=1671,fd=3))
[steve@stapp02 ~]$ exit
logout
Connection to stapp02 closed.
thor@jumphost ~$ ssh banner@stapp03
The authenticity of host 'stapp03 (172.16.238.12)' can't be established.
ED25519 key fingerprint is SHA256:ITy81VsMYNF90tdZTqJbisGZ1gHwOZ70b4TZhUSO9aw.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp03' (ED25519) to the list of known hosts.
banner@stapp03's password: 
[banner@stapp03 ~]$ sudo systemctl status httpd 
sudo ss -lntp | grep 5004

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for banner: 
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/h>
     Active: active (running) since Wed 2025-1>
       Docs: man:httpd.service(8)
   Main PID: 1666 (httpd)
     Status: "Total requests: 0; Idle/Busy wor>
      Tasks: 177 (limit: 411434)
     Memory: 19.6M
     CGroup: /docker/6490eb825bb90b6a7d6f5ff07>
             ├─1666 /usr/sbin/httpd -DFOREGROU>
             ├─1673 /usr/sbin/httpd -DFOREGROU>
             ├─1674 /usr/sbin/httpd -DFOREGROU>
             ├─1675 /usr/sbin/httpd -DFOREGROU>
             └─1676 /usr/sbin/httpd -DFOREGROU>

Dec 31 14:38:24 stapp03.stratos.xfusioncorp.co>
Dec 31 14:38:34 stapp03.stratos.xfusioncorp.co>
Dec 31 14:38:44 stapp03.stratos.xfusioncorp.co>
Dec 31 14:38:54 stapp03.stratos.xfusioncorp.co>
Dec 31 14:39:04 stapp03.stratos.xfusioncorp.co>
Dec 31 14:39:14 stapp03.stratos.xfusioncorp.co>
Dec 31 14:39:24 stapp03.stratos.xfusioncorp.co>
Dec 31 14:39:34 stapp03.stratos.xfusioncorp.co>
Dec 31 14:39:44 stapp03.stratos.xfusioncorp.co>
Dec 31 14:39:54 stapp03.stratos.xfusioncorp.co>
LISTEN 0      511          0.0.0.0:5004       0.0.0.0:*    users:(("httpd",pid=1676,fd=3),("httpd",pid=1675,fd=3),("httpd",pid=1674,fd=3),("httpd",pid=1666,fd=3))
[banner@stapp03 ~]$ ^C
[banner@stapp03 ~]$ ^C
[banner@stapp03 ~]$ sudo systemctl status httpd 
● httpd.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/h>
     Active: active (running) since Wed 2025-1>
       Docs: man:httpd.service(8)
   Main PID: 1666 (httpd)
     Status: "Total requests: 0; Idle/Busy wor>
      Tasks: 177 (limit: 411434)
     Memory: 19.6M
     CGroup: /docker/6490eb825bb90b6a7d6f5ff07>
             ├─1666 /usr/sbin/httpd -DFOREGROU>
             ├─1673 /usr/sbin/httpd -DFOREGROU>
             ├─1674 /usr/sbin/httpd -DFOREGROU>
             ├─1675 /usr/sbin/httpd -DFOREGROU>
             └─1676 /usr/sbin/httpd -DFOREGROU>

Dec 31 14:39:54 stapp03.stratos.xfusioncorp.co>
Dec 31 14:40:04 stapp03.stratos.xfusioncorp.co>
Dec 31 14:40:14 stapp03.stratos.xfusioncorp.co>
Dec 31 14:40:24 stapp03.stratos.xfusioncorp.co>
Dec 31 14:40:34 stapp03.stratos.xfusioncorp.co>
Dec 31 14:40:44 stapp03.stratos.xfusioncorp.co>
Dec 31 14:40:54 stapp03.stratos.xfusioncorp.co>
Dec 31 14:41:04 stapp03.stratos.xfusioncorp.co>
Dec 31 14:41:14 stapp03.stratos.xfusioncorp.co>
Dec 31 14:41:24 stapp03.stratos.xfusioncorp.co>
[banner@stapp03 ~]$ sudo ss -lntp | grep 5004
LISTEN 0      511          0.0.0.0:5004       0.0.0.0:*    users:(("httpd",pid=1676,fd=3),("httpd",pid=1675,fd=3),("httpd",pid=1674,fd=3),("httpd",pid=1666,fd=3))
[banner@stapp03 ~]$ exit
logout
Connection to stapp03 closed.
thor@jumphost ~$ 