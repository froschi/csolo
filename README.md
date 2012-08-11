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

# Roadmap

I have two goals for `csolo`.

First, I want to be able to use it to bootstrap my setup on a new Ubuntu workstation. For that, I will implement an `init` argument, which sets up and downloads the minimal set of dependencies "by hand", using calls to `apt-get` and such. I imagine the workflow for that to look something like this:

~~~ sh
$ mkdir -p $HOME/scm/code
$ cd HOME/scm/code
$ git clone git://github.com/froschi/csolo.git
$ csolo/csolo init
$ csolo/csolo system
$ csolo/csolo personal
~~~

Then I want to be able to switch to the maintenance phase, which would just consist of calls to `csolo system` or `csolo personal` after I pushed changes to any of the github repositories involved.
