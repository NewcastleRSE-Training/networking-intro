---
title: "Configure a Networkable Device"
teaching: 60 # teaching time in minutes
exercises: 10 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- "How do network devices identify themselves and talk to each other?
- "How can we configure our devices to be visible on a network?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

_By the end of this episode you will be able to..._

- Explain some principles of computer networking
- Use appropriate tools to examine a device's networking configuration
- Configure a device so that it is visible on a network


::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction
## Networking concepts
- IP addresses
- CIDR
- hostname


## Examining the device's hardware
When creating the operating system (Pi OS) image and writing this to the SD card, by default the hostname will be set to `raspberrypi`. This can be seen in the *terminal prompt* which has the form `<username>@<hostname>`, which for our devices will be `scnet@raspberrypi`.

We can display and manipulate the device's hostname using the `hostname` and `hostnamectl` shell commands.
```bash
scnet@raspberrypi:~ $ hostname
raspberrypi
scnet@raspberrypi:~ $ hostname -I

scnet@raspberrypi:~ $ hostname
```

:::::::::::::::::::::::::::::::::::;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;; challenge
## hostname
What does the `hostname -I` command do? Try typing `hostname --help` to see the options that `hostname` takes. Can you explain the output from `hostname -I`?
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;; solution
## Result
`hostname -I` returns a blank line because at this point we haven't given our device an IP address.
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

:::::::::::::::::::::::::::::::::::;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;; callout
Terminal prompt

The *terminal prompt* is often initialised, in this case, as `<username>@<hostname>`, but this is not fixed and you may see other forms. The form of the terminal prompt can be set by the user in a special shell variable. Without configuration, the shell will use `#` as the prompt.
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

:::::::::::::::::::::::::::::::::::;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;; callout
Configuring a device's hostname

Instead of configuring a device's hostname manually in the shell, the Pi OS writing tool *Raspberry Pi Imager* provides the option of setting the device hostname on OS creation.

It's possible for a device 
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;


::::::::::::::::::::::::::::::::::::: keypoints

- Explain how to use markdown with The Carpentries Workbench
- Demonstrate how to include pieces of code, figures, and nested challenge blocks

::::::::::::::::::::::::::::::::::::::::::::::::
