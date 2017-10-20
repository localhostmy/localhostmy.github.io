---
title: Creating Linux Debian bootable USB
layout: content
date: '2011-04-13 00:00:00'
categories: blogs
---

#apt-get install mtools

#apt-get install syslinux

#apt-get install dosfstools

#modprobe usb-storage

#fdisk -l /dev/sda

#mkdosfs -I /dev/sda

#syslinux /dev/sda

#wget http://http.us.debian.org/debian/dists/stable/main/installer-i386/current/images/hd-media/boot.img.gz

#zcat boot.img.gz > /dev/sda

#mount /dev/sda /tmp

1. Download the netinst (Net Install) ISO image of size 150-180MB from <a href="http://www.debian.org/CD/netinst/#netinst-stable">here.</a>
or
2. Download the businesscard image of size 40 MB from <a href="http://www.debian.org/CD/netinst/#businesscard-stable">here.</a>

#cp <image.iso> /mnt
#umount /mnt

Regards
Amir Haris Ahmad
amir@localhost.my