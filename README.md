<h1>Setting up SIEM using Microsoft Azure with live cyberattacks</h1>

<h2>Description</h2>
This project involves a walkthrough on creating a simple Active Directory home lab using Oracle Virtualbox. By configuring and running the lab, you gain an understanding of how the service works, as well as the networking principles behind it. In this project, a server with the necessary networking settings and features will be set up, along with a script to generate 1000 users for demonstration purposes. The result will be tested in a separate environment acting as a client or user trying to login with their new credentials.
<br />

<h2>Languages and Utilities Used</h2>

- <b>Oracle VM VirtualBox</b>
- <b>PowerShell</b> 

<h2>Environments Used </h2>

- <b>Windows 10 ISO</b> 
- <b>Server 19 ISO</b>

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
6. In the networking settings a new rule is added to make it so that everything is allowed into the vm:  <br/>
<img src="https://imgur.com/SzRxnog.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
7. Now create the virtual machine:  <br/>
<img src="https://imgur.com/NduSwtw.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
8. It is now deploying:  <br/>
<img src="https://imgur.com/3vuvDuk.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
9. Next we need to make a log analytics workspace:  <br/>
<img src="https://imgur.com/eNrE8IY.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
10. This is used for taking in and storing logs from the virtual machine:  <br/>
<img src="https://imgur.com/LzJf6qh.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
11. It is now deploying: <br/>
<img src="https://imgur.com/oJIfLBI.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
12. Now go to Microsoft Defender for cloud on Azure, this is what will enable the ability to gather logs from the virtual machine ot the loig analytics workspace:  <br/>
<img src="https://imgur.com/b592qp8.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
13. Kept everything on except for SQL servers since they won't be in use:  <br/>
<img src="https://imgur.com/5WBFaf2.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
14. Under Data Collection, select All Events:  <br/>
<img src="https://imgur.com/vK55aSE.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
15. In Log Analytics workspace, navigate to our Virtual Machine:  <br/>
<img src="https://imgur.com/9Co1FNX.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
16. Click connect to connect the Log Analytics workspace and our Virtual Machine:  <br/>
<img src="https://imgur.com/L7awxCF.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
17. Now we go to Azure Sentinel, which is the SIEM that will be used to visualise the data of the attack :  <br/>
<img src="https://imgur.com/Qx4Uods.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
18. Select the Workspace that we've connected to the Virtual Machine:  <br/>
<img src="https://imgur.com/wEnFBK2.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
19. Now return to the Virtual Machine, and copy the Public IP Address that has been generated:  <br/>
<img src="https://imgur.com/pOhHbbq.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
20. Enter that IP Address into remote desktop and enter the credentials created when the Virtual Machine was created:  <br/>
<img src="https://imgur.com/abzpyUn.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
21. Logging in: <br/>
<img src="https://imgur.com/1Gdl4fx.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
22. Once logged in, go to the Start menu and go to Event Viewer:  <br/>
<img src="https://imgur.com/VL4cnAz.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
24. These are all security events that have occured on the Virtual Machine, we are going to the be focussing on the login failures:  <br/>
<img src="https://imgur.com/huHQj2R.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
25. If we tried to ping the Virtual Machine from our normal machine it wont work:  <br/>
<img src="https://imgur.com/pD1gnRF.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
26. Open Windows Defender Firewall and turn off the firewall completely:  <br/>
<img src="https://imgur.com/aALpzPN.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
27. Now the ping from our own machine should work, this means the Virtual Machine is exposed:  <br/>
<img src="https://imgur.com/fefiI5O.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
28. This script grabs the IP address of people who failed to log in from the Event Viewer logs and gets the geodata, creating a log file:  <br/>
<img src="https://imgur.com/i5BCMZ0.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
29. The script is opened in powershell:  <br/>
<img src="https://imgur.com/CdsMWGx.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
30. This website is used track the details of the attacks, for example, country, state, city, latitude and longitude. Once an API key is generated enter it into the script in Powershell:  <br/>
<img src="https://imgur.com/J5Z7EvT.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
31. When the script is run, the failed login attempts will be displayed as the output: <br/>
<img src="https://imgur.com/vtcgHlh.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
32. This file failed_rdp has sample data to train Analytics Workspace with the bottom three being real attempts from myself:  <br/>
<img src="https://imgur.com/cOWMmg4.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
33. Create the same file with the same contents on your own machine:  <br/>
<img src="https://imgur.com/Vj8Vx38.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
34. Now we are going to create a custom log with the file to be able to bring the geodata into our Workspace:  <br/>
<img src="https://imgur.com/t0DADMq.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
35. Add the failed_rdp.log as a sample:  <br/>
<img src="https://imgur.com/A5DLtDk.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
36. :  <br/>
<img src="https://imgur.com/Hss3W76.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
37. :  <br/>
<img src="https://imgur.com/7Nfma5r.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
38. :  <br/>
<img src="https://imgur.com/nTtrpgZ.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
39. :  <br/>
<img src="https://imgur.com/Ju3oDgJ.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
40. :  <br/>
<img src="https://imgur.com/NR9ERaU.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
41. :  <br/>
<img src="https://imgur.com/onTcGP8.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
42. :  <br/>
<img src="https://imgur.com/QI0COQP.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
43. :  <br/>
<img src="https://imgur.com/R0Idxz0.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
44. :  <br/>
<img src="https://imgur.com/b0CE9XN.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
45. :  <br/>
<img src="https://imgur.com/gybDTIp.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
46. :  <br/>
<img src="https://imgur.com/FcsPvDg.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
47. :  <br/>
<img src="https://imgur.com/n3oJ3XO.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
48. :  <br/>
<img src="https://imgur.com/8PaDqo8.png" height="80%" width="80%" alt="Microsoft Azure SIEM Steps"/>
<br />
<br />
49. :  <br/>
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
