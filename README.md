<h1>Deploying Honeypot on Azure Virtual Machine with</h1>

<h2>Description</h2>
This project aims to facilitate the deployment of a Honeypot on a virtual machine hosted in the Azure cloud environment. The Honeypot will serve as a decoy system, designed to attract and identify potential cybersecurity threats and attack vectors, thus bolstering the overall security posture.

The project leverages Azure's infrastructure to create and manage the virtual machine, ensuring scalability and reliability. Connection to the virtual machine is established using Putty, a widely-used SSH client for Windows, enabling secure remote access and administration.

The Git repository contains detailed documentation and scripts for deploying the Honeypot, configuring the virtual machine. Additionally, it provides insights into monitoring and analyzing the captured data to gain valuable threat intelligence.

This project aims to gain hands-on experience in deploying and managing a Honeypot in a cloud environment, enhancing understanding of cybersecurity defense strategies and threat detection techniques.
<br />


<h2>Utilities Used</h2>

- [<b>T-pot</b> ](https://github.com/telekom-security/tpotce)
- [<b>puppy</b>](https://www.putty.org)

<h2>Environments Used </h2>

- <b>VM hosted in Azure</b>

<h2>Project walk-through:</h2>

<p align="center">
First, let's proceed with creating our virtual machine (VM). To begin, navigate to portal.azure.com. Upon arrival, locate and select the 'Virtual Machines' option. You may also conduct a search to find this feature. Once selected, you will be redirected to a new page where you can initiate the process of creating your virtual machine and proceed with the setup. <br/>
<img src="https://i.imgur.com/rj7v2VS.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center"> First and foremost, we must create a resource group, naming it 'Honeypot.' Consider the option to modify the operating system to ensure compatibility with the honeypot, which is specifically designed to run on Debian. Proceed with selecting this operating system, and maintain the default architecture. Ensure that SSH is selected, as it will be essential for future connections to the virtual machine.

<p align="center">Additionally, consider leveraging the Azure spot discount to potentially reduce the overall cost of the VM. Subsequently, it is crucial to determine the appropriate size for our VM. Explore all available sizes by clicking the respective option.

<p align="center">While the official documentation suggests a minimum of eight gigabytes, based on my experience, this setup may result in suboptimal performance and limited usability. Therefore, it is advisable to select 16 gigabytes. Furthermore, for the version, I will opt for the D4 d4 as version three.   <br/>

<img src="https://i.imgur.com/aqUCnCv.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next, we will proceed to configure the disk settings. Click on the "Next" button to continue. It is essential to create disks with a minimum capacity of 128 gigabytes. To achieve this, select the option to create and attach a new disk. Then, click on the "change size" option and specify the capacity as 128 gigabytes. Confirm the selection by clicking "Okay." <br/>
<img src="https://i.imgur.com/rFnESM9.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now, we can proceed to the networking section. Upon doing so, a new virtual network subnet and public IP address will be automatically generated. No further adjustments are necessary in this section. Once these configurations are in place, we are prepared to proceed with the creation of the virtual machine. <br/>
<img src="https://i.imgur.com/wBYg8T2.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now that we have completed the creation process in the Azure Portal, let's proceed with the configuration. Before exiting the Azure portal, it is essential to open specific ports to facilitate the subsequent steps. <br/>
<img src="https://i.imgur.com/5yszFLh.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
To simplify the process, we will open all ports to enable both incoming and outgoing connections to our port.

To begin, click on "Go to resource" and navigate to the networking section.

To open the ports, add an inbound rule and specify the entire range from 0 to 65,535 to keep it simple. Set the source destination to any service, choose the custom service, set the action to "allow," and click "Add" to create a new security rule. <br/>
<img src="https://i.imgur.com/kyiLt49.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The final step is to connect to our VM using Putty. Begin by obtaining the IP address of your VM, which can be found in the overview section of your virtual machine. Once you have the IP address, proceed to open Putty.<br/>
<img src="https://i.imgur.com/TOA3Oxt.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Upon receiving your Azure account's username and password, proceed to update the package list and upgrade the system by running the following basic commands:  Begin by typing "sudo apt update". Next, upgrade the packages using "sudo apt upgrade". After that, install Git to download the T-Pot into our machine. For this, refer to the original Git documentation of T-Pot, which can be found at [https://github.com/telekom-security/tpotce](https://github.com/telekom-security/tpotce). Additionally, all the commands are available in a text file within our repository. <br/>
<img src="https://i.imgur.com/VmW80ru.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
At a certain stage, a screen resembling the one depicted in the image will appear. Upon encountering this, proceed to confirm by selecting "Yes" and opt for the standard version. Subsequently, confirm your selection by pressing "Enter". Following this, you will be prompted to input your username and password, which will serve as the credentials for logging into the T-Pot console at a later stage. <br/>
<img src="https://i.imgur.com/psEMDSF.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The pod has been successfully deployed on the Microsoft Azure Cloud platform. You may now proceed to close the window. <br/>
<img src="https://i.imgur.com/TdgWi1c.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We can now access our T-Pot by using the IP address obtained from Azure, adding port 64297. Upon accessing the site, we will be prompted to enter the credentials set during the installation process of T-Pot. <br/>
<img src="https://i.imgur.com/aXEEcqm.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Allow me to provide an overview of each feature, following which we will delve into a more in-depth exploration.

First, we have the Attack Map, which presents a live visualization of the geographic locations of attackers and the types of attacks being directed at your honeypot.

Next, we have the Cockpit, which serves as the primary dashboard for your T-Pot honeypot. It furnishes a real-time view of the honeypot activity, including the number of attacks, top attackers, and the most targeted services.

Moving on, the Cyber Chef is a web-based tool that enables the analysis and decoding of data. It is seamlessly integrated into T-Pot, allowing for the analysis of captured traffic and the identification of patterns.

The Elastic View, on the other hand, serves as an Elastic Search client that facilitates the visualization of the data collected by T-Pot. This tool enables the search for specific events and the display of results in various visual formats.

Nibbana, another integrated tool, aids in visualizing the data collected by the honeypot. It empowers users to create custom dashboards and reports based on the collected data.

Lastly, Spider Foot, a reconnaissance tool, supports open-source intelligence (OSINT) gathering. It enables the collection of information about potential attackers from publicly available sources, encompassing IP addresses, domains, email addresses, and more. <br/>
<img src="https://i.imgur.com/rgjDrCa.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a new virtual machine within VirtualBox and configure the necessary settings such as memory, CPU, and network adapters: <br/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
