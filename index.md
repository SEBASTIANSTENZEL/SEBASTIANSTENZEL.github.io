# **Raspberry Assistant**
# **Foreword**

This blog is mainly about the introduction, configuration and function about Raspberry Pi for people who are interested in it. Frankly I am also just a beginner. So I am willing to write down my experiences about my project on Raspberry Pi for recording and sharing. I hope that with this blog we can learn together. Please do not hesitate to discuss or point out my errors. If you like it, please press the "Star" button to support me, thank you!

# **Something about project**

My project is called "Raspberry Assistant". It consists of 4 Raspberry Pi 4B, so actually it is a multifunctional server. There are 5 functions until now (NAS, Streaming Media, Web server, Smart Home and Cluster). In the following text I will introduce them in detail. Other models of Raspberry Pi have the same principles, but need to pay attention to differences of hardware, such as interface.

# **What is Raspberry Pi ?**

Raspberry Pi is a tiny single-board computer. The purpose is to promote basic computer science education in schools with low-cost hardware and free software. At present, the performance of Raspberry Pi can only support light (daliy) use and learning. If you need to use it for high-intensity work, such as edge computing, please use a higher-performance server.

Raspberry Pi uses an ARM-based processor. TF card (MicroSD) is used as system storage. Raspberry Pi is equipped with USB interface and HDMI video output (supports sound output), built-in Ethernet/WLAN/Bluetooth network link, and can use a variety of operating systems. Certainly there are many models of Raspberry Pi, but the most commonly used is the B type.

Raspberry Pi OS is an officially launched operating system, suitable for all models of Raspberry Pi. They also provides third-party systems such as Ubuntu MATE, Ubuntu Core, Ubuntu Server, and OSMC for the public to download.

