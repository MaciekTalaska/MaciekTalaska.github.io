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
Back in the days, when I was still using mainly Windows - I have been pretty happy user of Acronis TrueImage. It allowed me not only to create backup images, but also retrieve single files if needed. Acronis True Image is not available for Linux so I had to find replacement for it.

Images are convenient when playing with RaspberryPi - I do not want to spend extra time re-installing everything after making a mistake, or after trying out something new.

# Creating an image

I have spent some time looking for exact replacement for Acronis TrueImage, but in the end I have realized that the best tool is plain and simple `dd` command. It is capable of creating exact bit-to-bit copy of a block device, and recover this copy later. This small utility plus couple of others are perfectly capable of doing everything their commercial big-brother is offering.

Even though `dd` is small it offers a lot of options. One of the most important is `bs` which specifies the size of the block (in bytes) to be copied at once. If you care about the perfomance this is the option to fiddle with. After reading [great article on tuning dd block size](http://blog.tdg5.com/tuning-dd-block-size/) I use `bs=1024k`. Other options that I encourage to use is tracking progress with `status=progress`.

So, I usually use `dd` as follows: `sudo dd if=<source> of=<destination> bs=1024k status=progress`

# Protecting Image (recovery data)

Having partition/disk image is one thing, but being able to recover data from it at any time is completely different task. The worst thing that could happen is file being damaged (for example due to [bit rot/data degradation](https://en.wikipedia.org/wiki/Data_degradation)). How could we prevent it? Store the image in several places (different drives, cloud storage)... But the data could still be damaged.

## Checking image integrity

It is very important to check file integrity of the image befor deciding to recover data from it. It is especially crucial when recovering system partition (damaged image may result in system non-functioning correctly after being restored). Data integrity check is based on using one of the hashing algorightms (MD5, SHA1, SHA2 or others) and compute so called 'checksum' for the data. To be able to verify data integrity later on, first it has to be calculated for the newly created image file: 

`sha224sum inputimage.img > inputimage.img.sha224`

Having the checksum saved, checking if file has not changed is very easy:

`sha224sum -c inputimage.img.sha224`

You may also want to use MD5 instead of SHA. MD5 seem to be almost twice as fast as SHA2, but AFAIK SHA2 seem to be more reliable when it comes to possibility of collisions happening.

***Please note:*** that there are couple of versions of `shaXYZsum` tool available, for the full list and description of difference please have a look at [Wikipedia page on SHA-2](https://en.wikipedia.org/wiki/SHA-2a) and [discussion on StackOverflow](https://stackoverflow.com/questions/10061532/why-chose-sha512-over-sha384).

## Working with recovery files 

Checking file integrity is super important, but what to do if we know that file has changed? Another tool - excellent [par2/parchive tool](https://en.wikipedia.org/wiki/Parchive) has been designed to repair the damaged file(s). This is pretty popular solution and tools are available for Linux, OSX and Windows.

In short: par2 creates additional files that contain "recovery" data that will be used in case file is altered. Similarly to the checksum, to be able to repair the data, it is required to calculate "recovery data" after the image has been created.

Creating par2 files:

`par2 c -r15 <inputfile>` 
Options explained:
- c - is shortcut for 'create' (there is also possibility to call an alias: `par2create`)
- r15 - specifies that par2 should create files taking 15% total of the original file size. That means that roughly 15% data could be damaged, and par2 will still be able to repair the file.

Verification:

`par2 v <inputfile>` or `par2verify <inputfile>`

***Please note:*** in some recent versions of par2 there seem to be a performance bug when checking altered file. Instead of getting quick info that the file is broken it takes long time and no output is given to the user. Until this is solved I recommend using `cfv` which is capable of checking integrity of files that have .par2 generated for them. By default `cfv` works in "verify" mode, so checking if file has not been damaged is as simple as `cfv <filename>` - this will pick all the .par2 files created for this file, and verify if any modifications to the file happened since .par2 files creation.


Repairing damaged file:

`par2 r <inputimage>` or `par2repair <inputimage>`

Depending on the disk speed, image size and the CPU it may take several hours to get multi-GB file repaired. After the process is complete file is being checked again (verified) - just to make sure all is well.

# Creating & using multi-partition image(s)

Great thing about `dd` is its capability of creating image not only of the single partition but the whole drive (containing multiple partitions). That is especially important in case of buying new disk and trying to copy all the data (possibly many OSes) to a new drive (and not using direct drive clone for some reason).

Creating multi-parition image is the same as creating image of single partition - instead of specifying particular partition as a source the block device has to be sepcified: 

`sudo dd if=/dev/sda of=<imagename>` instead of `sudo dd if=dev/sda1 of=<imagename>`

# Recovering data

Data recovery using `dd` is simple, it is the matter of reversing the source and destination (image becomes source, and partition becomes destination):

`sudo dd if=<image> of=<partition> bs=1024k status=progress`

## Recovering whole partition/disk at once

Similarly to restoring content of the single partition it is possible to recover content of the whole drive (assuming image was created of the whole drive, not a single partition). 

## Mounting disk image

One of the most important things is ability to mount disk image, so that it is possible to copy file(s) from it, as conveniently as if it was another regular drive/partition.

Mounting single partition image: `sudo mount <image> /folder -o loop,ro,noatime`

Options explained:
- loop - required to mount an image as a block device
- ro - mount image in read-only mode - this should be sufficient to make sure no accidental changes are made to the content of the image (and no `noatime` should be required), but it happened to me several times that even though I have explicitly used `ro`, `atime` was updated (which led to disk image being changed... so data verification failed)
- noatime - that one is important - it means **do not modify files/folders access time**. I think it is pretty rare for someone to rely on access time for any purpose,  but more importantly: allowing `mount` to modify access times means **changing the image file** so checking the file integrity of the image **will fail**.

Mounting paritition from a multi-partition disk requires one additional step - enlisting all partitions as a loop device:

`sudo losetup -Pf disk.img`

after this is done, it is possible to mount parition (for example /dev/loop0p1):

`sudo mount /dev/loop0p1 <mount_folder>`

To check if image contains single partition or multiple partitions use `fdisk`:

`fdisk -lu <imagefile>`

## Recovering data with `cp` or `rsync`

Copying disk image content to partition has some drawback - this needs to touch each and single sector (or cell in case of SSD) of the disk. This may result in extra disk wear for SSDs. Sometimes it is enough to copy data from such an image to the destination partition. This seem to be super easy with data, but what to do in case of system partition (Linux)?

In such a case it is best to use `rsync`:

`rsync -axHAWXS --numeric-ids --info=progress2 <source> <destination>` 

In case you need explanation: [whole thread on SuperUser.com](https://superuser.com/questions/307541/copy-entire-file-system-hierarchy-from-one-drive-to-another)

# Summary

This post presents how to build your workflow using small utilities, and not rely on one big application. This approach is inspired by ["The Unix way"/Unix philosophy](https://en.wikipedia.org/wiki/Unix_philosophy) - i.e. creating small utilities capable of solving one problem very well, have bunch of such tools and build on top of them.

All utilities mentioned are pretty much standard tools & should be available in your distribution's repository (I am not sure if/how many are available for OSX).
