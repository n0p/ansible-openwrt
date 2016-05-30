ansible-openwrt
===============

Configure your [openwrt] system (and variants, cerowrt in my case) using
[ansible].

Works with the official raw module und some custom modules to avoid
having to run python on the target - no extra dependencies for your
embedded target system.

Currently under development. I have a way to set uci values if needed
and run commit at the end if anything changed. I am trying to at least
build a superset of the [config-cerowrt.sh] shell script plus whatever
i will need myself.

Be careful with blindly running it, if you connect to your openwrt via
wifi and you change network settings you may lock yourself out.

See `host_vars/example-gw.home.lan` for how to override the role
defaults in your local clone.


Installation (roles dependencies)
---------------------------------

This is a fork of the original lefant's playbook and I switched to git
submodules simply because I prefer using git rather than installing 
another tool. Also this simplifies the playbook IMHO

To automatically retrieve dependencies:

    cd ansible-openwrt
    git submodule init
    git submodule update


Contributors
------------

Fabian Linzberger ([lefant on github]) did create the original playbook

Jan Wagner ([waja on github]) pointed out that the uci module needs to
return json and contributed related fixes allowing it to work with
recent versions of ansible.


TODO
----
- port official opkg module to shellscript or raw
- how to manage /etc/dropbear_authorized_keys? port file to sh?

[openwrt]: https://openwrt.org/
[ansible]: http://www.ansible.com/
[config-cerowrt.sh]: https://github.com/richb-hanover/CeroWrtScripts/blob/master/config-cerowrt.sh
[waha on github]: https://github.com/waja
[lefant on github]: https://github.com/lefant
