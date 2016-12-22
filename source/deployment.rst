Deployment
=============

Pomf aims to be as simple as possible to deploy.

Written in PHP and using the PDO database
driver, Pomf may be deployed using a wide array of configurations.  Any PHP compatible web server, and PDO supported database
engine may be used.

Examples of supported web servers

* Nginx
* Apache HTTP Server
* lighttpd

Examples of supported database engines

* SQLite
* PostgreSQL
* MySQL


Environment setup
------------------
The deployment of a web stack is considered outside the scope of this documentation.  It is thus assumed that a web stack has already been deployed.

For your convenience however, guides are provided for basic deployments of various configurations.

TODO: basic deployment guides

.. toctree::
  deployment_nginx
  deployment_mariadb

Pomf setup
----------------

::

  git clone --recursive https://github.com/pomf/pomf
  nano pomf/includes/settings.inc.php
