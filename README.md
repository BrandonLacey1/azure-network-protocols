<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Network File Shares and Permission 

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create some sample file shares with various permissions
- On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”
- Attempt to access file shares as a normal user

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/HDhYuov.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log back on to your DC PC and choose a random user and once you pick that user, I used his information to login into Client one since all EMPLOYEES have access.
</p>
<br />

<p>
<img src="https://i.imgur.com/tWQEaln.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next on the DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”. 
</p>
<br />

<p>
<img src="https://i.imgur.com/oCSon6e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Then set the following permissions (share the folder) for the “Domain Users” group:
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
Repeat the same process for the others.
</p>
<br />

<p>
<img src="https://i.imgur.com/N2PVJX9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On Client-1, navigate to the shared folder (start, run, \\dc-1). This will take you too the shared folders. We are a normal user.
</p>
<br />

<p>
<img src="https://i.imgur.com/TuXLbYv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
These are the shared folders
</p>
<br />

<p>
<img src="https://i.imgur.com/hIZMZSA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This shows that the user doesn’t have permission. The user can't access the no-access folder. 
</p>
<br />

<p>
<img src="https://i.imgur.com/R5UZIue.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The same for this as well. The user can't access the read-access folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/RmlPj8z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
But however in the write-access, the user can access it. Therefore this user on has access to write-access and nothing else.
</p>
<br />
