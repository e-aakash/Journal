Let's Encrypt
=====

Setup
----
We'll use the automatic certificate renewal bot from `LetsEncypt <https://letsencrypt.org/>`_. Download the certbot tool from the `official website <https://certbot.eff.org/>`_. For CentOS use `this link <https://certbot.eff.org/#centos6-apache>`_. 

Follow the instructions given on that `website <https://certbot.eff.org/#centos6-apache>`_.


Usage
----
To use the certbot, simply open the directory where you've downloaded the certbot-auto script and execute it using ``sudo ./certbot-auto``

It would bring up an interactive interface allowing you to choose which domain you want to set up an SSL certificate for.



.. code-block:: linux

	Which names would you like to activate HTTPS for?
	-------------------------------------------------------------------------------
	1: iusms.in
	2: www.iusms.in
	3: wncc-iitb.org
	4: dsd.wncc-iitb.org
	5: www.dsd.wncc-iitb.org
	6: hooks.wncc-iitb.org
	7: www.hooks.wncc-iitb.org
	8: journal.wncc-iitb.org
	9: www.journal.wncc-iitb.org
	10: lendit.wncc-iitb.org
	11: noticeboard.wncc-iitb.org
	12: www.noticeboard.wncc-iitb.org
	13: portals.wncc-iitb.org
	14: www.portals.wncc-iitb.org
	15: resources.wncc-iitb.org
	16: www.resources.wncc-iitb.org
	17: www.wncc-iitb.org
	-------------------------------------------------------------------------------
	Select the appropriate numbers separated by commas and/or spaces, or leave input
	blank to select all options shown (Enter 'c' to cancel):


Select the options, and wait for the certbot to do its magic.


Renew
----
To renew the certificates, simply run ``sudo ./certbot-auto renew``. The certbot will do it's thing. 

This can be set as a cronjob to run `every month <https://crontab.guru/every-month>`_.

To open the crontab for the root user, type in ``sudo crontab -e``. This would open up the crontab in vim. Insert the following line:

``0 0 1 * * /home/nihal/certbot-auto renew``


Debugging
----

**Change not reflecting** --- If you've made a change in the ``/etc/httpd/conf/httpd.conf`` file, it may not reflect in the https configuration that gets set in ``/etc/httpd/conf/httpd-le-ssl.conf``, even on attempting to create a new certificate. The solution is to edit the https configuration file manually.

**Certbot error** --- The certbot occassionaly gives an error saying that it has created the certificate but was unable to add it to apache config. To fix this open ``/etc/httpd/conf/httpd-le-ssl.conf`` yourself, look at a similar previous example website that has it's config defined. Replicate the config, making changes wherever needed. Run the certbot again. There is a good chance that it would set up the config correctly now. If not, happy debugging!

