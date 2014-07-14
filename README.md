goagent-startup
============

An /etc/init.d script for running goagent, inspired from [node-startup](http://github.com/chovy/node-startup).

Why goagent-startup?
----

This script can be used in /etc/init.d/goagent which will allow rc.d to start your goagent when the machine boots.
If you are live in China, use Linux and goagent, you want to add this to your default run-level.

Installation
----

Clone the repo

	git clone https://github.com/ethrea1/goagent-startup.git
	cd goagent-startup/init.d

Edit the goagent script with your settings for python path, path to application directory (where your goagent source is), and a path to a pid file.

	vi goagent

	GOAGENT_DIR='/path/to/goagent-goagent-fd5235f'
	PID_FILE=$GOAGENT_DIR/goagent.pid
	LOG_FILE=$GOAGENT_DIR/goagent.log
	PYTHON_EXEC=`which python`

By default, it expects the pid file to be in /path/to/goagent-goagent-fd5235f/goagent.pid and your log file to be in /path/to/goagent-goagent-fd5235f/goagent.log

Copy the startup script goagent to your /etc/init.d directory

	sudo bash -l
	cp ./init.d/goagent /etc/init.d/


Test that it all works:

	service goagent start
	service goagent status
	service goagent restart
	service goagent stop

Add goagent to the default runlevels

	update-rc.d goagent defaults

Finally, reboot to be sure app starts automatically

	reboot

Supported OS
----

Tested with Ubuntu 14.04, but it should work on other Linux systems that use startup scripts in /etc/init.d (CentOS, Debian, Gentoo, Redhat, etc).


LICENSE
----

(The MIT License)
