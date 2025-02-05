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
<ul>
        <li>Installed VirtualBox and downloaded Windows 10 and Windows Server 2019 ISO files</li>
      </ul>
<br/>

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
<img src="https://i.imgur.com/7hOPjeH.png" height="80%" width="80%" alt=""/>
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
<br/> 
Naming the NAT<br/>
  <img src="https://i.imgur.com/MwSiJCU.png" height="80%" width="80%" alt=""/>
<br />
<br/>
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
<br />
Installing Active Directory.  On the right we can see that the AD has been created <br/>
<img src="https://i.imgur.com/qnYOTcB.png" height="80%" width="80%" alt=""/>
<br />
<br />
Creating my own DOMAIN (instead of using the built in domain account) <br/>
<img src="https://i.imgur.com/zeXQ0ua.png" height="80%" width="80%" alt=""/>
<br />

<br />
<ul>
     <li><b>Creating Organizational Units (OUs) & User Accounts :</b>
      <ul>
        <li>>Created a new Organizational Unit (OU) to manage users.</li>
        <li>Added a new Admin User (instead of using the built-in domain admin).</li>
       <li>Assigned the user Domain Admin privileges </li>
      </ul>
</ul>
<br />
Creating OU  <br/>
<img src="https://i.imgur.com/fHsAU19.png" height="80%" width="80%" alt=""/>
<br />
<br />
Create new user in _ADMINS <br/>
<img src="https://i.imgur.com/Ft8zAea.png" height="80%" width="80%" alt=""/>
<br />
<br />
Adding USER to make the it the ADMIN of the domain <br/>
<img src="https://i.imgur.com/5houEEu.png" height="80%" width="80%" alt=""/>

<br />
<ul>
     <li><b>Configuring RAS/NAT for Internet Access :</b>
      <ul>
        <li>Installing and configuring Routing and Remote Access (RAS) with NAT. The purpose of installing Routing and Remote Access Service (RAS) with NAT is to enable the Windows 10 CLIENT machine to connect to the private virtual network while still having internet access. By configuring RAS/NAT on the domain controller, the client machine can communicate within the private network while routing external traffic through the domain controller to access the internet.</li>
      </ul>
</ul>
<br />
Configuring Routing and Remote Access <br/>
<img src="https://i.imgur.com/fm3CzTD.png" height="80%" width="80%" alt=""/>
<br />

<br />
<ul>
     <li><b>Setting Up DHCP :</b>
      <ul>
        <li>Installed DHCP Server on the DC.</li>
       <li>Configured a DHCP scope to automatically assign IP addresses to client machines.</li>
      </ul>
</ul>
<br />
Configuring DHCP with the IP addresses <br/>
<img src="https://i.imgur.com/VYX87gb.png" height="80%" width="80%" alt=""/>
<br />

<br />
<br />
<ul>
     <li><b>Automating User Creation :</b>
      <ul>
        <li>Run a PowerShell script to create 1,000 Active Directory user accounts.</li>
      </ul>
</ul>
<br />
PowerShell Script Running <br/>
<img src="https://i.imgur.com/00oeDFR.png" height="80%" width="80%" alt=""/>
<br />
</p>


<br/>
<h3>Step 3: Configuring the Client Machine  </h3> 
<p align="center">

 <ul>
     <li><b>Automating User Creation :</b>
      <ul>
        <li>Installed Windows 10 on CLIENT1 and connected it to the private VirtualBox network.</li>
       <li>Joined CLIENT1 to the DC.</li>
       <li>Logged into CLIENT1 using a domain account created in AD (using the Powershell script).</li>
      </ul>
</ul>
<br />
Client Machine Joining the Domain
<img src="https://i.imgur.com/6VbNdFk.png" height="80%" width="80%" alt=""/>
<br />
</p>



<h3>Step 4: Verifying Configuration </h3> 
<p align="center">

 <ul>
     <li><b>Automating User Creation :</b>
      <ul>
        <li>Our client computer has obtained a DHCP lease. When we created and joined the client machine to the network, it automatically contacted the DHCP server to request an IP address. The DHCP server then assigned an address, and we can now see the active lease in the system.</li>
      </ul>
</ul>
<br />
DHCP Lease Verification
<img src="https://i.imgur.com/9N1XZPs.png" height="80%" width="80%" alt=""/>
<br />

<br/>
 <ul>
     <li><b>Automating User Creation :</b>
      <ul>
        <li>Run <b>whoami</b> on the command line to verify the user was authenticated under the domain</li>
      </ul>
</ul>
<br />
CMD showing 'whoami' Output with my username
<img src="https://i.imgur.com/wmaGLMW.png" height="80%" width="80%" alt=""/>
<br />
</p>

<h2>Final Thoughts</h2>
    <p>
        This project allowed me to gain hands-on experience with Active Directory, DNS, DHCP, NAT, and enterprise networking. The successful setup of a fully functional domain environment reinforced my knowledge of IT infrastructure and Windows Server administration.
     <h3>Skills Achieved: </h3>
    <ul>
        <li>Virtualization & Networking (VirtualBox, NAT, DHCP)</li>
        <li>Windows Server Administration (Active Directory, DNS, Group Policy)</li>
        <li>Security & User Management (Domain Controllers, Organizational Units, Admin Privileges)</li>
        <li>Automation with PowerShell</li>
    </ul>
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