The specific information can be found on the the [official website](https://www.raspberrypi.org/).

# **How to run Raspberry Pi ?**

All we need are _**Raspberry Pi**_, _**TF card (MicroSD)**_, _**heat sink**_, _**fan**_, and _**TypeC charging cable and plug**_. Raspberry Pi can centainly run without display. But I think it is more convenient to connect display and raspberry pi with _**Micro HDMI cable**_ when you first configure it. 

## - _**The first step**_ is to write the system into TF card.
 
Actually an official software for installing the system is provided, its name is [Pi Imager](https://www.raspberrypi.com/software/). After installing Pi Imager on PC, you can insert the TF card into PC and choose the operating system in it (Raspberry Pi OS (32 - bit) is recommanded). Although the software will format TF card before writting, I recommend formatting the TF card with another software first. I will provide the software later. After you finish it, just press "WRITE" button and wait for the end. Finally insert the TF card into Raspberry Pi.

## - _**The second step**_ is to power up Raspberry Pi.

I. With display





II. Without display




## - _**The third step**_ is to set Chinese.

After the system becomes Chinese, there will be garbled characters. But it is still helpful for beginners.

I. Install Chinese character library. When prompted "Do you want to continue[Y/n]?", enter y.

`sudo apt-get install ttf-wqy-zenhei`

II. Install sunpinyin and google pinyin.

`sudo apt-get install fcitx fcitx-googlepinyin fcitx-module-cloudpinyin fcitx-sunpinyin`

III. Set to support Chinese. Localisation Options -> Change Locale. Press Space ro choose _zh_CN GB2312_, _zh_CN.GB18030 GB18030_, _zh_CN.GBK GBK_, _zh_CN.UTF-8 UTF-8_ and press Enter to confirm.

`sudo raspi-config`

IV. Choose _zh_CN.UTF-8_ and press Enter to confirm.

V. Resart Raspberry Pi.

`sudo reboot`

VI. If it still doesn't show Chinese, open Raspberry Pi Configuration to change Character Set in Locale in Localisation to _GB18030_ and restart.

VII. If you can not input chinese characters. You can add sunpinyin and google pinyin in Fcitx Configuration.

## - _**The forth step**_ is to set static IP.

I. Modify the /etc/dhcpcd.conf file with this command.

`sudo nano /etc/dhcpcd.conf`

II. And then put these codes into the end of the file.

```
interface eth0
 
static ip_address=192.168.7.10/24
static routers=192.168.7.1
static domain_name_servers=192.168.7.1
 
interface wlan0
 
static ip_address=192.168.7.200/24
static routers=192.168.7.1
static domain_name_servers=192.168.7.1
```

It should be known that eth0 is the wired configuration, wlan0 is the wireless configuration, ip_address (/24 is necessary) is the static IP that you want, routers are gateways and static domain_name_servers is DNS.

## - _**The fifth step**_ is to open VNC.

I. Enter the following command in the terminal to enter the configuration interface.

`sudo raspi-config`

II. Interfacing Options -> VNC -> Yes. The system may prompt you if you want to install the VNC service, enter y and press Enter. Then wait for the system to automatically download and install.

## - _**The sixth step**_ is to install teamviewer.

VNC can be used to remotely control Raspberry Pi in LAN. But teamviewer allow people to remotely control Raspberry Pi from anywhere, which is more convenient. It can also be used for chatting, transferring files and monitoring device status. It is the best choice for unattended devices.

I. First update to prevent errors.

`sudo apt-get update`

`sudo apt-get upgrade`

II. Download .deb file (a special one for Raspberry Pi).

`wget https://download.teamviewer.com/download/linux/teamviewer-host_armhf.deb`

III. Install with dpkg.

`sudo dpkg -i teamviewer-host_armhf.deb`

IV. After running the above command, you will notice some errors about a particular package not being installed. Use this command to automatically detect missing packages and try to download the best version for the software.

`sudo apt --fix-broken install`

V. Teamviewer should be ok. You can certainly change some settings if you want.

## - _**Optional**_: LCD Display

I. Download LCD display driver.

`wget -O LCD-show.tar.gz http://www.waveshare.net/w/upload/0/00/LCD-show-170703.tar.gz`

II. Install LCD display driver.

2.8 inch: 

```
sudo tar zxvf LCD-show.tar.gz
cd LCD-show/
sudo ./LCD28-show
```

3.5 inch (B): 

```
sudo tar zxvf LCD-show.tar.gz
cd LCD-show/
sudo ./LCD35B-show
```

Return to HDMI: 

```
sudo tar zxvf LCD-show.tar.gz
cd LCD-show/
sudo ./LCD-hdmi
```

## - _**Optional**_: Netdata Monitor

I. Enter the following command in the terminal to install.

`bash <(curl -Ss https://my-netdata.io/kickstart.sh)`

II. Enter the URL in the address bar of the browser to monitor.

`http://[RASPBERRYPIIPADDRESS]:19999`

# **How to realize these function ?**

## **- NAS**




## **- Web Server**

Apache is No.1 web server software used in the world. It can run on almost all widely used computer platforms and is the most popular web server-side software due to its cross-platform and security being widely used.

I. Install Apache on the Raspberry Pi

`apt-get install apache2`

When prompted "Do you want to continue[Y/n]?", enter y,  and wait for the installation to complete. If there is an error, please try to update the command with the following 2 commands.

`sudo apt-get update`

`sudo apt-get upgrade`

II. Test

Enter the IP address of Raspberry Pi in the address bar of the browser, s Webpage will be shown. This is the home page of the default Apache Web Server. This html file can be modified, it is /var/www/index.html. This kind of file can be editted by Notepad++ (on PC) or Geany (on Raspberry Pi).

III. Intranet penetration

## **- Smart Home**

In this part, Homekit developed by Apple and Homebridge will be used to build a smart home.

Homebridge is a lightweight NodeJS server built to emulate the iOS HomeKit API. Using this software, you can integrate devices in your home with Homekit. You can also use Homebridge to connect various third-party apps that aren't supported by Homekit, such as Xiaomi.

I. 

`curl -sL https://deb.nodesource.com/setup_12.x | sudo bash -`

II. 

`sudo apt install -y nodejs gcc g++ make python`

III. 

`node -v`

IV. 

`sudo npm install -g npm`

V. 

`sudo npm install -g --unsafe-perm homebridge homebridge-config-ui-x`

VI. 

`sudo hb-service install --user homebridge`

VII. 

`hostname -I`

VIII. 

`http://[RASPBERRYPIIPADDRESS]:8581`

IX. 

`sudo hb-service uninstall`

X.

`sudo npm uninstall -g homebridge homebridge-config-ui-x`



## **- Cluster**





