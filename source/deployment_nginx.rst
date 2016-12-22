Basic Nginx deployment guide
=============================
TODO: nginx, php-fpm intro; explain software choice/necessity

This guide documents a basic deployment of the Nginx web server, along
with PHP support provided through php-fpm.

It is assumed you have already deployed an Enterprise Linux distribution, such as Red Hat Enterprise Linux or CentOS.

Preparation
-------------

System update
^^^^^^^^^^^^^^^
Though optional, it is recommended you update your system before you continue.

On Enterprise Linux systems this may be done like so
::
  # yum update -y

Package installation
^^^^^^^^^^^^^^^^^^^^^^
The necessary packages to support an nginx deployment with php support should be installed
::
  # yum install -y nginx php70w-fpm php70w-common


Nginx configuration
--------------------

TODO: nginx config

The Nginx systemd service should now be enabled and started
::
  # systemctl enable nginx.service
  # systemctl start nginx.service

PHP configuration
------------------
TODO: php config

::
  sudo vi /etc/php.ini
  cgi.fix_pathinfo=0

The `php-fpm.service` systemd service should now be enabled and started
::
  # systemctl enable php-fpm.service
  # systemctl start php-fpm.service
