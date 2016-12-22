MariaDB basic deployment guide
===============================
TODO: mariadb intro

This guide documents a basic deployment of the MariaDB database engine.
It assumed you have both already deployed an Ent.rprise Linux distribution, such as
Red Hat Enterprise Linux or CentOS, as well as a supported web server, such as Nginx, Apache, or lighttpd.

Preparation
------------
Before you continue, it is necessary to install the MariaDB database encine pacakges, as well as the corresponding PDO driver necessary to support its use via PHP.

TODO: put all packages here
On Enterprise Linux
::
  # yum install -y php70w-mysql

Database engine configuration
------------------------------

The `mariadb.service` systemd service should be enabled and started before continuing
::
  # systemctl start mariadb
  # systemctl enable mariadb

The initial secure configuration of the database engine should then be performed
::
  # mysql_secure_installation

TODO: these commands
::
  mariadb-server mariadb-y
  mysql -u root -p
  CREATE DATABASE pomf;
  GRANT ALL ON pomf.* TO pomf@localhost IDENTIFIED BY 'password';
  mysql -u pomf -p pomf < schema.sql
