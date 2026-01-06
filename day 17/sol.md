thor@jumphost ~$ ssh peter@stdb01
The authenticity of host 'stdb01 (172.16.239.10)' can't be established.
ED25519 key fingerprint is SHA256:BzuRLIjod0EPMEuZ5NCbPbgHO6G44YpaC9phlTlE9Ss.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stdb01' (ED25519) to the list of known hosts.
peter@stdb01's password: 
[peter@stdb01 ~]$ sudo su - postgres

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for peter: 
[postgres@stdb01 ~]$ psql
psql (13.14)
Type "help" for help.

postgres=# CREATE USER kodekloud_cap WITH PASSWORD 'Rc5C9EyvbU';
CREATE ROLE
postgres=# CREATE DATABASE kodekloud_db4;
CREATE DATABASE
postgres=# GRANT ALL PRIVILEGES ON DATABASE kodekloud_db4 TO kodekloud_cap;
GRANT
postgres=# \q
[postgres@stdb01 ~]$ exit
[peter@stdb01 ~]$ exit
Connection to stdb01 closed.
thor@jumphost ~$