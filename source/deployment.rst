Deployment
=============

Pomf aims to be as simple as possible to deploy.  This document provides an in detail look at the deployment process with a verbose description of steps.  If you are instead mmerely interesetd in quilky deploying Pomf, see :ref:`simple_deployment.rst`.

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

Node.JS
^^^^^^^^
Aa

Web stack
^^^^^^^^^^
The deployment of a web stack is considered outside the scope of this documentation.  It is thus assumed that a web stack has already been deployed.

For your convenience however, guides are provided for basic deployments of various configurations.

TODO: basic deployment guides

.. toctree::
  deployment_nginx
  deployment_mariadb

Pomf setup
-----------

Deployment of Pomf itself looks as follows

#. Clone source repository
#. Perform inital site configuration
#. Compile pomf
#. Install to destination directory


Clone source repository
^^^^^^^^^^^^^^^^^^^^^^^^
To obtain a copy of Pomf, the source repository should be cloned.  Note this is *not* the compiled Pomf site served to visitors.

::
  $ git clone --recursive https://github.com/pomf/pomf

Site configuration
^^^^^^^^^^^^^^^^^^^
Pomf configuration occurs in two places: in `dist.json` for front end related settings, and `settings.inc.php` for back end related settings.

Front end
Front-end related settings, such as the name of the site, and maximum allowable file size, are found in templates/site_variables.json. Changes made here will only take effect after rebuilding the site pages. This may be done by running make from the root of the site directory.

Back-end related settings, such as database configuration, and path for uploaded files, are found in static/php/includes/settings.inc.php. Changes made here take effect immediately.
