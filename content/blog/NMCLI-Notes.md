+++
title = "NMCLI Set Static IP Address"
author = ["Preston Davis"]
description = "Setting static ip address using NMCLI"
date = 2024-07-13T15:25:00-04:00
lastmod = 2024-07-13T15:39:38-04:00
tags = ["article", "linux"]
draft = false
+++

## Determine the interface to be updated {#determine-the-interface-to-be-updated}

In most systems, you will have 1 or more network cards that can be used to pass traffic. To find out which cards you have available, run the following command:

```bash
ifconfig
```

This will list out the cards seen by your system.


### Update your configuration {#update-your-configuration}

We will issue the following commands to set the ip address, gateway, and dns for our chosen network card:

```bash
sudo nmcli con mod <networkcard> ipv4.address 192.168.10.20/24

sudo nmcli con <networkcard> ipv4.gateway 192.168.10.1

sudo nmcli con mod <networkcard> ipv4.dns "1.1.1.1"

sudo nmcli con mod <networkcard> ipv4.method manual
```

Once completed, we will enable the settings with the following:

```bash
nmcli con up <networkcard>
```
