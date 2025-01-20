<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Preparing AD Infrastructure in Azure</h1>
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

- Part 1 Setup Domain Controller in Azure
- Part 2 Setup Client-1 in Azure
- Part 3 Testing the Enviroment

<h2>Deployment and Configuration Steps</h2>

![image](https://github.com/user-attachments/assets/4edcd31e-145d-418c-b085-c02b138e773f)

![image](https://github.com/user-attachments/assets/8b97b666-63bd-4068-a015-baaaf045da1d)

<p>
Create a Resource Group
</p>
<br />


![image](https://github.com/user-attachments/assets/2268d063-3223-4e1a-a920-a7b17e896bb5)

<p>
Create a Virtual Network and Subnet
</p>
<br />

![image](https://github.com/user-attachments/assets/a881922b-1b85-439a-acb1-54dce2cf4a74)

<p>
Create the Domain Controller VM (Windows Server 2022) named “DC-1” Size = Processing speed of VM
</p>
<br />


![image](https://github.com/user-attachments/assets/071ce730-d228-4412-92dc-acf5f8ccd903)

<p>
- Username: Labuser1
  </p>
- Password: Labpassword1
</p>
<br />


![image](https://github.com/user-attachments/assets/d4e30e71-de6c-4b26-822d-81250469e3c4)

![image](https://github.com/user-attachments/assets/a6a84c56-ef1c-4d4f-8001-f4487b290495)

<p>
In Networking tab, Make sure the newly created Vnet is selected, then Create
</p>
<br />


![image](https://github.com/user-attachments/assets/42174e2d-e08d-4681-ba37-e753b0a12c3a)

<p>
Create the Client VM (Windows 10) named “Client-1”
</p>
<br />


![image](https://github.com/user-attachments/assets/7c2f2ea8-bfb9-47ef-bf1e-30c08bbb0b8a)

<p>
In Networking tab, Make sure the newly created Vnet is selected, then Create
</p>
<br />


![image](https://github.com/user-attachments/assets/a1927aca-558f-4f95-9946-b46b8de4b99f)

![image](https://github.com/user-attachments/assets/bd8a3094-9540-4703-a385-ee12e2ad1b51)

<p>
After VM is created, set Domain Controller’s NIC Private IP address to be static
</p>
<br />


![image](https://github.com/user-attachments/assets/f239703e-8f60-47b8-beb4-68b03b476c5a)

<p>
Use Remote Desktop Protocol to Log into the DC-1 
</p>
<br />

![image](https://github.com/user-attachments/assets/91370c17-bafe-437f-85b9-8bf4dc2c338a)

<p>
Run > wf.msc
</p>
<br />

![image](https://github.com/user-attachments/assets/e1878d3a-aa96-41bf-81d6-c056cbabe82f)

<p>
Select Firewall Properties
</p>
<br />

![image](https://github.com/user-attachments/assets/8b9be272-5053-4258-b681-bf28c6f7cb47)

![image](https://github.com/user-attachments/assets/9feb4a87-ea43-4fd7-a59a-e2cfe86272fd)

![image](https://github.com/user-attachments/assets/9f956812-2a99-4868-8378-f8f718a048c4)

<p>
Disable the Domain, Private, Public Profile’s Firewall, then Apply
</p>
<br />

![image](https://github.com/user-attachments/assets/b7309316-747f-4ce2-a582-3e4a068ec14c)

![image](https://github.com/user-attachments/assets/34515651-a8a9-4de2-852d-51d7b11d448f)

<p>
Configure Client-1’s DNS settings to DC-1’s Private IP address
</p>
<br />

![image](https://github.com/user-attachments/assets/a0cb415b-f232-432e-bc91-c40be3020f66)

<p>
From the Azure Portal, restart Client-1
</p>
<br />

![image](https://github.com/user-attachments/assets/a5b142f7-276b-4581-8fc8-435542a0b005)

![image](https://github.com/user-attachments/assets/a0519f3f-c9fc-403f-b53f-910ba29a4b7a)

<p>
Use Remote Desktop Protocol to Log into Client-1 using the public IP
</p>
<br />

![image](https://github.com/user-attachments/assets/f50b10d4-1fc4-45ad-963a-bcbef098e5aa)

![image](https://github.com/user-attachments/assets/7414c674-2ecd-4c00-b235-c48865f0c903)

<p>
From Client-1, open PowerShell and run ping 10.0.0.4
</p>
<br />

![image](https://github.com/user-attachments/assets/19d22fb5-ce6f-4032-9701-e1124827d1c9)

<p>
Run ipconfig /all 
</p>
The output for the DNS settings should show DC-1’s private IP Address
</p>
<br />

<p>
Preparing AD Infrastucture in Azure, Complete
</p>
<br />

