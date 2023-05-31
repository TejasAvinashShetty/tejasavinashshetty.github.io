---
toc: true
layout: post
description: Setting Dropbox in AntiX linux distribution.
categories: [markdown, antix, dropbox]
title: Dropbox meets AntiX Linux
comments: true
hide: false
search_exclude: false
---
# Dropbox meets AntiX Linux
 
oK LET ME BE CLEAR. i REALLY DON'T HAVE ANY IDEA WHY ALL THESE STEPS WORK.
They worked for me so here they are.

## Acknowledgements
- [How to install Headless Dropbox on Ubuntu Server](https://www.fosslinux.com/45045/headless-dropbox-ubuntu-server.htm)
- [How to get HELP with an antiX PROBLEM](https://www.antixforum.com/forums/topic/how-to-get-help-with-an-antix-problem/)
- [How to install Dropbox and setup sync on Ubuntu](https://www.fosslinux.com/17023/how-to-install-dropbox-and-setup-sync-on-ubuntu.htm)
- [Download Dropbox linux](https://www.dropbox.com/install)
- [Dropbox . py](https://www.dropbox.com/download?dl=packages/dropbox.py)

## Install Dropbox

### Getting Dropbox
First update the package lst and ensure we are on the latest compatible version of packages  this section is paraphrased from
[How to install Dropbox and setup sync on Ubuntu](https://www.fosslinux.com/17023/how-to-install-dropbox-and-setup-sync-on-ubuntu.htm)

```bash
sudo apt update
sudo apt upgrade
```

Next, make sure that the wget package is installed on your system. If it is not installed, you can install it using the following command:

```bash
sudo apt install wget
```

It is better to get Dropbox from the oficial site rather than from debian repositories
[Download Dropbox linux](https://www.dropbox.com/install)
By command line
```bash
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
```
or by downloading the appropriate debian package 64 bit ubuntu (risky as it is actually for Ubuntu)


It will download the dropbox downloader script and extract it to your home directory. The extracted folder will be hidden 

## Start Dropbox
To start dropbox downloader , enter
```bash
~/.dropbox-dist/dropboxd
```
When the installation is completed, it will ask you to sign in in the browser.
Once you do the needful, you will get a page showing that dropbox is signed in.

Download the dropbox.py  from [Dropbox . py](https://www.dropbox.com/download?dl=packages/dropbox.py) and place it in /usr/local/bin/dropbox
```bash
sudo wget -O /usr/local/bin/dropbox "https://www.dropbox.com/download?dl=packages/dropbox.py"
```
Make script executable by 
```bash
sudo chmod +x /usr/local/bin/dropbox
```
Increase the iwatches using this command
```bash
 echo fs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf; sudo sysctl -p
```
Now one can operate Dropbox using the dropbox command. To start it
```bash
dropbox  start
```
Dropbox status
```bash
dropbox status
```
Autostart dropbox at startup
```bash
dropbox autostart
```
better to keep dropbox on initially till it syncs up fully and then prevent it from autostart as it consumes RAM

```bash

```

## more about AntiX
If this post has intrigued you about AntiX linux please see

<iframe width="560" height="315" src="https://www.youtube.com/embed/JCTaUAP6sSg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

or see [run with dolphin ](https://www.youtube.com/@runwiththedolphin)
