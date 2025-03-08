---
layout: default
---

_Created by Matthew Adriaanzen_

Nmap offers many different types of scans that can be used to obtain various results about our targets. Some of the features of Nmap can be divided into the following scanning techniques:

*  Host discovery
*  Port scanning
*  Service enumeration & detection
*  OS detection

## What you'll learn here:

*  Understanding basic Nmap scanning techniques.
*  Identifying open ports & running services.
*  Detecting vulnerabilities.
*  Gaining insights into network reconnaissance.

## Tools Used:

*  Nmap – For scanning & enumeration.
*  Parrot OS/Linux – The environment used for testing.
*  HTB Academy – The learning platform followed for this project.
*  StationX Nmap Cheat Sheet.

## Methodology:

This section details the step-by-step approach for using Nmap.

### Syntax

The syntax for Nmap is fairly simple and looks like this:

![NmapSyntax](nmapsyntax1.png)

### Scan Techniques

Nmap offers many different scanning techniques, making different types of connections and using differently structured packets to send. Here we can see all the scanning techniques Nmap offers:

![NmapScanTechniques](nmapscantechniques1.png)

The TCP-SYN scan `(-sS)` is one of the default settings unless we have defined otherwise and is also one of the most popular scan methods. This scan method makes it possible to scan several thousand ports per second. The TCP-SYN scan sends one packet with the SYN flag and, therefore, never completes the three-way handshake, which results in not establishing a full TCP connection to the scanned port.

*  If our target sends a SYN-ACK flagged packet back to us, Nmap detects that the port is open.
*  If the target responds with an RST flagged packet, it is an indicator that the port is closed.
*  If Nmap does not receive a packet back, it will display it as filtered. Depending on the firewall configuration, certain packets may be dropped or ignored by the firewall.

Lets take a look at an example of such a scan:

![NmapSYNselfscan](nmapSYNselfscan1.png)

In the example above, we can see that we have four different TCP ports open. In the first column, we see the number of the port. Then, in the second column, we see the service's status and then what kind of service it is.

Here are some more examples on how you can use Nmap (take note of the command Syntaxes):

(_Note: `localhost` refers to my own machine `127.0.0.1`. I'm testing these scans on my system to understand what information can be exposed about me. This is a good practice for security awareness. Additionally, HTB prohibits scanning external machines, so I'm only scanning my own._)

### 1. Scanning for Open Ports

![NmapAllPortScan](nmapallportscan1.png)

> Purpose: The `-p-` option scans all 65,535 ports to identify open ones. However in this case the results were the same as the pervious scan because only these 4 ports are opened.

### 2. Service and Version Detection

![NmapServiceVersionDetection](NmapServiceVersionDetection1.png)

> Purpose: The `-sV` option detects the versions of services running on open ports. This helps in vulnerability assessment.

Additionally if you would like to check the version of the service running on a specific port (in this example we using port 22 which is SSH) you can do the below command:

![NmapServiceVersionDetectionSSH](NmapServiceVersionDetectionSSH1.png)

### 3. Operating System Detection

![NmapOSdetection](NmapOSdetection1.png)

> Purpose: The `-O` option specifies the nmap command to determine the OS running on the target based on response fingerprints.

### 4. Aggressive Scan (All-in-One)

![NmapAllinfo1_enhanced](NmapAllinfo1_enhanced.png)
![NmapAllinfo2_enhanced](NmapAllinfo2_enhanced.png)

> Purpose: The `-A` option combines multiple techniques, including OS detection, version detection, script scanning, and traceroute.

These are just a few of the many many ways you can conduct a scan, The tables below includes more ways you can use Nmap:

### Target Specification

| Switch       | Example                       | Description               |
|:-------------|:------------------------------|:--------------------------|
|              | nmap 192.168.1.1 192.168.2.1  | Scan specific IPs         |
|              | nmap 192.168.1.0/24           | Scan using CIDR notation  |
|              | nmap 192.168.1.1-254          | Scan a range              |
|              | nmap scanme.nmap.org          | Scan a domain             |

As stated before there are many more (complex) ways to use Nmap, this is just a beginners guide to get you a bit more familar with the tool and understand the basics of how to use Nmap.

If you would like a more in depth guide to Nmap (which includes: Firewall/IDS/IPS Evasion, Host Discovery, NSE Scripts, etc...) I recommend checking the course on HackTheBox Academy, its completely free! Just sign up and you're ready to go!

HTB Nmap Course:
<a href="https://academy.hackthebox.com/course/preview/network-enumeration-with-nmap" target="_blank" rel="noopener noreferrer">HackTheBox</a>

Nmap Cheat Sheet:
<a href="https://www.stationx.net/nmap-cheat-sheet/" target="_blank" rel="noopener noreferrer">StationX</a>

