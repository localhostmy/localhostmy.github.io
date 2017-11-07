---
title: "[DNSSEC] The simplest way to integrate the Alea I with dnssec-keygen"
layout: content
date: '2011-02-08 00:00:00'
categories: BLOG
---

<img classs="img-fluid center" src="/assets/images/post/dnssec-keygen.jpg"/>

The simplest way to integrate the Alea I with dnssec-keygen is to use the "randomfile" program which is provided as C source on the Alea I driver CD, and pipe its output into the standard input of the dnssec-keygen program. For example, this command will generate a 2048-bit RSA zone key for the "my" TLD:



sudo randomfile -b | dnssec-keygen -r /dev/fd/0 -a RSASHA1 -b 2048 my.



Here, the "-b" causes the randomfile program to output the randomness in binary form (which is what dnssec-keygen expects), and the "-r /dev/fd/0" causes dnssec-keygen to read randomness from standard input instead of /dev/random. Note that the randomfile program needs to be run as root unless you set up specific udev rules to give non-root users permission to access the Alea I USB device.



amir@localhost.my