
# A Lightweight Node JS Client to connect your low power device to the IoT.nxt SaaS Platform

v2.0.1

This is a tutorial on how to get your Raspberry Pi set up, using the Node.js client, to connect your low power device to the IoT.nxt SaaS platform. 
You can also look at the [instructional video](https://www.youtube.com/watch?v=DVdypq6D_zs&list=PL-8IgX2Bx5hVou2kqyNVZlRlgdreiwtL0) for more information.

Alternatively, you can download the PiZero img [here](https://github.com/IoT-nxt/ReadyIoTnxt-Images).

*Please note that the software used in this tutorial, is what we found to be the easiest to get started with. If you have other preferred methods on how to set up your Pi, feel free to use it. In the end, all that is needed is a working Pi, on the network, running Node.js.*

----------

## Requirements
### Software
Download the following on your PC.
- [PiBakery](http://pibakery.org/)
- [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/)
- [Angry IP Scanner](https://angryip.org/download/#windows)

----------

### Hardware

- Raspberry Pi 3 B+ ***or***
- Raspberry Pi Zero
- 16GB SD card (recommended*)

Take your SD card and plug into your computer

**The card doesn't have to be 16GB big, but is recommended as you might need to have some good space for caching and to also run other POC's from the same device, without having to wipe it and start again.* 

----------
## Let's get started
### Load OS on SD card

Now it is time to prep our MicroSD card. To do this, 
1. Start PiBakery
2. Build the basic recipe and fill in the Network SSID and Password
:: On first boot
:: Setup WiFi
:: Enable VNC Server at Boot
3. Click the blue SD card button *Write* in the top right corner
4. Select the drive that the SD card is picked up from
5. Select Raspbian Full *(Raspbian Lite is not covered in this tutorial)*
6. Click *Start write*
7. Wait

----------

### Plug in your Pi unit

Now load your MicroSD card into your Pi and startup the Pi unit

----------

### Let's find the Pi

Open **Angry IP Scanner**, and start scanning your subnet network. Find the Pi unit in the list. This would be the manufacturer "Pi Foundation" as the PC make, or **raspberrypi.local** as the hostname.

----------

### Let's connect to the Pi

Open VNC viewer, type in the Pi's IP address and connect to the Pi unit.
Type in the username and password. Default is ***pi*** and ***raspberry*** respectively, unless it was changed during the baking process.
First let's make the screen bigger. Open a terminal and type 
`sudo rapi-config`

Go to advanced options and select *Resolution*. Here you can set a bigger resolution.
Save and reboot the Pi.

----------

### Update and upgrade

Now open a terminal and type the following; (run each separately)

    sudo apt-get update 

    sudo apt-get upgrade -y

----------

### Make some space

One of the really nice things about the newest builds of Raspbian, is that it comes with just about all the software you need to get running. The downside of that is that all that software takes up a ton of space. RasPi.tv points out you can quickly snag about a 1GB back by deleting two apps: **LibreOffice** and **Wolfram**.

Obviously deleting apps free up space, that’s not a surprise to anyone, but it’s easy to forget how important this is when you’re working with an operating system that runs off a MicroSD card. Every little bit of space matters in this case, and if you’re new to Linux or the Raspberry Pi, you might not know how exactly to go about freeing up space.

LibreOffice takes up around 250MB, while Wolfram clogs up about 650MB. This means they’re two of the bigger space hogs on the Pi. Obviously, if you’re using these programs, don’t delete them. But if you aren’t, getting rid of them is super easy. Just run these commands in the terminal to get rid of 
##### Wolfram
    sudo apt-get purge wolfram-engine 
    sudo apt-get clean 
    sudo apt-get autoremove

##### LibreOffice
    sudo apt-get purge libreoffice 
    sudo apt-get clean 
    sudo apt-get autoremove
  
Other space wasting culprits could include **minecraft-pi** and **sonic-pi**. Of course, if you don’t want any additional software, you can use the Raspbian Lite image from the get-go. This tutorial doesn't cover that however. The Lite image just includes the necessities to run Raspbian without any of the extra apps.

Reboot your Pi when done

----------

### Install some Node and Git

We would need some things installed before we continue 

##### NodeJS 
The processor on Raspberry Pi is ARM, but depends on the model there can be ARMv6, ARMv7 or ARMv8. This 3 versions of ARM is supported by Node.js.

First detect what processor is running on your Pi, by typing the following in a terminal

    uname -m

If the response starts with **armv6** then that's the version that you will need. For example for Raspberry Pi Zero W will need ARMv6

Go to the [Node.js](https://nodejs.org/en/download/) download page. Right click on the version of ARM that you need and choose ***Copy Link address***.

Open a terminal, and download the file using wget. You do this by typing

    wget <the copied link address>
Make sure the extension is .tar.gz. If it's something else change it to this and it should be ok.

For example I will need ARMv6 and I will type this in my terminal:

    wget  https://nodejs.org/dist/v8.9.0/node-v8.9.0-linux-armv6l.tar.gz

(You can change the arm version in the link)

Using `tar` that is already installed on your Raspberry Pi, just type the following; (make sure you change the filename with the file that you have)

    tar -xzf node-v8.9.0-linux-armv6l.tar.gz cd node-v6.11.1-linux-armv6l/ sudo cp -R * /usr/local/

Before we carry on, let's check if **node** and **npm** are installed correctly. These lines should print the versions of them.

    node -v 

    npm -v

Now you have Node.js installed on your Raspberry Pi, and working, you can build something using node.

##### Git
Simply run the following to install git;

    sudo apt-get install git
Then clone the *IotNxt-NodeJS-RestService* repo by running

    git clone https://github.com/IoT-nxt/IotNxt-NodeJS-RestService.git
