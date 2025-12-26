---
title: Free Tier Oracle server experience
published: 2025-12-25
description: 'Setting up oracle server'
image: "/assets/images/oracle-server/oserver.webp"
tags: [Guide,Experience,Blogging]
category: Guides
draft: false 
lang: ''
---
# How did this idea started
Before the oracle server, I had a powerful 6-core CPU with 16GB of RAM on [Google Cloud Server](https://cloud.google.com/) running stuff like Minecraft Server, proxying, and rendering useless maps for fun.

Along the way, I learnt a lot about the command in Ubuntu Linux. But since the server was running on a free credit, after around 3 months, the credit ran out and I forgot to stop it. Costing me a fortune of 6.8 POUNDS outside of the free credit.

For a period of time, I was having "server-less life" and it felt like someone was missing. Then, I came across a reddit post stating that oracle gives free ARM servers, and they do look quite powerful. So here we go.

## Determine the resources we can use

First of all, Oracle provide two types of free shapes. You can read more about it [here](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm)
![](/assets/images/oracle-server/avaliable_shape.webp)

Oracle also provide you with some free credit before it expires, so you can create some powerful servers and have some fun before creating the free tier server.

:::note
In many places, the ARM instance is not avaliable, so you will need some luck to get it. I chose France (Paris) and appearently all of the ARM instances are taken. So I had no choice but to use the AMD Processor instance.
:::

To create an account, you first head to [Oracle](https://www.oracle.com/). Where you will find "View Accounts" at the top right corner, and "Sign Up for Free Cloud Tier"

Carefully go through the regestration. Choose a region that is cloest to you for better network performance and connection.

:::warning
It is important to use real adress and card details, since Oracle have the rights to confiscate your server at any point. And Oracle does check your card detail frequently. DO NOT USE a VPN and digital bank cards during set up process
:::

# Creating a free tier server

After regestration, head to the [Cloud Console](https://cloud.oracle.com/). At the top of the page, search for "Instance", and click the "Instance" under "Services"

Now, you want to "Create instance". Set the name to anything you want.

## Image

For the image part, if you know which type of OS Server works best for you, choose it. If not, I would recomment Ubuntu server
![](/assets/images/oracle-server/instance_image.webp)

## Shape

Edit the shape, go for Virtual machine and under "Specialty and previous generation" you will find the AMD Processor, and "Ampere" you will find the ARM Processor. It is recommended to go for the ARM processor as it often has mnuch better performance, and you get more RAM **(WOW! Free RAM in this economy?)**

Tap on the Add OCPU button as high as possible until it said you ran out of limit. Click Apply, and head to the next section. Enable Security and next. Create a Primary VNIC, Virtual Cloud Network and a subnet by following the guide on the website. You do not have to change any of the settings when creating them.

:::important
At the bottom of the Networking page, there is a option for "Download private key" and "Download public key". YOU MUST download the private key or else YOU WILL NOT be able to ssh into your server later on, and the whole process is ruined. For the public key, download at your own preference.
:::

## Storage

Now on to the Storage part, create a Boot volume of any size equal or under 200GB, if you are setting up an ARM machine (Which you can only set up one) , then it would be better to use the full 200GB of free storage. If you are planning to set up multiple servers using the AMD Processor, when you would want to have 200/(number of server) to get the storage fully utilized. Ignore the warning on the screenshot because I've already used my credit.

![](/assets/images/oracle-server/boot_volume.webp)

After storage, head to review page and make sure all your server information are correct and create!

# Tweaking time~

Now, head to the instance section and you should see your server. Make sure there is a **Always Free** sign at the end of your server name. 
![](/assets/images/oracle-server/always_free.webp)

Take a note of your Public IP, and click on the server name. You should see a list of options you can make changes.
![](/assets/images/oracle-server/option_list.webp)

## Networking

Click on networking and click on your subnet. 
![](/assets/images/oracle-server/security_list.webp)

Instead of making changes to the Default Security List for *Server Name*. I recommend to create a new security list, as you have a high chance of messing up and causing you not able to ssh into the server later on.

Name the security list as anything you want. Open it and head to Security rules section. Here, you want to open the port needed for your project later on.
![](/assets/images/oracle-server/security_rules.webp)

Here is some of the ports I have opened
| Port | Description |                                                                                                                                                                                   
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  `22`       | SSH |
| `80`   | HTTP                                                                                                                                                                    |
| `443`        |HTTPS                                                                                                                                               |
| `8388`       | TDP/UDP |
| `25565`      |Take a guess? Of course it's for :spoiler[Minecraft Server!]         

To create a ingress of egress rule. Click on the "Add Ingress/Egress rule"
![](/assets/images/oracle-server/ingress_rule.webp)

For the "Source CIDR" if you want to be able to access this port everywhere, put **0.0.0.0/0**. Fill in "Srouce Port Range" with **All**, and "Destination Port Range" as needed. I would recommend you to open port **80, 443** and **8388** on both ingress and egress before you add any other ports, it may cause you to have problem accessing package manager later on.

Head back to the server detail and start your server with the "Start" button on top right.

## SSH into your server

Open your CMD if you are on Windows and Terminal on MacOS. To SSH into your server, you would need to get the private key location which you have previously downloaded, and your server Public IP. If you have no idea how to type the location into a Terminal, you can simply drag the file into terminal and it will auto-fill.

Copy the following command, be aware to modify the file location

```bash
ssh ubuntu@Server Public IP -i Private Key location
```

:::tip
If you can't SSH into your server, try switching your network environment, as some network block port 22 on purpose.
:::

And voilà! If everything went smoothly, you should be greeted with something like this

```bash
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.14.0-1016-oracle x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Thu Dec 25 22:24:37 UTC 2025

  System load:  X.XX              Processes:             147
  Usage of /:   XX% of XXGB   Users logged in:       0
  Memory usage: XX%                IPv4 address for ens3: 10.0.0.XX

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

Expanded Security Maintenance for Applications is not enabled.

XX updates can be applied immediately.
To see these additional updates run: apt list --upgradable

XX additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm


*** System restart required ***
Last login: hh:mm:ss from XXX.XXX.XXX.XXX
ubuntu@host-10-0-0-XX:~$
```
## Update your server

Before you do anything else, update your server OS, as there are recently many crypto mining virus on the internet. And you do not want to have it.

```bash
sudo apt full-upgrade
```

You will then see a bunch of service and updates, with a prompt saying "Do you want to continue? [Y/n]" Type in Y to continue.

To monitor your server with a better CLI GUI, btop is very handy to use. It allows you to monitor various of system info easily. To install, run

```bash
sudo apt install btop
```

Type Y to confirm. After that, run with this command

```bash
btop
```
And a nice CLI GUI should appear on your screen. To get out of it, press Ctrl+C

:::tip
You can press **ESC** to adjust the theme and settings.
:::

The server doesn't automatically come with a swap, causing a lot of problem for me in the early stage, as anything heavier than a few hundred MB will cause the system to come to a halt, so to have better performance, we will need to create a swap. Run the command one by one.

```bash
sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```
What does those command do

1.Create the swap file, the file size is 4GB, adjust it based on your need

2.Secure the file

3.Set it up as a swap

4.Enable swap

# Enjoy!

Aaaaaaand that is pretty much it. You should by now have a working server and feel free to mess around with it. 

I am planning to have a seperate blog about interesting projects you can run on your server, from easy to hard. This is my first ever blog and hope you like it. There will be more blog abot tech and planes coming up.