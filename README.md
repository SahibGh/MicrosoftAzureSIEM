<h1>Setting up SIEM using Microsoft Azure with live cyberattacks</h1>

<h2>Description</h2>
This project involves creating a honeypot using Microsoft Azure. A live virtual machine will be set up to act as the honeypot, designed to attract and log potential cyberattacks. Azure Sentinel is the SIEM and will be connected to the Virtual Machine to monitor incoming attacks. We will observe and log live attacks from around the world in real-time. Then a PowerShell script to determine the geolocation of the attackers. The geolocation data will then be visualized on a map using the built-in visualization features of Azure Sentinel. This will help us gain insights into the geographic distribution of the attacks.
<br />

<h2>Services and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>PowerShell</b> 

<h2>Microsoft Azure features Used </h2>

- <b>Virtual Machines</b> 
- <b>Log Analytics Workspaces</b>
- <b>Microsoft Defender for Cloud</b>
- <b>Microsoft Sentinel</b>

<h2>Project Walkthrough:</h2>

<p align="center">
1. : <br/>
<img src="https://imgur.com/ukLUUvr.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
2. This is Microsoft Azure, a cloud computing platform. The services and tools they provide will be used in this project:  <br/>
<img src="https://imgur.com/2wDKDy8.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
3. First create a new virtual machine:  <br/>
<img src="https://imgur.com/kbRTMnH.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
4. This is the virtual machine that will be exposed to the internet, people from other countries will try to attack it:  <br/>
<img src="https://imgur.com/mfxDz23.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
5. In the networking settings a new rule is added to make it so that everything is allowed into the vm:  <br/>
<img src="https://imgur.com/SzRxnog.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
6. Now create the virtual machine:  <br/>
<img src="https://imgur.com/NduSwtw.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
7. It is now deploying:  <br/>
<img src="https://imgur.com/3vuvDuk.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
8. Next we need to make a log analytics workspace:  <br/>
<img src="https://imgur.com/eNrE8IY.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
9. This is used for taking in and storing logs from the virtual machine:  <br/>
<img src="https://imgur.com/LzJf6qh.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
10. It is now deploying: <br/>
<img src="https://imgur.com/oJIfLBI.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
11. Now go to Microsoft Defender for cloud on Azure, this is what will enable the ability to gather logs from the virtual machine ot the loig analytics workspace:  <br/>
<img src="https://imgur.com/b592qp8.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
12. Kept everything on except for SQL servers since they won't be in use:  <br/>
<img src="https://imgur.com/5WBFaf2.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
13. Under Data Collection, select All Events:  <br/>
<img src="https://imgur.com/vK55aSE.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
14. In Log Analytics workspace, navigate to our Virtual Machine:  <br/>
<img src="https://imgur.com/9Co1FNX.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
15. Click connect to connect the Log Analytics workspace and our Virtual Machine:  <br/>
<img src="https://imgur.com/L7awxCF.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
16. Now we go to Azure Sentinel, which is the SIEM that will be used to visualise the data of the attack :  <br/>
<img src="https://imgur.com/Qx4Uods.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
17. Select the Workspace that we've connected to the Virtual Machine:  <br/>
<img src="https://imgur.com/wEnFBK2.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
18. Now return to the Virtual Machine, and copy the Public IP Address that has been generated:  <br/>
<img src="https://imgur.com/pOhHbbq.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
19. Enter that IP Address into remote desktop and enter the credentials created when the Virtual Machine was created:  <br/>
<img src="https://imgur.com/abzpyUn.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
20. Logging in: <br/>
<img src="https://imgur.com/1Gdl4fx.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
21. Once logged in, go to the Start menu and go to Event Viewer:  <br/>
<img src="https://imgur.com/VL4cnAz.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
22. These are all security events that have occured on the Virtual Machine, we are going to the be focussing on the login failures:  <br/>
<img src="https://imgur.com/huHQj2R.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
23. If we tried to ping the Virtual Machine from our normal machine it wont work:  <br/>
<img src="https://imgur.com/pD1gnRF.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
24. Open Windows Defender Firewall and turn off the firewall completely:  <br/>
<img src="https://imgur.com/aALpzPN.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
25. Now the ping from our own machine should work, this means the Virtual Machine is exposed:  <br/>
<img src="https://imgur.com/fefiI5O.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
26. This script grabs the IP address of people who failed to log in from the Event Viewer logs and gets the geodata, creating a log file:  <br/>
<img src="https://imgur.com/i5BCMZ0.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
27. The script is opened in powershell:  <br/>
<img src="https://imgur.com/CdsMWGx.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
28. This website is used track the details of the attacks, for example, country, state, city, latitude and longitude. Once an API key is generated enter it into the script in Powershell:  <br/>
<img src="https://imgur.com/J5Z7EvT.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
29. When the script is run, the failed login attempts will be displayed as the output: <br/>
<img src="https://imgur.com/vtcgHlh.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
30. This file failed_rdp has sample data to train Analytics Workspace with the bottom three being real attempts from myself:  <br/>
<img src="https://imgur.com/cOWMmg4.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
31. Create the same file with the same contents on your own machine:  <br/>
<img src="https://imgur.com/Vj8Vx38.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
32. Now we are going to create a custom log with the file to be able to bring the geodata into our Workspace:  <br/>
<img src="https://imgur.com/t0DADMq.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
33. Add the failed_rdp.log as a sample:  <br/>
<img src="https://imgur.com/A5DLtDk.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
34. Enter the path of the file within the Virtual Machine:  <br/>
<img src="https://imgur.com/7Nfma5r.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
35. It has been created and now all the events are being displayed:  <br/>
<img src="https://imgur.com/NR9ERaU.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
36. All of the data from the sample log as well as our three failed attempted are being displayed:  <br/>
<img src="https://imgur.com/QI0COQP.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
37. With this script the data will be displayed with several fields that show the data of each event:  <br/>
<img src="https://imgur.com/R0Idxz0.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
38. Within Sentinel, the workbook feature is going be used to create a visualation of the attacks:  <br/>
<img src="https://imgur.com/b0CE9XN.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
39. Reenter the script used before to create this query:  <br/>
<img src="https://imgur.com/gybDTIp.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
40. Change the visualation to world map and it will display the location of each attack:  <br/>
<img src="https://imgur.com/FcsPvDg.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
41. This is how it looks:  <br/>
<img src="https://imgur.com/n3oJ3XO.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
42. After waiting while new events have appeared indicating that some people have attempted to attack the Virtual Machine:  <br/>
<img src="https://imgur.com/8PaDqo8.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
43. This is what the map now looks like, 199 attacks from Netherlands and 2 from Morocco:  <br/>
<img src="https://imgur.com/8vArZrt.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
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
