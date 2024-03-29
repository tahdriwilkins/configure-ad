<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This project outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



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

- Setting up the Domain Controller and the Client virtual machines in Microsoft Azure
<br />

<p>
<img width="674" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/58cbf53a-b285-494b-a73b-58d3beb3562a">
</p>

- Now I am ensuring there is connectivity between the domain and the client. I logged into Client-1 and ping DC-1 private IP address and it is not connecting.
<br />

<p>
<img width="1000" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/cb94747a-fe3d-4139-85e0-586d3799abde">
</p>

-  Then I log into DC-1 and adjust the firewall settings so I can ping it and make sure it is connecting. I enabled IMCP to echo so when we log back on ti Client-1, I should receive packets.
<br />

<p>
<img width="674" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/e36dd8c0-b840-41c3-a311-fced82cf4c56">
</p>

-   Now you can see when I log back into Client-1 and ping it again. Instead of being timed out, it is now receiving packets
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
</p>

- Now in the domain I created an Admin and Normal/Employee User account in Active Directory 
<br />

<p>
<img width="1000" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/499e0651-70ef-44d2-82dd-e507fc63653e">
</p>
      
- Then I created a user in the _ADMIN organizational unit named after me. Then I added myself to the "Domain Admins" security group to give me admin access
<br />

<p>
<img width="750" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/38f1782d-c1ce-4a5e-ab0a-3421a9919db3">
  <ul>
      <li> After I log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\tahdri_admin” I will use tahdri_admin as the admin account from now on </li>
  </ul>
</p>
<br />

<p>
<img width="1128" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/29616e4c-8b39-4aed-98a9-7bffab1dc81a">
<img width="1128" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/7f8da877-61fa-4047-b9c8-607fb656d8a7">
  <p>
    <ul>
        <li>Now I am going to join Client-1 to the domain (mydomain.com). From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address</li>
    </ul>
  </p>

<p>
<img width="1128" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/b7e13ff3-1ed2-4df5-b442-ea0c50ce3801">
  <ul>
      <li>Then login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain </li>
 </ul>
</p>

<p>
<img width="825" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/d97bf998-80e8-4149-94ce-4ce99b5d95c0">
  <ul>
      <li>Then login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain</li>
  </ul>
</p>
<br />

<p>
<img width="1128" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/bdc6fc3d-a38b-423d-8d8d-8ccb67f19b52">
</p>
<p>
  <ol>
    <li>Log into Client-1 as mydomain.com\jane_admin and open system properties</li>
    <li>Click “Remote Desktop”</li>
    <li>Allow “domain users” access to remote desktop</li>
    <li>I can now log into Client-1 as a normal, non-administrative user now</li>
  </ol>
</p>
<br />

<p>
<img width="975" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/02ee2ac1-f183-4675-b959-2f6abf259f39">
</p>

<p>
  <ol>
    <li>Login to DC-1 as jane_admin</li>
    <li>Open PowerShell_ise as an administrator</li>
    <li>Then I created a new File and paste the contents of this script into it (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)/li>
  </ol>
</p>

<p>
  <img width="1000" alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/1a32c02b-f478-47c9-8653-111bd273efb2">
  <ul>
    <li>  Then Run the script and observe the accounts being created</li>
  </ul>
</p>

<p>
  <img width="800 alt="image" src="https://github.com/tahdriwilkins/configure-ad/assets/141438778/1d3fd859-c216-42bf-904c-d68c852edd49">
  <ul>
    <li>When finished, open Active Directory Users and Computers and observe the accounts in the _EMPLOYEES Organizational Unit</li>
  </ul>
</p>
<br />

