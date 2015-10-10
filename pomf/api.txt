.. _api:

API
===

Pantsu.cat has an API that is similar to Pomf.se and the other Pomf clones.
This means that most existing scripts and programs will be fully compatible with Pantsu.cat.
The only exception to this rule is that Pantsu.cat has scrict TLS 1.0+ only.

Example request
---------------
::

    curl -sS -F "files[]=@48_circles.gif" https://pantsu.cat/upload.php   

Example response
----------------
::
    
    {
      "success": true,
      "files": [
        {
          "hash": "f0ff06fc9770b96ff040a6016d14140ad6b79570",
          "name": "48_circles.gif",
          "url": "https:\/\/i.pantsu.cat\/gltraw.gif",
          "size": 4824
        }
      ]
    }
    

Output description
------------------

==========   ===========================================
Attributes   Description    
==========   ===========================================
success      true if uploading file was a success
hash         SHA1 hash 
name         Original file name 
url          URL that the uploaded file can be found at
size         File size 
==========   ===========================================

Example request
---------------
::

    curl -sS -F "files[]=@" https://pantsu.cat/upload.php   

Example response
----------------
::

  {
    "success": false,
    "errorcode": 400,
    "description": "No input file(s)"
  }

Output description
------------------

==========   ===========================================
Attributes   Description    
==========   ===========================================
success      false if uploading file failed 
errorcode    error code 
decription   description of the error 
==========   ===========================================


Output formats
--------------
The Pantsu.cat API supports a number of different output formats.
These have been implemented to serve different functions.

==========   ===========================================
Formats      Description    
==========   ===========================================
default      Default output is in json 
text         Multiple plain/text links 
html         HTML links 
gyazo        Single plain/text link
==========   ===========================================

To make use of different output formats just append ?ouput=format to upload.php.

Text response 
-------------
::

    curl -sS -F "files[]=@48_circles.gif" https://pantsu.cat/upload.php\?output\=text                                                                     ~
    https://i.pantsu.cat/fdrcdu.gif


HTML response
-------------
::

    curl -sS -F "files[]=@48_circles.gif" https://pantsu.cat/upload.php\?output\=html                                                                 ~
    <a href="https://i.pantsu.cat/mlmwnj.gif">https://i.pantsu.cat/mlmwnj.gif</a><br> 

Gyazo response 
--------------
::

    curl -sS -F "files[]=@48_circles.gif" https://pantsu.cat/upload.php\?output\=gyazo                                                                    ~
    https://i.pantsu.cat/azfyrf.gif    
