thor@jumphost ~$ sudo pip3 install --upgrade pip
sudo: pip3: command not found
thor@jumphost ~$ ^C
thor@jumphost ~$ sudo yum install -y python3 python3-pip
CentOS Stream   24 kB/s | 6.7 kB     00:00    
CentOS Stream   16 MB/s | 8.8 MB     00:00    
CentOS Stream   33 kB/s | 6.8 kB     00:00    
CentOS Stream   22 MB/s |  25 MB     00:01    
CentOS Stream   36 kB/s | 8.0 kB     00:00    
CentOS Stream   62 kB/s |  20 kB     00:00    
Extra Packages 165 kB/s |  34 kB     00:00    
Extra Packages  13 MB/s |  20 MB     00:01    
Extra Packages 5.0 kB/s | 993  B     00:00    
Extra Packages  89 kB/s |  24 kB     00:00    
Extra Packages 396 kB/s | 289 kB     00:00    
Package python3-3.9.18-3.el9.x86_64 is already installed.
Package python3-pip-21.3.1-1.el9.noarch is already installed.
Dependencies resolved.
===============================================
 Package  Arch   Version       Repo       Size
===============================================
Upgrading:
 openssl  x86_64 1:3.5.1-5.el9 baseos    1.5 M
 openssl-devel
          x86_64 1:3.5.1-5.el9 appstream 4.8 M
 openssl-libs
          x86_64 1:3.5.1-5.el9 baseos    2.3 M
 python3  x86_64 3.9.23-2.el9  baseos     26 k
 python3-libs
          x86_64 3.9.23-2.el9  baseos    8.1 M
Installing dependencies:
 openssl-fips-provider
          x86_64 1:3.5.1-5.el9 baseos    814 k

Transaction Summary
===============================================
Install  1 Package
Upgrade  5 Packages

Total download size: 17 M
Downloading Packages:
(1/6): openssl 835 kB/s | 814 kB     00:00    
(2/6): python3 350 kB/s |  26 kB     00:00    
(3/6): openssl 1.1 MB/s | 1.5 MB     00:01    
(4/6): openssl  11 MB/s | 4.8 MB     00:00    
(5/6): openssl 1.2 MB/s | 2.3 MB     00:01    
(6/6): python3 1.5 MB/s | 8.1 MB     00:05    
-----------------------------------------------
Total          2.5 MB/s |  17 MB     00:06     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                       1/1 
  Upgrading        : openssl-libs-1:3.    1/11 
  Installing       : openssl-fips-prov    2/11 
  Upgrading        : python3-3.9.23-2.    3/11 
  Upgrading        : python3-libs-3.9.    4/11 
  Upgrading        : openssl-1:3.5.1-5    5/11 
  Upgrading        : openssl-devel-1:3    6/11 
  Cleanup          : openssl-1:3.2.1-1    7/11 
  Cleanup          : openssl-devel-1:3    8/11 
  Cleanup          : python3-3.9.18-3.    9/11 
  Cleanup          : python3-libs-3.9.   10/11 
  Cleanup          : openssl-libs-1:3.   11/11 
  Running scriptlet: openssl-libs-1:3.   11/11 
  Verifying        : openssl-fips-prov    1/11 
  Verifying        : openssl-1:3.5.1-5    2/11 
  Verifying        : openssl-1:3.2.1-1    3/11 
  Verifying        : openssl-libs-1:3.    4/11 
  Verifying        : openssl-libs-1:3.    5/11 
  Verifying        : python3-3.9.23-2.    6/11 
  Verifying        : python3-3.9.18-3.    7/11 
  Verifying        : python3-libs-3.9.    8/11 
  Verifying        : python3-libs-3.9.    9/11 
  Verifying        : openssl-devel-1:3   10/11 
  Verifying        : openssl-devel-1:3   11/11 

Upgraded:
  openssl-1:3.5.1-5.el9.x86_64                 
  openssl-devel-1:3.5.1-5.el9.x86_64           
  openssl-libs-1:3.5.1-5.el9.x86_64            
  python3-3.9.23-2.el9.x86_64                  
  python3-libs-3.9.23-2.el9.x86_64             
Installed:
  openssl-fips-provider-1:3.5.1-5.el9.x86_64   

Complete!
thor@jumphost ~$ pip3 --version
pip 25.2 from /usr/local/lib/python3.9/site-packages/pip (python 3.9)
thor@jumphost ~$ sudo pip3 install --upgrade pip
sudo: pip3: command not found
thor@jumphost ~$ sudo pip3 install ansible==4.9.0
sudo: pip3: command not found
thor@jumphost ~$ ^C
thor@jumphost ~$ which pip3
/usr/local/bin/pip3
thor@jumphost ~$ sudo /usr/local/bin/pip3 install ansible==4.9.0
Collecting ansible==4.9.0
  Downloading ansible-4.9.0.tar.gz (36.6 MB)
     ━━━━━━━━━━━ 36.6/36.6   89.2 MB/s  0:00:00
                 MB                            
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Collecting ansible-core<2.12,>=2.11.6 (from ansible==4.9.0)
  Downloading ansible-core-2.11.12.tar.gz (7.1 MB)
     ━━━━━━━━━━━━ 7.1/7.1 MB 90.8 MB/s  0:00:00
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Collecting jinja2 (from ansible-core<2.12,>=2.11.6->ansible==4.9.0)
  Downloading jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
