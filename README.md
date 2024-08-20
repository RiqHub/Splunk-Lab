# Splunk-Lab

*ATTENTION* 
To set up the two machines you need you can use these two videos: 
- [Lab Prep Vid 1](https://www.youtube.com/watch?v=kku0fVfksrk&list=PLG6KGSNK4PuBWmX9NykU0wnWamjxdKhDJ&index=1)
- [Lab Pred Vid 2](https://www.youtube.com/watch?v=5iafC6vj7kM&list=PLG6KGSNK4PuBWmX9NykU0wnWamjxdKhDJ&index=3)



<h2>Description</h2>
This project open
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Splunk</b>
  - [Installation Tutorial](https://www.youtube.com/watch?v=iaBJ-PK8_RI)
- <b>Metasploit</b>
- <b>Nmap</b>
- <b>Sysmon</b>
  - [Installation Tutorial(https://www.youtube.com/watch?v=uJ7pv6blyog)

<h2>Environments Used </h2>

- <b>Windows 10</b> 
- <b>Kali Linux</b>

<h2>Program walk-through:</h2>



<p align="center">
Nmap the Target Machine:
  *If RDP port does not show up turn it off on windows machine*<br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/main/Screenshot%202024-08-19%20162519.png" height="80%" width="80%"
<br />
<br />
For this example we will be using the reverse tcp payload via msfvenom. Use your attack PC's IP for LHOSTS and 4444 as the port. This will be an execution file disguised as a pdf so we will name it Resume.pdf:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/Screenshot%202024-08-19%20170616.png" height="80%" width="80%"/>
<br />
<br />
Open metasploit, use the multi/handler. Multi/handler: It's a generic payload handler in Metasploit that listens for incoming connections from payloads that you've deployed on target systems.: <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20171915.png" height="80%" width="80%" />
<br />
<br />
Set payload to windows reverse shell and Lhost to attack machine IP:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20172034.png" height="80%" width="80%" />
<br />
<br />
Open new tab and start a web server via python so the target machine can download the service:(Had to steal a screenshot because i forgot to grab one of this)  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/Screenshot%202024-08-19%20183501.png" height="80%" width="80%" />
<br />
<br />
Switch back to original tab and open a shell:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20173248.png" height="80%" width="80%" />
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
