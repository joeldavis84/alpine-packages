# hitch SSL Termination Daemon

This is as basic of an install as I could. Hitch has some idiosyncrasies that I've also tried to iron out so that the package behaves how many installing might assume it will:

* There is no default configuration file. Hitch requires the invoking user to either specify one on the command line or for  all configuration be provided on the command line. I've created a default configuration file and a system service for starting it up. This is more in line with daemons such as nginx or httpd with which users are more likely to be familiar with and will likely expect hitch to function similarly. I've placed the default configuration file in an easy to discover place that includes the package name ("/etc/hitch").

* The default compile also doesn't really allow one to just _run_ it and get some level of reduced functionality (such as httpd or nginx which install to landing pages). For example, an SSL certificate is required but none provided. This package generates a new self-signed certificate at install-time and places in the same directory as the default configuration. The default configuration will already be pointing to this certificate so all that should be required is simply starting the system service to get the hitch part of their web stack going.
