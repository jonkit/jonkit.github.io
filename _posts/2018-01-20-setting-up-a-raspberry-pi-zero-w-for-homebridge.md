---
layout: post
category: post
date: 2018-01-20 21:43:58 -0500
permalink: setting-up-a-raspberry-pi-zero-w-for-homebridge
title: "Setting Up A Raspberry Pi Zero W For Homebridge"
---

Have you ever seen that [xkcd comic](https://xkcd.com/927/) where someone proposes a solution to having too many competing standards by creating a standard that consolidates them all? Except the end result is that they just add one more standard to the mix? Well this is that, but for guides on setting up homebridge on a Raspberry Pi. I have probably used a dozen or so different guides and resources to try and develop a repeatable setup process and finally compiled all of the steps myself. I cannot guarantee this will work for you and I’m not competent enough to really provide any troubleshooting support... but for my setup[^1-home], the following steps worked.

### Flash SD Card

I used to use PiBaker but have since found an app called [Etcher](https://etcher.io) that does a fantastic job of copying the desired OS to an SD card.  

I am using Raspbian Stretch and as a result I need to enable SSH on the device. To do so, re-mount the SD card and place a blank file named `ssh` in the `boot` volume. I do that via macOS terminal and the command: 

`touch /Volumes/boot/ssh` 

(where `/Volumes/boot/` is the path to the SD card).

I am also using a Raspberry Pi Zero W for this setup so I need to add the wifi credentials so that it will connect to my network when I first boot it up[^2-home]. With the SD card mounted, I had to add a file named `wpa_supplicant.conf` into the `boot` volume with my wifi credentials. I do that via macOS terminal and the command: 

`nano /Volumes/boot/wpa_supplicant.conf`  

I came across several variations of what to put in the file but here is a plain text file of what I have in my file. You will need to replace the network name and network password as well as the country code (using the ISO/IEC alpha2 country code).  

[My wpa_supplicant.conf file](http://jonkit.ca/cdn/files/wpa_supplicant.conf.txt)... just copy/paste the text into the file you create.

> **March 2018 Update:**  
> 
> If you change Wi-Fi networks (or passwords), you can remove the SD card from the Pi Zero, mount it on a computer, and use the steps above to create a new wpa_supplicant file with your new network information. Copy that new file into the mounted `boot` drive and then put the SD card back in the Pi Zero and boot it up. It should connect to your new network*

You should be set to plug in the Raspberry Pi and access it via SSH now. You will need to know the IP address of the Pi in order to access it. I was able to find this in the eero app as it lists all of the devices on my network. There are other ways to find the IP address of the devices on the network but I won’t be of much help with that. 

SSH into the Pi using the IP address and the username/password combo of `pi` and `raspberry`.

On first boot you should change the default password. To do that, type `passwd`, then enter the current password and the new password (twice) following along with the prompts. 

### Setting up homebridge

In theory, you should be able to do this using all of the information from the [homebridge github](https://github.com/nfarina/homebridge) page but I have never had luck getting it to work. Here are the steps that I have followed.

Run the update and upgrade commands to get everything up-to-date:  

`sudo apt-get update`

`sudo apt-get upgrade`

A version of node is required to make this all work. I have found success using v4.3.2 on my Raspberry Pi Zero W. Download that version directly from nodejs.org, unarchive the file, and then copy the files to your `/usr/local` directory with the following four commands:  

> **July 2018 Update:**  
> 
> Running through this setup I came across an error setting up PM2 (one of the last steps). I investigated it and it turns out it was because it required a newer version of node. Knowing that, I have made adjustments to the code below to go from Node.js v4.3.2 to v.4.5.0. Also worth noting - this isn't the first time that I've come across errors with a homebridge on a Raspberry Pi that were related to the version Node.js. If you come across an error in the future and track it down to Node.js, you can view all versions of Node at [this website](https://nodejs.org/dist/) (you will want to use the arm6l version). Swap in the URL below and adjust the `tar` and `cd` commands.

`wget https://nodejs.org/dist/v4.5.0/node-v4.5.0-linux-armv6l.tar.gz` 

`tar -xvf node-v4.5.0-linux-armv6l.tar.gz` 

`cd node-v4.5.0-linux-armv6l`

`sudo cp -R * /usr/local`


You can confirm you have installed this version of node with the command `node -v`

Now install git with the command: 

`sudo apt-get install git`

Finally, install several other required dependencies with the command: 

`sudo apt-get install libavahi-compat-libdnssd-dev`

To install homebridge, run: 

`sudo npm install -g --unsafe-perm homebridge`

This is where I would install all of the plugins you know you want. I was only doing this to add support the Harmony Hub, so I installed that plugin with: 

`sudo npm install -g homebridge-harmonyhub`

You can confirm that homebridge has been installed by trying to run it with the command: 

`homebridge`

You may see several warnings but ultimately it should launch and give you a HomeKit code to use to add homebridge to the Home.app.

Now we need to setup the config.json file. If homebridge is still running, use `control+c` to quit it. 

Change into the homebridge directory with: 

`cd .homebridge`

and create the config.json file with: 

`sudo nano config.json`

You can copy the config.json file from the homebridge GitHub repo and edit it to add support for all of the plugins you installed (each plugin page should have specific instructions). Within the config.json file I usually alter the `username` value as well as the HomeKit `pin` value. I’m not sure if this matters but I assume there is at least some risk using all of the defaults.  

Exit the file using `control+x`, selecting `Y` to confirm you want to save it, and then hit enter to confirm it. Now when you run homebridge you should see the new HomeKit pin listed and you should see it loading the plugins.  

Lastly, to make homebridge run as a service there are a few different options. In theory (again), you should be able to use the instructions in the homebridge GitHub but I have not had much success doing so. 

Recently I have used `pm2` as a way to run homebridge as a service. To do so, install pm2 with: 

`sudo npm install -g pm2`

You can confirm that pm2 was installed by typing: 

`pm2 startup`

Add homebridge to pm2 startup with the following two commands:

`pm2 start homebridge` 

`pm2 save`

Initialize pm2 and systemd with the following command:  

`sudo env PATH=$PATH:/usr/local/bin /usr/local/lib/node_modules/pm2/bin/pm2 startup systemd -u pi --hp /home/pi`

At this point, homebridge should be running and should start on each boot. You can now add homebridge to the Home.app... hopefully.

<p class="separator">&#10048; &#10048; &#10048;</p>

[^1-home]: Raspberry Pi Zero W using Raspbian Stretch Lite (2017-11-29). Other (probably not relevant details): a Kingston 64GB class 10 microSD card, eero wireless network, powered by a USB wall plug.

[^2-home]: There are definitely other ways to do this but this seemed to be the easiest for me.
