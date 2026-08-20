---
title: "Connecting Devices in a Network"
teaching: 40 # teaching time in minutes
exercises: 20 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

 - how are devices connected together into a network
 - how can we check that a device is properly connected?
 - how can we interact with a device via the network?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

_By the end of this episode, learners should be able to..._

- create an IP address network between two devices
- use the /etc/hosts file to connect using hostnames 
- test a network connection using ping 
- create a network between two devices using hostnames 
- connect to a console on a remote device using ssh 

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

### connect your devices via ip address

We have 2 devices which are capable of talking to each other over a network
Next we physically connect them.  The simplest way to do this is using a network cable between the devices.

### test the connection with ping
We know the IP addresses of each device because we set them in the last episode.  Check the ip address of the device you are logged in on with

```bash
hostname -I
```output
192.168.0.2
```error
just checking
```

### configure a hostname
### edit etc/hosts
### connect via hostname
#### test that connection with ping
#### test that connection with ssh

:::::::::::::::::::::::::::::::::::::::: instructor
only visible to instructors.
appear inline
are aggregated into the bottom part of instructor notes for the lesson.

:::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: challenge

### Exercise Title


:::: hint
a hint here
:::::::::

:::: solution
the answer
:::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

Objective: test a network connection using ping
Multichoice:

Have a list of commands with their outputs
Ask participants to choose the right one for using ping to test a connection
The right one must show a successful connection
Objective: create a network between two devices using hostnames
Authentic Assessment:

ask the participants to connect their devices using hostnames
then test that this has worked with ping
Objective: connect to a console on a remote device using ssh
Multi choice:

choose the correct ssh command from a list of possible commands
ssh user@192.168.0.2
scp user@192.168.0.2
ssh hostname
ssh user -ip=192.168.0.2
Objective: create an IP address network between two devices
Authentic Assessment:

We have pinged with IP then connected with hostname, and shown ssh
How would you connect with ssh using the IP address?
Switch to IP connection and try ssh-ing



:::::::::::::::::::::::::::::::::::::::: keypoints

- answer to the question

::::::::::::::::::::::::::::::::::::::::::::::::::
