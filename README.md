# Ansible Role: Memcached

在RedHat/CentOS上安装Memcached的Ansible角色 \
An Ansible Role that installs Memcached on RedHat/CentOS


## Requirements
无
None.

## Role Variables

下面介绍了可用变量和默认值(可参照"defaults/main.yml"文件) \
The following describes the available variables and default values(refer to the "defaults/main.yml" file)

1. 运行Memcached的用户。\
 Users running memcached.

默认是使用"vars/main.yml" 中的定义的变量 memcached_app_user(memcached) \
The default is to use the variable memcached_app_user(memcached) defined in "vars/main.yml"

如果你想自定义的运行用户请在playbook中设置下面变量。\
If you want to customize the running user, please set the following variables in the playbook.


    memcached_user: memcached

2. 设置Ip和端口 \
Ip and Port

Memcached默认侦听请求的端口和IP地址(127.0.0.1为本地主机地址)。\
The port and IP address on which memcached  default listens for requests (127.0.0.1 for the localhost).

    memcached_port: 11211
    memcached_listen_ip: 127.0.0.1

3. Memcached限制。RAM的最大使用量(64 MB是默认值),和Mimcached的最大连接数 \
 Memcached limits. The maximum amount of RAM `memcached` will consume (64MB is the default), and the maximum number of simultaneous connections memcached will handle.

该roles中的memcached_memory_limit通过facts采集的`ansible_memtotal_mb`设置为远程主机的一半。(task: Define Memcached memory size) \
The variables `memcached_memory_limit` in the roles are set to half of the remote host through `ansible_memtotal_mb` collected by facts (task: Define Memcached memory size)

    memcached_memory_limit: 64
    memcached_connections: 1024

4. memcached日志文件的位置。\
The location of the memcached log file.

    memcached_log_file: /var/log/memcached/memcached.log

5. 通常memcached不会记录任何内容。更改为“-v”以启用日志记录，或更改为“-vv”以进行调试日志记录。\
 Normally memcached does not log anything. Change to "-v" to enable logging or to "-vv" for debug logging.

    memcached_log_verbosity: ""

Dependencies
------------
无依赖.\
None.


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: memcached, memcached_user: memcached }

License
-------

BSD

Author Information
------------------
Azure-sea
QQ: 2053921233
email: 2053921233@qq.com
