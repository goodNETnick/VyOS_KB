Scrapli 
=======

`scrapli <https://carlmontanari.github.io/scrapli/>`_ -- scrap(e c)li -- is a python library focused on connecting to devices, 
specifically network devices (routers/switches/firewalls/etc.) via SSH or Telnet.

Supports both synchronous and asynchronous usage.

If multiple devices need to be accessed at the same time, there are some ways 
to speed up the execution of the tasks. It is possible to use 
multiprocessing, multithreading or asynchronous programming.
Since it is very often necessary to wait for I/O when polling 
network devices, it is advisable to try the asynchronous approach when 
working with a large number of devices.

With the advent of Scrapli, this is quite easy. Especially since the 
scrapli-community has support for VyOS.


