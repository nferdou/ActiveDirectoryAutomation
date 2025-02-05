# ActiveDirectoryAutomation

 ### [YouTube Demonstration](https://)

<h2>Description</h2>
The project involved creating PowerShell scripts to automate the provisioning, maintenance, and deprovisioning of user accounts in Active Directory on Windows Server. The project also included configuring Remote Access Server (RAS) features to support NAT/PAT, implementing Windows DNS and DHCP services, and setting up Windows File Servers with quotas and NTFS permissions. The environment was set up using Oracle VirtualBox to simulate and test the configurations.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>  
- <b>Active Directory</b>  

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Oracle VirtualBox</b>

<h2>Project Setup Diagram</h2>
<img src="https://i.imgur.com/ONp1J3x.png" height="80%" width="80%" alt=""/>




<h2>Program walk-through:</h2>

<h3>Step 1: Setting Up Virtual Machines</h3> <br/>
- Installed VirtualBox and downloaded Windows 10 and Windows Server 2019 ISO files <br/>

<h3>Step 2: Configuring the Domain Controller </h3> <br/>
<ul>
        <li><b>Network Adapter Setup:</b>
            <ul>
                <li><b>Adapter 1:</b> External internet connection.</li>
                <li><b>Adapter 2:</b> Private VirtualBox network for internal communication.</li>
            </ul>
        </li>
    </ul>
<p align="center">
DC Network Adapter Configuration
<img src="https://imgur.com/ionRqbx.png" height="80%" width="80%" alt=""/>
<br />
 
<br />
    <ul>
     <li><b>Installing Windows Server 2019:</b>
      <ul>
        <li>Set up the internal NAT manually. Here I identified the network, the home IP and the Internet and named it as _INTERNET_ (internet) and X_internet_X(home IP)</li>
      <li>Assigned static IP addresses for internal networking. </li>
      </ul>
    </ul>
    <br/>
 
  Naming the NAT<br/>
  <img src="https://i.imgur.com/OjJ3FVA.png" height="80%" width="80%" alt=""/>
<br />
Assigned static IP addresses  <br/>
<img src="https://i.imgur.com/CpoWE7o.png" height="80%" width="80%" alt=""/>
<br />

<br />
<ul>
     <li><b>Installing & Configuring Active Directory :</b>
      <ul>
        <li>Promoted the server to a Domain Controller.</li>
        <li>Created a custom Active Directory Domain.</li>
      </ul>
    </ul>
Installing Active Directory. On the right we can see that the AD has been created <br/>
<img src="https://i.imgur.com/qnYOTcB.png" height="80%" width="80%" alt=""/>
<br />
<br />
Creating my own DOMAIN (instead of using the built in domain account) <br/>
<img src="https://i.imgur.com/zeXQ0ua.png" height="80%" width="80%" alt=""/>
<br />
<br />
step  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
<br />
<br />
step:  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
<br />
<br />
step:  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
</p>

<h3>Step 3: Configuring the Client Machine  </h3> <br/>
<p align="center">
DC Network Adapter Configuration
<img src="https://imgur.com/ionRqbx.png" height="80%" width="80%" alt=""/>
<br />
<br />
step  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
<br />
<br />
steps: <br/>
<img src="https://" height="80%" width="80%" alt=""/>
<br />
<br />
step:  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
<br />
<br />
step  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
<br />
<br />
step:  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
<br />
<br />
step:  <br/>
<img src="https://" height="80%" width="80%" alt=""/>
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
