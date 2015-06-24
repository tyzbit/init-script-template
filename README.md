System V init script template
=============================

A simple template for init scripts that provide the start, stop,
restart and status commands.

Handy for [Node.js](http://http://nodejs.org/) apps and everything
else that runs itself.

NOTE: this will only work on Debian-based distributions like Ubuntu, by design.  The reason for this is the start-stop-daemon handles running processes as another user better than sudo (especially Node.js applications).

Getting started
---------------

Copy _template_ to /etc/init.d and rename it to something
meaningful. Then edit the script and enter that name after _Provides:_
(between _### BEGIN INIT INFO_ and _### END INIT INFO_).

Now set the following three variables in the script:

### dir ###

The working directory of your process.

### user ###

The user that should execute the command.

### cmd ###

The command line to start the process.

Here's an example for an app called
[algorithms](http://algorithms.ubercode.de):

    dir="/var/apps/algorithms"
    user="node"
    cmd="node server.js"

Script usage
------------

### Start ###

Starts the app.

    /etc/init.d/algorithms start

### Stop ###

Stops the app.

    /etc/init.d/algorithms stop

### Restart ###

Restarts the app.

    /etc/init.d/algorithms restart

### Status ###

Tells you whether the app is running. Exits with _0_ if it is and _1_
otherwise.

    /etc/init.d/algorithms status

Logging
-------

By default, standard output goes to _/var/log/scriptname.log_ and
error output to _/var/log/scriptname.err_. If you're not happy with
that, change the variables `stdout_log` and `stderr_log`.

License
-------

Copyright (C) 2012-2014 Felix H. Dahlke

This is open source software, licensed under the MIT License. See the
file LICENSE for details.
