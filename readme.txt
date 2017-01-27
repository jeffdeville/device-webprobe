This is a web interface to the SunSpec core library and supporting scripts, to probe any SunSpec-conformant device on the Internet.

There are four components:

1. the web-app front end - a MEAN application with an Angular/Bootstrap front end and a node.js backend, which invokes the...

2. service - a python script that offers a REST service interface to the underlying...

3. SunSpec core - a set of python scripts that communicate with SunSpec-compliant  devices

4. device simulator - a set  of python scripts that simulate a SunSpec device, principally for testing everything else


USAGE:
------

device simulator:
-----------------
sudo python modsim.py -m tcp mbmap_test_device.xml
Logs are in /var/log/cherrypy

core:
-----
install them on the target system as a python lib.  Beats the hell out of me how to do that

service:
--------
sudo cherryd -c suns_device_service.config -i suns_device_service -d

web-app:
--------
1. be sure mongod is running.  It should be, as it is included in the /etc/init.d infrasctructure.
See /etc/init.d/mongod; config is in /etc/mongod.conf, log is in /var/log/mongod.log

2. run web-app.  The 'released' version, in /usr/local/interop-test, should be running, as it is included in the /etc/init.d infrastructure.
node server.js
server listens on port 8082
log is in /var/log/interop-test.log


PRODUCTION DEPLOYMENT:
----------------------

The package is running in production on ec2-54-70-231-31.us-west-2.compute.amazonaws.com.  It is managed in these scripts:

/etc/init.d/...

You can use the script deploy.sh to deploy updates if you check the code out on that server.

