---
layout: post
tags: debian linux network
title: Example network config for debian
---
{% highlight bash %}
#/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
allow-hotplug eth0
#iface eth0 inet dhcp
iface eth0 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    gateway 192.168.1.254

#Add another IP address to eth0
auto eth0:101
allow-hotplug eth0:101
iface eth0:101 inet static
    address 192.168.0.101
    netmask 255.255.255.0
{% endhighlight %}
