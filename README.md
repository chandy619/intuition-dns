<p align="center">
<img width="171" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/56212e77-8a1c-4b27-835d-325553023ae7"
>
</p>

<h1>Understanding Domain Name System (DNS)</h1>
This lab focuses on building intuition for DNS and how it works. DNS is a fundamental system that enables the translation of human-readable domain names into numerical IP addresses, facilitating the communication between devices on the internet. Picking up from the last tutorial, I will be logged in as Jane Doe (Admin User) on both the Client-1 and Domain Controller (DC-1) VMs. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Command Prompt

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>HIgh-level Steps</h2>

- Inspect DNS A-Records on the server (hostname to IP address mappings)
- Create A-records on the server and observe from Client-1
- Delete records from server and inspect/ clear Client-1 DNS cache
- Touch on 'CNAME' records (mapping one name to the another)

<h2>DNS Configuration Steps</h2>
<p>
<img width="357" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/8acc133b-6f5c-4f04-b7ec-b3323c17af97">

</p>
<p>
We'll begin with opening Command in Client-1. Enter 'ping mainframe'. The request will fail because the local computer essentially does not have  an IP address for 'mainframe'. Therefore, we will create an A-record for mainframe.
</p>
<br />

<p>
<image>
</p>
<p>
Switching to DC-1, open Server Manager from the Start menu. Click on 'Tools' located at the top right corner of the window and select 'DNS'. click on DC-1 on your left-hand side, select the folder labeled 'Foward Lookup Zones' which will expand for you to select the 'mydomain.com' folder. From here, right-click in the space to the right for a list of options; select 'New Host (A OR AAAA)...'
</p>
<br />

<p>
<image>
</p>
<p>
Text
</p>
<br />

<p>
<image>
</p>
<p>
Text
</p>
<br />

<p>
<image>
</p>
<p>
Text
</p>
<br />
