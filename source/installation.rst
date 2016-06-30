Installation
=============

Pomf is very simple to setup.  Its main dependencies are a web server with PHP support, and a PDO-compatible database.

The recommended configuration of pomf consists of:
* Nginx
* Mariadb
* PHP-7
* Lets encrypt

Start by updating the system

::
	sudo yum update

Setup Nginx
---------

::
	sudo nano /etc/yum.repos.d/nginx.repo
	[nginx]
	name=nginx repo
	baseurl=http://nginx.org/packages/mainline/centos/7/$basearch/
	gpgcheck=0
	enabled=1
	
	sudo yum install -y nginx
	curl  https://raw.githubusercontent.com/pomf/pomf/master/confs/nginx.conf > /etc/nginx/nginx.conf
	curl  https://raw.githubusercontent.com/pomf/pomf/master/confs/pantsu.cat.conf > /etc/nginx/conf.d/pantsu.cat.conf
	curl  https://raw.githubusercontent.com/pomf/pomf/master/confs/u.pantsu.cat.conf > /etc/nginx/conf.d/u.pantsu.cat

Setup PHP
----------

::
	sudo rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
	sudo rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm

	sudo yum install php70w-fpm php70w-common php70w-mysql
	sudo vi /etc/php.ini
	cgi.fix_pathinfo=0

	sudo systemctl start php-fpm
	sudo systemctl enable php-fpm

Setup Mariadb
--------------

::
	sudo systemctl start mariadb
	sudo mysql_secure_installation
	sudo systemctl enable mariadb

	mariadb-server mariadb-y
	mysql -u root -p
	CREATE DATABASE pomf;
	GRANT ALL ON pomf.* TO pomf@localhost IDENTIFIED BY 'password';
	mysql -u pomf -p pomf < schema.sql


Configure Pomf
----------------

::
	git clone --recursive https://github.com/pomf/pomf
	nano pomf/includes/settings.inc.php

