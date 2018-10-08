A Lightweight Node JS Client to connect your low power device to the IoT.nxt SaaS Platform
=================

v2.0.1

You can follow the instructional video her start from scratch : https://www.youtube.com/watch?v=DVdypq6D_zs&list=PL-8IgX2Bx5hVou2kqyNVZlRlgdreiwtL0
Or You can download the PiZero img here and get started : https://github.com/IoT-nxt/ReadyIoTnxt-Images
You can follow the instructional video her start from IMG : https://www.youtube.com/watch?v=DVdypq6D_zs&list=PL-8IgX2Bx5hVou2kqyNVZlRlgdreiwtL0

--------------------------------
Lets start from scratch 

-download and install pibakery ,  http://www.pibakery.org/ yes its a gig and a bit but the most handy tool you will use to date when dealing with pi units
-download and install VNC viewer for your pc https://www.realvnc.com/en/connect/download/viewer/ 
-download and install angry ip scanner https://angryip.org/download/#windows 

_______________________________
Hardware: 

Lets prep our hardware , you can buy a Raspberry Pi ( Zero - 3 B+) all compatible 
Important , but a 16GB SSD card and higher , you might need to have some good space for caching and to also run other POC's from the same device without having to wipe and start again
Take your SD card and plug into your computer 

_______________________________
Load OS on SD card

To do this , start pibakery , select any startup scripts from the startup tab (View video if needed) like the WIFI setup 
Very IMPORTANT! Also drag in the enable VNC for the pi unit , we will use VNC to connect to the PI and setup everything we need , you can always disable when we are done
Then push on the blue write to SD card button , the top right corner
Select the SD card 
Select Raspbian Full 
Wait for the card to write

---------------------------------
Plug in your Pi unit

Now load your sd card into your pi and startup the pi unit

_________________________________
Lets find that pi 

Open angry ip scanner, and start scanning your subnet network 
Find the PI unit in the list , this would be the manufacturer pi foundation as the PC make 
__________________________________
Lets connect to the pi

Now open VNC viewer and type in the pi ip address and connect to the pi unit
First lets make the screen bigger 
Open a terminal and type 
sudo rapi-config 

go to advanced options  and select resolution , here you can set the bigger resolution 
save and reboot

___________________________________
UPDATE, Update , upgrade

now open a terminal and type the following (or paste in :) and run each line separately 

sudo apt-get update
sudo apt-get upgrade -y 

___________________________________
Make some space 

One of the really nice things about the newest builds of Raspbian is that it comes with just about all the software you need to get running. The downside of that is that all that software takes up a ton of space. RasPi.tv points out you can quickly snag about a 1GB back by deleting two apps: LibreOffice and Wolfram.

Obviously deleting apps frees up space, that’s not a surprise to anyone, but it’s easy to forget how important this is when you’re working with an operating system that runs off a MicroSD card. Every little bit of space matters in this case, and if you’re new to Linux or the Raspberry Pi, you might not know how exactly to go about freeing up space.

LibreOffice takes up around 250MB, while Wolfram clogs up about 650MB. This means they’re too of the bigger space hogs on the Pi. Obviously, if you’re using these programs, don’t delete them. But if you aren’t, getting rid of them is super easy. Just run these commands to get rid of Wolfram:

Run:
sudo apt-get purge wolfram-engine
sudo apt-get clean
sudo apt-get autoremove

You can do the same for LibreOffice by substituting libreoffice* in for wolfram-engine above. 
Other space wasting culprits could include minecraft-pi and sonic-pi. Of course, if you don’t want any additional software, 
just use the Raspbian Lite image from the get-go. The Lite image just includes the necessities to run Raspbian without any of the extra apps.

reboot pi when done
_________________________________
Install some things 

We would need some things installed before we continue 
-NodeJS 
The processor on Raspberry Pi is ARM, but depends on the model there can be ARMv6, ARMv7 or ARMv8. This 3 versions of ARM is supported by Node.js.

So first of all type this in your terminal on raspberry pi to detect the version that you need:
Run on terminal:
uname -m
If the response starts with armv6 than that's the version that you will need. For example for raspberry pi zero W you will need ARMv6

Go to node.js download page (https://nodejs.org/en/download/) and check right click on the version of ARM that you need and choose Copy Link address.

After that in the terminal using wget download the tar.gz file for that version. Just type wget, paste the link copied before and make sure the extension is .tar.gz. If it's something else change it to this and it should be ok. For example I will need ARMv6 and I will type this in my terminal:

wget https://nodejs.org/dist/v8.9.0/node-v8.9.0-linux-armv6l.tar.gz   (You can change the arm version in the link) 

Using tar that is already installed with the system on your raspberry pi just type this (make sure you change the filename with the file that you have)

tar -xzf node-v8.9.0-linux-armv6l.tar.gz
cd node-v6.11.1-linux-armv6l/
sudo cp -R * /usr/local/

Check if node and npm are installed correctly. This line should print the version of node and npm installed.

node -v
npm -v

Now you have node.js installed on your Raspberry Pi and working so you can build something using node

Next we install git :

sudo apt-get install git

git clone https://github.com/IoT-nxt/IotNxt-NodeJS-RestService.git

__________________________________
