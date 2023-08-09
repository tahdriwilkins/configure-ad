<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Microsoft Azure
- Ensure Connectivity between the Client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User account in Active Directory
- Join Client-1 to Domain
- Setup Remote Desktop for non-aministrative users on Client-1
- Create a bunch of additional users and attempt to log into Client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1128" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/8580c5d8-ee1a-4c35-b237-c56014a6050f">
</p>
<p>
Setting up the Domain Controller and the Client virtual machines in Microsoft Azure</p>
<br />

<p>
<img width="674" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/58cbf53a-b285-494b-a73b-58d3beb3562a">
<img width="1000" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/cb94747a-fe3d-4139-85e0-586d3799abde">
<img width="674" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/e36dd8c0-b840-41c3-a311-fced82cf4c56">

</p>
<p>
<ol>
  <li>Now I am ensuring there is connectivity between the domain and the client. I logged into Client-1 and ping DC-1 private IP address and it is not connecting.</li>
  <li>In the next picture, I log into DC-1 and adjust the firewall settings so I can ping it and make sure it is connecting. I enabled IMCP to echo so when we log back on ti Client-1, I should receive packets.</li>
  <li>In the third picture you can see that I log back into Client-1 and ping it again. Instead of being timed out, it is now receiving packets</li>
</ol> 
</p>
<br />

<p>
<img width="700" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/611bb925-c6a3-4949-96af-080819ebdc32">
<img width="918" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/80c2df9f-aa1f-497c-8a5b-110650c33870">

</p>
<p>
<ol>
  <li>Now I will be installing Active Directory to DC-1</li>
  <li>In the second picture, I clicked on the flag to promote this server into a domain controller. Then I go through the rest of the configuration process</li>
</ol>
</p>
<br />

<p>
<img width="978" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/7ef0dae9-ac59-49d5-8fe6-89f7a37b1e81">
<img width="1000" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/499e0651-70ef-44d2-82dd-e507fc63653e">

</p>
<p>
<ol>
  <li> Now in the domain I created an Admin and Normal/Employee User account in Active Directory </li>
  <li> Then I created a user in the _ADMIN organizational unit named after me. Then I added myself to the "Domain Admins" security group to give me admin access</li>
  <li> After I log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\tahdri_admin” I will use tahdri_admin as the admin account from now on </li>
</ol>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

