nodeapp_init
============

A basic node app startup script (thanks to start-stop-daemon).
This work is freely insipired by the following work (https://github.com/chovy/node-startup) and a script from Vincent Bernat (https://github.com/vincentbernat).

The idea, behind this script, is to have a simple, standard and reliable way to launch/stop node application as any other usual service.


How to use
----

Clone the repo to retrieve the script

	cd /tmp
	git clone https://github.com/labynocle/nodeapp_init.git
	cd nodeapp_init

Adapt the script to your environment

	NODE_APP_NAME='my_app'
	mv nodeapp_init $NODE_APP_NAME
	sed -i -e "s/__NODE_APP_NAME__/$NODE_APP_NAME/g" $NODE_APP_NAME

	vim $NODE_APP_NAME
	# and adapt the mandatory variables (directory, app, user, port, environment...)
	
	cp $NODE_APP_NAME /etc/init.d/

Note that by default the log file is /var/log/$NODE_APP_NAME/$NODE_APP_NAME.log and if the directory doesn't exist, it will be automatically created and chowned to $NODE_USER.

Now the following commands will be avalaible:

	/etc/init.d/$NODE_APP_NAME start
	/etc/init.d/$NODE_APP_NAME status
	/etc/init.d/$NODE_APP_NAME restart
	/etc/init.d/$NODE_APP_NAME stop

Add the script to the default runlevels

	update-rc.d $NODE_APP_NAME defaults


LICENSE
----

(The MIT License)
