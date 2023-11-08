<h1>Performing a Denial of Service Attack from the Wan Lab</h1>

<h2>Description</h2>
The lab environment comprises an internal network, which includes a Windows server (IP address: 192.168.1.10), a Metasploitable server (IP address: 192.168.1.30), and a Linux sniffer machine without a designated IP address. At the network perimeter, there is a pfSense firewall with an IP address of 203.0.113.100. Additionally, an external Windows 8.1 Attack machine with an external IP address of 175.45.176.200 is present.

In this experiment, we will utilize a software tool known as "Low Orbit Ion Cannon" (LOIC) to execute TCP, UDP, and HTTP flood attacks on the network. The Linux machine will serve as a packet capture device, allowing us to record the packets generated during each type of flood.

It is important to emphasize that LOIC is not a legitimate or legal tool; instead, it is a piece of software commonly associated with malicious activities, specifically Distributed Denial of Service (DDoS) attacks. These attacks involve inundating a target computer system or network with an excessive volume of traffic, thereby rendering it inaccessible to legitimate users. LOIC is just one of the tools that can be exploited to carry out such attacks.
<br />

<h2>Project walk-through:</h2>

<p align="center">
Lab Topology: <br/>
<img src="https://imgur.com/9qQbUOC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Start by accessing the Linux Sniffer machine  <br/>
<img src="https://imgur.com/3JqTn6y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open the Linux terminal and determine the IP Address for the Sniffer Machine: <br/>
<img src="https://imgur.com/ogm0CQV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use the following command to remove the IP address of the Linux Sniffer machine:  <br/>
<img src="https://imgur.com/CIKFPJm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use the following command to create a text file for the packets sniffed during the DDOS Attacks:  <br/>
<img src="https://imgur.com/UzCMdoM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 <h2>Explanation</h2>
Enter the following command: tcpdump -i eth0 -nntttt -s 0 -w TCPcapture.cap
 <br />
 'tcpdump': command is used for packet capture and network analysis.
 <br />
 'eth0': specifies the name of the network interface to monitor (Linux sniffer).
 <br />
 '-nn': These options make `tcpdump` show IP addresses and port numbers in numbers, not names, to speed up the capture process by avoiding DNS and service name lookups.
 <br />
 '-tttt': This option sets the timestamp format for captured packets to include microseconds.
 <br />
 '-s 0': This option, when set to 0, captures the entire packet, ensuring the full content is recorded. If you specify a value, `tcpdump` will cut off packets at that length.
 <br />
 '-w TCPcapture.cap': This option tells `tcpdump` where to save the captured packets. In this case, it saves them to a file called TCPcapture.cap.
 <br />
 <br />
The Linux sniffer is now Listening for packets and analyzing traffic:  <br/>
<img src="https://imgur.com/I7juYfY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> Start up the Windows external Attack machine:  <br/>
 <img src="https://imgur.com/Eozh0nc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Double-click on the LOIC.exe and start up the Low Orbit ION Cannon Software:  <br/>
<img src="https://imgur.com/N14NRNN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
 <br />
 The Low Orbit ION Cannon is configured to TCP Flood the Linux machine. The selected target is set to the IP address of the Pfense router:  <br/>
 <img src="https://imgur.com/M2ErzMN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
 <br />
Return to the Linux sniffer click ctl+c and observe packets captured from the TCP flood: 
 <img src="https://imgur.com/7ezS9zg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br/>
 <h2>Explanation</h2>
 Also, run the command Capinfos TCPcapture.cap
 <br/>
 The `capinfos` command tells you details about a captured network file (like `TCPcapture.cap`). 
  <br/>
 It shows information like when the capture started, how many packets were recorded, which network interfaces were used, and more. 
  <br/>
 It helps you understand what's inside the capture file.
  <br/>
 The following steps are repeated to create a UDP Flood and HTTP Flood attack on the network and captured by the Linux sniffer.
  <br/>
   <br/>
 End of Lab  <br/>
 

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
