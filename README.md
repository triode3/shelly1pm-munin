# README 
for the shelly1pm plugin for monitoring the power and temperature of a [Shelly](https://www.shelly.com/) 1PM **1st Gen** to [Munin](https://munin-monitoring.org/)

This readme is broken into a few small sections: What,  Why, How to install, How to change, License. 

# What is this thing?

This readme assumes you know what [Munin](https://munin-monitoring.org/) is all about, and that you have an "older" Shelly 1PM (gen1 maybe 2) and you would like to graph power and temperature.

Here is an exmaple output from munin monitoring power and temperature:

![screenshot of Shelly1PM](https://github.com/triode3/shelly1pm-munin/blob/main/images/shelly1pm.png)

Note that the shelly is set to come on every day around 0530-0700, and then from 1900-2145. The temperature rises due to the power through shelly and it being in a small enclosure. Also, the temperature of the unit does swing wildly because it is in an unconditioned space (this is just to point out that the large variations in temperature are expected in this particular setup). 

# Why did I make this?

I have a number of Shelly 1PM units around, and realized that you can request a URL and receive a jspn formatted output of the status of the unit. That status includes the current power utilization of the device and the temperature reading that it has in the internal sensor of the unit. Given that, this plugin is really a (bad, probably) hack job of grabbing those two fields from the json output using (mostly) built in tools in linux. 

# How to install it.

It is a plugin just like any munin plugin, so you need to do the following:

First, we need to add your username and password for the shelly1pm, so

- edit shelly1pm and change username:password in the URL to your own setup
- If yo do not have a username and password, delete username:password from the URL.
- place the shelly1pm file into /usr/share/munin/plugins (or if you moved it, the munin plugin dir)
- create a link from /etc/munin/plugins/shelly1pm to /usr/share/munin/plugins/shelly1pm
- restart munin-node
- restart munin (if you want to). 

Again, if you moved munins plugins dir, change the links to relect this. 

# How to change it, etc. 

**NOTE** The plugin relies on jq, which is "noramlly" installed in most distributions of linux out of the box, but not all (for example, on my gentoo box, it was not a default package). You may need to install it, so check if jq is present first. The program curl is also installed, but I do not know many distributions that do not have that pre-installed. 

**NOTE** The temperature is output in F, if you want that in C, just read the note in the plugin and change '2 p' to '1 p' in the plugin. 

# LICENSE

GNU GENERAL PUBLIC LICENSE (see LICENSE.md)

A copy of the GPL3 is included with this software. (see gpl-3.0.txt)




