WordPress Backup Ant Script
===========================

This is a simple Ant script to make backups of a WordPress blog in a remote machine.

Basically, it will connect to your server, make a copy of the WordPress directory, make a dump of the MySql database, zip everything, and then download the resulting file. The final zip is named with the timestamp, so you can easily find backups latter.

I wrote it to automate remote backups of [my own blog](http://leonardofischer.com/). It runs on a Linux server, but I would like to save the backups in a external machine running Windows.


Pre-Requisites
--------------

- Your server must run a Linux distribution;
- The local machine where you will execute the WordPress Backup Ant Script may be a Windows, Linux, or anything else that runs [Ant](http://ant.apache.org/ "Apache Ant");
- The server must be support SSH using key files (Google for [Setting up SSH keys](http://www.google.com/search?q=Setting+up+SSH+keys "Setting up SSH keys") if you're not sure how to do it).


Installation
------------

- Install [Ant](http://ant.apache.org/ "Apache Ant") on your local machine. It was tested with the [version 1.8.4](http://archive.apache.org/dist/ant/binaries/apache-ant-1.8.4-bin.zip "Apache Ant 1.8.4"), but any version above 1.8 should work. The location where Ant is installed will be called $ANT_HOME from now on;
- Download the [JSch jar](http://www.jcraft.com/jsch/index.html "JSch - Java Secure Channel") and save it on the $ANT_HOME/lib directory. Is was tested with the [JSch version 0.1.48](http://sourceforge.net/projects/jsch/files/jsch.jar/0.1.48/jsch-0.1.48.jar/download "Download JSch version 0.1.48");
- [Download this script](https://github.com/lgfischer/wordpress-backup-ant-script/zipball/master "Download WordPress Backup Ant Script") and paste it anywhere on your local machine.


Configuration
-------------

All the configuration you need to do is on the *backup.properties* file. Please open it, and complete each value with your server configuration.

Some of these values are optional, and you may leave then commented (with the # at the beginning of the line).

You don't need to keep the name *backup.properties*, change the file name as you like. For example, if you have several blogs that you want to backup, you may create one file for each blog, with names "your_blog.properties". You can also save it on a directory different than the one that you saved the build.xml file. Just take note of the name and the path to use latter.


Execution
---------

Open your terminal/console window, go to the directory where you saved the build.xml script and type

	ant backup

If you renamed or moved the backup.properties file, replace it in the line above. If the path to your properties file has spaces, write it with quotation marks *"*, like this:

	ant backup -Dproperties="/path/to/your properties directory/your.properties"

Download
--------

[Download WordPress Backup Ant Script as a zip file](https://github.com/lgfischer/wordpress-backup-ant-script/zipball/master "Download WordPress Backup Ant Script")


TODOs
-----

Installation:
- Remove the need to manually download JSch by adding the .jar on a "lib" directory and referencing it on the build.xml file.

Configuration:
- Add support for an password interactive based login (for those that don't know how to set key files). This **should not** allow the user to write the password on the build.xml or on the .properties file (as it is easy to let anyone copy the password);
- Make the default value of the db.address equals to the server.host if not present.
