Time
====

Configure timezone
------------------
Run ``date`` to see what time and timezone is set.

To set timezone to IST, do the following-

.. code-block:: bash

	rm -rf /etc/localtime
	ln -s /usr/share/zoneinfo/Asia/Kolkata /etc/localtime

Next, we want to write the system time info into the hardware clock.

Open up the hardware clock config- ``vi /etc/sysconfig/clock``, and write the below lines into the file.

.. code-block:: bash

	ZONE="Asia/Shanghai"
	UTC=false
	ARC=false

Save and quit. Run ``hwclock --systohc --localtime``. 

Check if the change has reflected, by running ``hwclock``.

Enable NTP
----------
To enable NTP to automatically update the time, follow the below steps-

.. code-block:: bash

	yum install ntp
	sudo chkconfig ntpd on
	sudo ntpdate pool.ntp.org
	sudo service ntpd start

