# Description

csolo is the first piece in the puzzle which I like to call my personal configuration management. It's essentially nothing more than a glorified wrapper of chef-solo.

# Usage

Currently, everything is hard-coded (while developing). Edit the variables in the script to suit your needs.

~~~ sh
$ csolo personal
~~~

This will execute `chef-solo` with the rules file in `$HOME/.chef/solo.json`. For me, this currently points to a cookbook which manages personal stuff, like creating directories that I am used to work with.

~~~ sh
$ csolo system
~~~

This will invoke `chef-solo` with the rules file in `$HOME/.chef/solo.system.json`. It will run using `sudo`, because this rules file makes sure that the software packages that I rely on are installed.

If no argument is provided, `csolo` will run as `csolo personal`.
