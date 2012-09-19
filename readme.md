WordPress Backup Ant Script
===========================

This is a simple Ant script to make backups of a WordPress blog in a remote machine (possibly running Windows).

Basically, it will connect to your server, make a copy of the WordPress directory, make a dump of the MySql database, zip everything, then download the resulting file. The final zip is named with the timestamp, so you can easily find backups latter.


Pre-Requisites
--------------

- Your server must run a Linux distribution;
- The local machine where you will execute the WordPress Backup Ant Script may be a Windows, Linux, or anything else that runs [Ant](http://ant.apache.org/ "Apache Ant");
- The server must be support SSH using key files (Google for [Setting up SSH keys](http://www.google.com/search?q=Setting+up+SSH+keys "Setting up SSH keys") if you're not sure how to do it).


Installation
------------

- Install [Ant](http://ant.apache.org/ "Apache Ant") on your local machine. It was tested with the version 1.8.4, but any version above 1.8 should work. The location where Ant is installed will be called $ANT_HOME from now on;
- Download the [JSch jar](http://www.jcraft.com/jsch/index.html "JSch - Java Secure Channel") and save it on the $ANT_HOME/lib directory. Is was tested with the [JSch version 0.1.48](http://sourceforge.net/projects/jsch/files/jsch.jar/0.1.48/jsch-0.1.48.jar/download "Download JSch version 0.1.48");
- Download this script and paste it anywhere on your local machine.


Configuration
-------------

All the configuration you need to do is on the *example.properties* file. Please open it, and complete each value with your server configuration.

Some of these values are optional, and you may leave then commented (with the # at the begining of the line).

You don't need to keep the name *example.properties*, change the file name as you like. You can also save it on a directory different than the one that you saved the build.xml file. Just take note of the name and the path to use latter.

Execution
---------

Open your terminal/console window, go to the directory where you saved the build.xml script and type

	ant -Dproperties=example.properties

If you renamed or moved the example.properties file, replace it in the line above. If the path to your properties file has spaces, write it with quotation marks *"*, like this:

	ant -Dproperties="/path/to/your properties directory/your.properties"

Download
--------