Requirement already satisfied: PyYAML in /usr/lib64/python3.9/site-packages (from ansible-core<2.12,>=2.11.6->ansible==4.9.0) (5.4.1)
Requirement already satisfied: cryptography in /usr/lib64/python3.9/site-packages (from ansible-core<2.12,>=2.11.6->ansible==4.9.0) (36.0.1)
Collecting packaging (from ansible-core<2.12,>=2.11.6->ansible==4.9.0)
  Downloading packaging-25.0-py3-none-any.whl.metadata (3.3 kB)
Collecting resolvelib<0.6.0,>=0.5.3 (from ansible-core<2.12,>=2.11.6->ansible==4.9.0)
  Downloading resolvelib-0.5.4-py2.py3-none-any.whl.metadata (3.7 kB)
Requirement already satisfied: cffi>=1.12 in /usr/lib64/python3.9/site-packages (from cryptography->ansible-core<2.12,>=2.11.6->ansible==4.9.0) (1.14.5)
Requirement already satisfied: pycparser in /usr/lib/python3.9/site-packages (from cffi>=1.12->cryptography->ansible-core<2.12,>=2.11.6->ansible==4.9.0) (2.20)
Collecting MarkupSafe>=2.0 (from jinja2->ansible-core<2.12,>=2.11.6->ansible==4.9.0)
  Downloading markupsafe-3.0.3-cp39-cp39-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (2.7 kB)
Requirement already satisfied: ply==3.11 in /usr/lib/python3.9/site-packages (from pycparser->cffi>=1.12->cryptography->ansible-core<2.12,>=2.11.6->ansible==4.9.0) (3.11)
Downloading resolvelib-0.5.4-py2.py3-none-any.whl (12 kB)
Downloading jinja2-3.1.6-py3-none-any.whl (134 kB)
Downloading markupsafe-3.0.3-cp39-cp39-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (20 kB)
Downloading packaging-25.0-py3-none-any.whl (66 kB)
Building wheels for collected packages: ansible, ansible-core
  Building wheel for ansible (pyproject.toml) ... done
  Created wheel for ansible: filename=ansible-4.9.0-py3-none-any.whl size=60168827 sha256=1bb4afda543b0f1520a21cab3420d12fb9e4fde9aa426acf25be9e2c791e350f
  Stored in directory: /root/.cache/pip/wheels/33/b7/3a/a0419b4a74d0493a7a17adb9b944b045ed8e81c6e5ec5f81d6
  Building wheel for ansible-core (pyproject.toml) ... done
  Created wheel for ansible-core: filename=ansible_core-2.11.12-py3-none-any.whl size=1961046 sha256=0cfde6a6cdea993897d3c880d89995e57bc1eff03ea4c6650fa7d5c79bed0fc0
  Stored in directory: /root/.cache/pip/wheels/06/b5/3d/4a4a1b494bb61ba26534ba172b81d1972467ee6c792d737b78
Successfully built ansible ansible-core
Installing collected packages: resolvelib, packaging, MarkupSafe, jinja2, ansible-core, ansible
Successfully installed MarkupSafe-3.0.3 ansible-4.9.0 ansible-core-2.11.12 jinja2-3.1.6 packaging-25.0 resolvelib-0.5.4
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager, possibly rendering your system unusable. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv. Use the --root-user-action option if you know what you are doing and want to suppress this warning.
thor@jumphost ~$ ^C
thor@jumphost ~$ ansible --version
ansible [core 2.11.12] 
  config file = None
  configured module search path = ['/home/thor/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.9/site-packages/ansible
  ansible collection location = /home/thor/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.9.23 (main, Aug 19 2025, 00:00:00) [GCC 11.5.0 20240719 (Red Hat 11.5.0-11)]
  jinja version = 3.1.6
  libyaml = True
thor@jumphost ~$ which ansible
/usr/local/bin/ansible
thor@jumphost ~$ echo $PATH
/home/thor/.local/bin:/home/thor/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin
thor@jumphost ~$ sudo su -
ansible --version
[root@jumphost ~]# sudo su -
Last login: Wed Oct  1 16:15:50 UTC 2025 on pts/1
[root@jumphost ~]# ansible --version
ansible [core 2.11.12] 
  config file = None
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.9/site-packages/ansible
  ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.9.23 (main, Aug 19 2025, 00:00:00) [GCC 11.5.0 20240719 (Red Hat 11.5.0-11)]
  jinja version = 3.1.6
  libyaml = True
[root@jumphost ~]# ^C
[root@jumphost ~]# 