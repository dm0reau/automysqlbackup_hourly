automysqlbackup_hourly
======================

This script is an extension of [automysqlbackup](https://sourceforge.net/projects/automysqlbackup/),
to support hourly backups of MySQL databases.

Compatibility
-------------

Debian and Ubuntu only. Tested on production servers with Debian 8 (Jessie) and Ubuntu 14.04.

Installation
------------

First, automysqlbackup *must* be installed :
<pre><code>sudo apt-get install automysqlbackup</code></pre>
The automysqlbackup_hourly script can be copied or linked into /etc/cron.hourly/ : 
<pre><code>sudo ln -s automysqlbackup_hourly /etc/cron.hourly/</code></pre>
For testing it, just launch as root : 
<pre><code>./automysqlbackup_hourly</code></pre>
Then, in your backup's directory, you will see :
<pre><code>hourly daily weekly monthly</code></pre>

Every hour, you'll have a new dump for each database in hourly directory.

How it works
------------

Every hour, it takes the last dump present in your daily or weekly directory
(depending on the day given by DOWEEKLY parameter), and move it to the
hourly/yourdb directory. Then, it launches the automysqlbackup script to
create a new dump in daily or weekly directory.
Finally, dumps older than 7 days in hourly directory are deleted. You can
change the number of days by changing ROTATION_DAYS variable, at the beginning
of the script.
