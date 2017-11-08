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
size         File size in bytes
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

## Upload API endpoint:
/upload.php


## POST arguments:
files[]: 

**Content-Type:** multipart/form-data

File to upload; multiple values supported.


## GET arguments:
###	output:
#### gyazo:
**Content-Type:** text/plain

Complete URLs to uploaded files in the same order as the input files, separated by newlines. Does not have a trailing newline (Pomf1 compat version).

**Example output:**
```txt
'https://example.com/foobar.jpg\nhttps://example.com/qweasd.txt'
```

#### text:
**Content-Type:** text/plain

Complete URLs to uploaded files in the same order as input files. Each line ends in a newline (Unix style).

**Example output:**
```txt
'https://example.com/foobar.jpg\nhttps://example.com/qweasd.txt\n'
```
Protip: if you include input names of uploaded files, how do you handle e.g. newlines in filenames?

#### html:
**Content-Type:** text/html

A HTML page containing links to uploaded files. Can be anything and is primarily meant to be shown to a human user.

**Example output:**
```html
'<a href="https://example.com/foobar.jpg">https://example.com/foobar.jpg</a><br /><a href="https://example.com/qweasd.txt">https://example.com/qweasd.txt</a><br />'
```
