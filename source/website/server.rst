Server
======

Apache
------
Apache is a web server that is used to serve websites from a machine.

Apache is available within CentOS’s default software repositories, which means you can install it with the `yum` package manager.

Update the local Apache httpd package index to reflect the latest upstream changes:

.. code-block:: bash
    
    sudo yum update httpd

Once the packages are updated, install the Apache package:

.. code-block:: bash
    
    sudo yum install httpd

**Checking your Web Server:**

Apache does not automatically start on CentOS once the installation completes. You will need to start the Apache process manually:

.. code-block:: bash
    
    sudo systemctl start httpd

The default configuration for Apache will allow your server to host a single website. If you plan on hosting multiple domains on your server, you will need to configure virtual hosts on your Apache web server.

Configuring
-----------
Todo
