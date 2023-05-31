---
layout: post
title: HP Printer meets AntiX Linux
excerpt: Setting up HP Printer in AntiX linux distribution.
modified: 2/29/2016, 22:00:24
tags: [markdown, antix, printer, HP]
comments: true
category: blog

---

oK LET ME BE CLEAR. i REALLY DON'T HAVE ANY IDEA WHY ALL THESE STEPS WORK.
They worked for me so here they are.

## Acknowledgements
- [Install HP Printer drivers in Ubuntu, Linux Mint, and elementary OS : FossLinux](https://www.fosslinux.com/1547/install-hp-printer-drivers-in-ubuntu-linux-mint-and-elementary-os.htm)
- [How to get HELP with an antiX PROBLEM](https://www.antixforum.com/forums/topic/how-to-get-help-with-an-antix-problem/)
- [Unable to access CUPS or configure a printer on AntiX-19](https://www.antixforum.com/forums/topic/unable-to-access-cups-or-configure-a-printer-on-antix-19/)
- [How to Fix "Systemctl Command Not Found" Error in Linux](https://allthings.how/how-to-fix-systemctl-command-not-found-error-in-linux/)
- [Installing Printers in Linux CUPS, Printing, and Scanning - YouTube : Chris Titus](https://www.youtube.com/watch?v=En2DJAMpwmY&pp=ygUcaHAgcHJpbnRlciBub3Qgd29ya2luZyBsaW51eA%3D%3D)


CUPS and HPLIP are what we are after here.
CUPS Common Unix Printing Standard

## Getting CUPS
Type in the terminal
```bash
sudo apt-get update
sudo apt-get install cups
sudo apt-get install cups-browsed
sudo apt-get install cups-filters
sudo service cups start
```

after which you should be able to login in browser using

```html
http://localhost:631
```
## HPLIP
*It would probably be better to install HPLIP also while we are at it as no harm done.
I don't think so the system made any use of it but I may be mistaken.*
As in [Install HP Printer drivers in Ubuntu, Linux Mint, and elementary OS : FossLinux](https://www.fosslinux.com/1547/install-hp-printer-drivers-in-ubuntu-linux-mint-and-elementary-os.htm)
we 
- check if we already have HPLIP via `dpkg -l hplip` *not there*
- decided not to install HPLIP from [Get HPLIP](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip) as we have no idea of the COMPATIBILITY with our system or the distribution
- decided to go with 
 
` sudo apt update`
 
 `sudo apt upgrade`
   
 `sudo apt install hplip hplip-gui`
   
   as we felt it would be more compatible with our system


## An aside
AntiX is not a systemd distro. So, systemctl won't work in it. So tutorials such as [Installing Printers in Linux | CUPS, Printing, and Scanning - YouTube : Chris Titus](https://www.youtube.com/watch?v=En2DJAMpwmY&pp=ygUcaHAgcHJpbnRlciBub3Qgd29ya2luZyBsaW51eA%3D%3D)
won't work off the bat. We need to improvise. So we looked at [How to Fix "Systemctl Command Not Found" Error in Linux](https://allthings.how/how-to-fix-systemctl-command-not-found-error-in-linux/)
There we got the idea of replacing systemctl with service.
So we have `sudo service cups start` instead of `sudo systemctl enable cups`
and `sudo systemctl start cups`

## Continuing further
We have this page for CUPS
![image](https://github.com/TejasAvinashShetty/silvercloud/assets/27445854/98cd139d-a363-4667-84fa-36f6a7268ce4)
We then click on the highlighted area ![image](https://github.com/TejasAvinashShetty/silvercloud/assets/27445854/0406d58b-fa38-4f58-859b-5505de8546d3)
This leads us to ![image](https://github.com/TejasAvinashShetty/silvercloud/assets/27445854/63472cff-8c25-457f-a344-2144f92bb400)
If you read throughly through this you may be able to do every thing by the command line.
But at least I am not so pedantic.
Just click on the portion  encircled in red ink
![image](https://github.com/TejasAvinashShetty/silvercloud/assets/27445854/9e33f23b-7468-4c0d-8495-47283e3f7bc1)
We will get the following. Click on the **Add printer**
![image](https://github.com/TejasAvinashShetty/silvercloud/assets/27445854/05f071a3-df2b-476c-acdc-a515944c2bbc)
This goes to what we see below. Select the printer as below. If it is not present try reconnecting the printer and praying to god.
![image](https://github.com/TejasAvinashShetty/silvercloud/assets/27445854/c452b75a-3972-4686-a2a7-7427f986a54a)
Hopefully you are lucky and just follow the on screen instruction here on.

If at any time, you don't end up getiing a printout just  delete all the printers you have in CUPS and start over again.


### extra info 
From [Installing Printers in Linux | CUPS, Printing, and Scanning - YouTube : Chris Titus](https://www.youtube.com/watch?v=En2DJAMpwmY&pp=ygUcaHAgcHJpbnRlciBub3Qgd29ya2luZyBsaW51eA%3D%3D)

It seems to do stuff from the command line you could do the following

CUPS Setup - localhost:631

Setup user with modification to use printers

```bash

sudo usermod -aG lpadmin username
```
## more about AntiX
If this post has intrigued you about AntiX linux please see

<iframe width="560" height="315" src="https://www.youtube.com/embed/JCTaUAP6sSg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

or see [run with dolphin ](https://www.youtube.com/@runwiththedolphin)
