# Raspberry Assistant

## Foreword

This blog is mainly about the introduction, configuration and function about Raspberry Pi for people who are interested in it. Frankly I am also just a beginner. So I am willing to write down my experiences about my project on Raspberry Pi for recording and sharing. I hope that with this blog we can learn together. Please do not hesitate to discuss or point out my errors. If you like it, please press the "Star" button to support me, thank you!

## Something about project

My project is called "Raspberry Assistant". It consists of 4 Raspberry Pi 4B, so actually it is a multifunctional server. There are 5 functions until now (NAS, Streaming Media, Web server, Smart Home and Cluster). In the following text I will introduce them in detail. Other models of Raspberry Pi have the same principles, but need to pay attention to differences of hardware, such as interface.

## What is Raspberry Pi ?

Raspberry Pi is a tiny single-board computer. The purpose is to promote basic computer science education in schools with low-cost hardware and free software. At present, the performance of Raspberry Pi can only support light (daliy) use and learning. If you need to use it for high-intensity work, such as edge computing, please use a higher-performance server.

Raspberry Pi uses an ARM-based processor. TF card (MicroSD) is used as system storage. Raspberry Pi is equipped with USB interface and HDMI video output (supports sound output), built-in Ethernet/WLAN/Bluetooth network link, and can use a variety of operating systems. Certainly there are many models of Raspberry Pi, but the most commonly used is the B type.

Raspberry Pi OS is an officially launched operating system, suitable for all models of Raspberry Pi. They also provides third-party systems such as Ubuntu MATE, Ubuntu Core, Ubuntu Server, and OSMC for the public to download.

The specific information can be found on the the [official website](https://www.raspberrypi.org/).

## How to run Raspberry Pi ?

All we need are _**Raspberry Pi**_, _**TF card (MicroSD)**_, _**heat sink**_, _**fan**_, and _**TypeC charging cable and plug**_. Raspberry Pi can centainly run without display. But I think it is more convenient to connect display and raspberry pi with _**Micro HDMI cable**_ when you first configure it. 

### **The first step** is to write the system into TF card.
 
Actually an official software for installing the system is provided, its name is [Pi Imager](https://www.raspberrypi.com/software/). After installing Pi Imager on PC, you can insert the TF card into PC and choose the operating system in it (Raspberry Pi OS (32 - bit) is recommanded). Although the software will format TF card before writting, I recommend formatting the TF card with another software first. I will provide the software later. After you finish it, just press "WRITE" button and wait for the end. Finally insert the TF card into Raspberry Pi.

### **The second step** is to power up Raspberry Pi.

1. With display.

2. Without display.

### **The third step** is to open SSH and VNC.

1. SSH.

2. VHC.

### **The forth step** is to set static IP.



### **The fifth step** is to set language.


## How to realize these fucntion ?

### NAS

### Web Server

### Smart Home

### Cluster
