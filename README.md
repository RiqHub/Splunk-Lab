# Splunk-Lab

*ATTENTION* 
To set up the two machines you need you can use these two videos: 
- [Lab Prep Vid 1](https://www.youtube.com/watch?v=kku0fVfksrk&list=PLG6KGSNK4PuBWmX9NykU0wnWamjxdKhDJ&index=1)
- [Lab Pred Vid 2](https://www.youtube.com/watch?v=5iafC6vj7kM&list=PLG6KGSNK4PuBWmX9NykU0wnWamjxdKhDJ&index=3)



<h2>Description</h2>
This project intendds to show how a SOC analyst would go about identifying malware on 
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Splunk</b>
  - [Installation Tutorial](https://www.youtube.com/watch?v=iaBJ-PK8_RI)
- <b>Metasploit</b>
- <b>Nmap</b>
- <b>Sysmon</b>
  - [Installation Tutorial](https://www.youtube.com/watch?v=uJ7pv6blyog)

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
Perform a couple commands in order to get some Telemetry:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20173326.png" height="80%" width="80%" />
<br />
<br />
Switch back to original tab and open a shell:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20173248.png" height="80%" width="80%" />
<br />
<br />
Switch to Windows machine and turn off realtime protection in Windows defender:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/Screenshot%202024-08-19%20172611.png" height="80%" width="80%" />
<br />
<br />
Open a web browser and go to the attackers web directory and download and run the Resume file:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/Screenshot%202024-08-19%20172725.png" height="80%" width="80%" />
<br />
<br />
Follow the file path below and delete the input file and insert the input file in this respitory. This will aloow you to get the sysmon features in the index:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20173435.png" height="80%" width="80%" />
<br />
<br />
Open services and restart the splunkd service:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20173612.png" height="80%" width="80%" />
<br />
<br />
Login to Splunk and got to settings > search reports and alerts:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20180801.png" height="80%" width="80%" />
<br />
<br />
Create a new index named endpoint:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20181014.png" height="80%" width="80%" />
<br />
<br />
Under apps we will search sysmon and install "Splunk add on for Sysmon":  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20181120.png" height="80%" width="80%" />
<br />
<br />
Go backto Search and reporting and search "index=endpoint Resume.pdf.exe. Expand the first event, scroll down to process_guid, copy the value, remove resume.pdf and add it to the search:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20181506.png" height="80%" width="80%" />
<br />
<br />
Refine the search using a pipe and "table". Use the search provided below and you will be able to see the commands you used when you opened the shell:  <br/>
<img src="https://github.com/RiqHub/Splunk-Lab/blob/Pictures/splunk%20lab/Screenshot%202024-08-19%20181537.png" height="80%" width="80%" />
<br />
<br />
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
