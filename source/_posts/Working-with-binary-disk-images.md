---
layout: draft
title: Working with binary disk images
date: 2019-11-20 11:55:28
categories:
- setup
tags:
- dd
- par2
- sha2
- backup
---

# The need for creating images

I was always trying to make sure that if something happens to my OS I am able to quickly recover it, and start working where I left of. One thing is making data backups, the other important aspect is to make sure I have an up to date copy of my system partition stored on a separate drive somewhere.
Back in the days, when I was still using mainly Windows - I have been pretty happy user of Acronis TrueImage. It allowed me not only to create backup images, but also retrieve single files if needed. Acronis True Image is not available for Linux so I had to find another way.

Images are also pretty important when playing with my RaspberryPi - I do not want to spend extra time re-installing everything after making a mistake, or trying out something new.

# Creating an image

The first thing that comes to mind is to look for a direct replacement of Acronis TrueImage, but it seems to me that the best tool one may use is plain and simple `dd` command. It is capable of creating exact bit-to-bit copy of a block device, and recover this copy later.

After reading [great article on tuning dd block size](http://blog.tdg5.com/tuning-dd-block-size/) I use `bs=1024k` which seem to be pretty good in terms of performance. Other options that I encourage to use is tracking progress `status=progress`.

So, I usually use `dd` as follows: `sudo dd if=<source> of=<destination> bs=1024k status=progress`

# Protecting Image (recovery data)

Having partition/disk image is one thing, but being able to recover data from it at any time is completely different problem. The worst thing that could happen is file being damaged. How could we prevent it? Store the image in several places (different drives, cloud storage)... But that still does not make it much more safe.

## Checking image integrity

The very first thing, before using the image, is checking the file integrity. This could be done by simple computing hash for the image file:

`sha224sum inputimage.img > inputimage.img.sha224`

checking if file has not changed is very easy:

`sha224sum -c inputimage.img.sha224`

You may also want to use MD5 instead of SHA. MD5 seem to be almost twice as fast as SHA2, but AFAIK SHA2 seem to be more reliable when it comes to possibility of collisions happening.

***Please note:*** that there are couple of versions of `shaXYZsum` tool available, for the full list and description of difference please have a look at [Wikipedia page on SHA-2](https://en.wikipedia.org/wiki/SHA-2a) and [discussion on StackOverflow](https://stackoverflow.com/questions/10061532/why-chose-sha512-over-sha384).

## Working with recovery files 

Checking file integrity is super important, but what to do if we know that file has changed? In this case we may use excellent [par2/parchive tool](https://en.wikipedia.org/wiki/Parchive) to repair the damaged file. This is pretty popular solution and tools are available for Linux, OSX and Windows.

In short: par2 creates additional files that contain "recovery" data that will be used in case file is altered.

Creating par2 files:

`par2 c -r15 <inputfile>` where "r15" specifies that par2 should create files taking 15% total of the original file size. That means that roughly 15% data could be damaged, and par2 will still be able to repair the file.

Verification:

`par2 v <inputfile>`

***Please note:*** in some recent versions of par2 there seem to be a performance bug when checking altered file. Instead of getting quick info that the file is broken it takes long time and no output is given to the user. Until this is solved I recommend using `cfv` which is capable of checking integrity of files that have .par2 generated for them. By default `cfv` works in "verify" mode, so checking if file has not been damaged is as simple as `cfv <filename>` - this will pick all the .par2 files created for this file, and verify if any modifications to the file happened since .par2 files creation.


Repairing damaged file:

`par2 r <inputimage>`

Depending on the disk speed, image size and the CPU it may take several hours to get multi-GB file repaired. After the process is complete file is being checked again (verified) - just to make sure all is well.

# Creating & using multi-partition image(s)

Great thing about `dd` is its capability of creating image not only of the single partition but the whole drive (multiple partitions). That is especially important in case of buying new disk and trying to copy all the data (possibly many OSes) to a new drive.

Creating multi-parition image is the same, just instead of specifying particular partition as a source - provide the block device itself (so instead of `dev/sda1` just type `/dev/sda`).

# Recovering data

Data recovery using `dd` is simple, it is the matter of reversing the source and destination (so image becomes source, and partition becomes destination):

`sudo dd if=<image> of=<partition> bs=1024k status=progress`

## Recovering whole partition/disk at once

Similarly to restoring content of the single partition it is possible to recover content of the whole drive (assuming image was created of the whole drive, not a single partition). 

## Mounting disk image

One of the most important thing is ability to mount disk image, so that it is possible to copy file(s) from it, exactly the same as if it was another drive/partition.

Mounting single: `sudo mount <image> /folder -o loop,ro,noatime`

Important things to mention:
- loop - required to mount an image as a block device
- ro - mount image in read-only mode - this should be sufficient and no `noatime` should be required, but it happened to me several times that even though `ro` was specified, atime was still updated (which led to disk image being changed...)
- noatime - that one is very important - it means we **do not want to modify files/folders access time**. First: I have never seen a need to rely on access time for any purpose, and second: allowing mount to modify access times means **changing the image itself** so checking the file integrity of the image **will fail**.

Mounting paritition from a multi-partition disk requires one additional step - enlisting all partitions as a loop device:

`sudo losetup -Pf disk.img`

after this is done, it is possible to mount parition (for example /dev/loop0p1):

`sudo mount /dev/loop0p1 /mnt/loop0p1`

## Recovering data with `cp` or `rsync`

Copying disk image content to partition has some drawback - this needs to touch each and single sector (or cell in case of SSD) of the disk. This may result in extra disk wear for SSDs. Sometimes it is enough to copy data from such an image to the destination partition. This seem to be super easy with data, but what to do in case of system partition (Linux)?

In such a case it is best to use `rsync` as follows:

`rsync -axHAWXS --numeric-ids --info=progress2 <source> <destination>` 

In case you need explanation: [whole thread on SuperUser.com](https://superuser.com/questions/307541/copy-entire-file-system-hierarchy-from-one-drive-to-another)

# Summary

So instead one huge app, there were several tiny utilities mentioned in this blog post. And this is in line with the "Unix way" - create something small, that works and is capable of performing one taks very well. Then build your workflow out of many small utilities. 
