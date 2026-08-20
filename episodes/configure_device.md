---
title: "Configure a Networkable Device"
teaching: 60 # teaching time in minutes
exercises: 10 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::::::::::::::: questions

- "How do network devices identify themselves and talk to each other?
- "How can we configure our devices to be visible on a network?

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::: objectives

_By the end of this episode you will be able to..._

- Explain some principles of computer networking
- Use appropriate tools to examine a device's networking configuration
- Configure a device so that it is visible on a network


::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction
## Networking concepts
- IP addresses
- CIDR
- hostname


## Setting a `hostname`
When creating the operating system (Pi OS) image and writing this to the SD card, by default the hostname will be set to `raspberrypi`. This can be seen in the *terminal prompt* which has the form `<username>@<hostname>`, which for our devices will be `scnet@raspberrypi`.

We can display and manipulate the device's hostname using the `hostname` and `hostnamectl` shell commands.
```bash
scnet@raspberrypi:~ $ hostname
```
```output
raspberrypi
```
```bash
scnet@raspberrypi:~ $ hostname -I
```
```output

```

::::::::::::::::::::::::::::::::::::::::::::::::::: callout

## Terminal prompt

The *terminal prompt* is often initialised, in this case, as `<username>@<hostname>`, but this is not fixed and you may see other forms. The form of the terminal prompt can be set by the user in a special shell variable. Without configuration, the shell will use `#` as the prompt.

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::: challenge

## hostname
What does the `hostname -I` command do? Try typing `hostname --help` to see the options that `hostname` takes. Can you explain the output from `hostname -I`?

:::::::::::::::::::::::::::::: solution

## Result
`hostname -I` returns a blank line because at this point we haven't given our device an IP address.

:::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

Generally we'd like our networked devices to all have different hostnames so they can be distinguished from each other. We can change our device's hostname using the `hostnamectl` (host name control) shell command.
```bash
scnet@raspberrypi:~ $ hostnamectl
```
```output
 Static hostname: raspberrypi
       Icon name: computer
      Machine ID: a012d884fd9522e2cc329983ea31a790
         Boot ID: f4201aa4e935522113f840a843b3218f
Operating System: Debian GNU/Linux 13 (trixie)
          Kernel: Linux 6.18.34@rpt-rpi-v8
    Architecture: arm64
```
```bash
scnet@raspberrypi:~ $ hostnamectl hostname
```
```output
raspberrypi
```
```bash
scnet@raspberrypi:~ $ hostnamectl hostname frodo
```
```output
==== AUTHENTICATION FOR org.freedesktop.hostname1.set-static-hostname ====
Authentication is required to set the statically configured local hostname, as well as the pretty hostname.
Authenticating as: Rasperry Pi OS (scnet)
Password:
==== AUTHENTICATION COMPLETE ====
```
```bash
scnet@raspberrypi:~ $ hostnamectl hostname
```
```output
frodo
```
```bash
scnet@raspberrypi:~ $ hostnamectl hostname mynet-1
```
```output
==== AUTHENTICATION FOR org.freedesktop.hostname1.set-static-hostname ====
Authentication is required to set the statically configured local hostname, as well as the pretty hostname.
Authenticating as: Rasperry Pi OS (scnet)
Password:
==== AUTHENTICATION COMPLETE ====
```
```bash
scnet@raspberrypi:~ $ hostnamectl
```
```output
 Static hostname: rpi-1
       Icon name: computer
      Machine ID: a012d884fd9522e2cc329983ea31a790
         Boot ID: f4201aa4e935522113f840a843b3218f
Operating System: Debian GNU/Linux 13 (trixie)
          Kernel: Linux 6.18.34@rpt-rpi-v8
    Architecture: arm64
```

We'll leave the hostname of this device as `rpi-1`.

::::::::::::::::::::::::::::::::::::::::::::::::: challenge

## What's happened to the prompt?
Despite changing the hostname, the prompt hasn't changed. Why is this?

:::::::::::::::::::::::::::::: solution

The prompt is set in a special shell variable on logging into a new shell. You can check this by either launching a new shell or logging out (`exit`) and back in.
```bash
scnet@raspberrypi:~ $ bash
scnet@rpi-1:~ $ exit
scnet@raspberrypi:~ $
```

:::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::: challenge

## No hostname?
Is it possible for a device to have no hostname at all? How would you accomplish this?

:::::::::::::::::::::::::::::: solution

```bash
scnet@raspberrypi:~ $ hostnamectl hostname ""
```
```output
==== AUTHENTICATION FOR org.freedesktop.hostname1.set-static-hostname ====
Authentication is required to set the statically configured local hostname, as well as the pretty hostname.
Authenticating as: Rasperry Pi OS (scnet)
Password:
==== AUTHENTICATION COMPLETE ====
```
```bash
scnet@raspberrypi:~ $ hostnamectl hostname
```
```output
localhost
```

It's possible for a device to have no hostname. Note that by default the Raspberry Pi Imager will always assign a default hostname of `raspberrypi` if none is provided.
:::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::: callout

## Other `hostname` facts

Instead of configuring a device's hostname manually in the shell, the Pi OS writing tool *Raspberry Pi Imager* provides the option of setting the device hostname on OS creation.

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

## Setting an IP address
Computer networks don't internally deal with hostnames, they require IP addresses. What is the IP address of our device? To find out we need to look at what network devices are present using the Network Manager.

```bash
scnet@rpi-1:~ $ nmcli
```
```output
lo: connected (externally) to lo
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536
        inet4 127.0.0.1/8
        inet6 ::1/128

eth0: unavailable
        "Microchip SMSC9512/9514"
        ethernet (smsc95xx), B8:27:EB:BB:B1, hw, mtu 1500

wlan0: unavailable
        "Broadcom BCM43438 combo and Bluetooth Low Energy"
        wifi (brcmfmac), B8:27:EB:EE:91:E4, sw disabled, hw, mtu 1500

Use "nmcli device show" to get complete information about known devices and
"nmcli connection show" to get an overview on active connection profiles.

Consult nmcli(1) and nmcli-examples(7) man pages for complete usage details.
```
```bash
scnet@rpi-1:~ $ nmcli connection show
```
```output
NAME                UUID                                 TYPE     DEVICE
lo                  47a655e2-45d3-2295-9a0d-5086219e882e loopback lo
Wired Connection 1  432de219-fa35-9023-bf52-94344db2348b ethernet --
```

What does `nmcli device show` produce?

`nmcli` tells us that we have an Ethernet device, `eth0`, and a wireless device, `wlan0`. There's another device, `lo`, which is the *loopback device*, a virtual network interface which the computer uses to talk to itself. We can see that presently neither the ethernet nor the wireless devices have an IP address, i.e. they are not configured for networking.

::::::::::::::::::::::::::::::::::::::::::::::::: keypoints

- Explain how to use markdown with The Carpentries Workbench
- Demonstrate how to include pieces of code, figures, and nested challenge blocks

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
