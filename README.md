runapache
=========

Small shell script to run Apache HTTP server on the foreground without
root privileges. I use it on some PHP projects, but there is nothing
specific to PHP. I didn't want to add virtualhosts, reload apache, edit
configurations for each project. I just wanted to enter a directory,
start a simple http server and jump into coding. I wanted to be able to
run PHP & Apache just like running "./manage.py runserver".

Well, PHP 5.4 built-in webserver didn't work quite well for some
projects that I was working on. So I decided to use something that
always works with PHP: Apache! Besides, my main development OS (which is
OS X Mountain Lion) has already Apache and PHP installed, I didn't have
to install anything.


Install
-------

Copy the script somewhere in your PATH. 


Usage
-----

    $ runapache

That's it! Apache will publish current working directory at 127.0.0.1:8080.

There are some useful command line parameters:

    -d DIR          specify the directory to be published (aka DocumentRoot), default is current working directory
    -l [ADDR]:PORT  listen addr and port, default is 127.0.0.1:8080
    -b DIRECTIVE    add apache directive before the default configuration
    -B FILE         add apache conf file before the default configuration
    -a DIRECTIVE    add apache directive after the default configuration
    -A FILE         add apache conf file after the default configuration


For example, If you want to use PHP installed via brew, you can run:

    $ runapache -b "LoadModule php5_module /usr/local/opt/php54/libexec/apache2/libphp5.so"
