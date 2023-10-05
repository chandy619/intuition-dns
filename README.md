<p align="center">
<img width="171" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/56212e77-8a1c-4b27-835d-325553023ae7"
>
</p>

<h1>Understanding Domain Name System (DNS)</h1>
This lab focuses on building intuition for DNS and how it works. DNS is a fundamental system that enables the translation of human-readable domain names into numerical IP addresses, facilitating the communication between devices on the internet. Picking up from the last lab, I will be logged in as Jane Doe (Admin User) on both the Client-1 and Domain Controller (DC-1) VMs. <br />

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
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/7196c58e-cde3-4eee-90be-46c378896e80">
</p>
<p>
We'll begin with opening Command in Client-1. Enter 'ping mainframe'. The request will fail because the local computer essentially does not have  an IP address for 'mainframe'. Therefore, we will create an A-record for mainframe.
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/b8123210-ee08-4d98-bbd1-d7a22e9c7735">
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/ac257cf8-f681-48dd-89d0-7a8d0c038fbf">
</p>
<p>
Switching to DC-1, open Server Manager from the Start menu. Click on 'Tools' located at the top right corner of the window and select 'DNS'. Double- click 'DC-1' in the left-side column, select the folder labeled 'Foward Lookup Zones' which will expand for you to select the 'mydomain.com' folder. From here, right-click in the space to the right for a list of options; select 'New Host (A OR AAAA)...' to add our own A-record. Type 'mainframe' in the name field and DC-1's private IP address. *An A-record essentially creates a mapping of a Domain Name to IP Address.*
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/06b4843e-6722-481b-801c-ee202560d0e8">
</p>
<p>
Now that the A-record is added, return to Client-1 to 'ping' mainframe once more to find that it succeeds. Using the command 'nslookup', you'll also find that the local computer is able to return the IP address back.
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/afb0b7b1-98b8-4510-85ba-00792b26eabf">
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/c2ef79b6-0181-4dae-ade1-2f1b151806fc">
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/c164bc57-22cf-4429-a7de-a8f001c5726c">
</p>
<p>
For the next portion of this tutorial, we will examine how DNS cache works. Go back to DC-1 and change the IP address of the A-record we previously created to 8.8.8.8. Now that mainframe has an new IP address, 'ping' mainframe once more from Client-1's VM to see what happens. You'll find that Client-1 is still able to successfully 'ping' mainframe, however, the old IP address (10.0.0.4) because the old IP address still exists in the local DNS cache. To change this, open Command and 'Run as admninistrator'. Enter 'ipconfig /flushdns' to erase the DNS cache. Next, 'ping' mainframe again to see the new IP address return. *Flusing the DNS cache can be useful in troubleshooting so that it can pull more current DNS records.*
</p>
<br />

<p>
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/83fcb2fb-18ae-466e-8b2d-0fcf508286e3">
<img width="960" alt="image" src="https://github.com/chandy619/intuition-dns/assets/144288806/cc0ba6b2-fc24-45be-928a-edc0a938a7c7">
</p>
<p>
Lastly, enter 'ping search' in Command. You'll find that the Client-1 is unable to find the host 'search'. Return to DC-1 and add a new record, but this time, select 'New Alias (CNAME)'. Enter 'search' as the 'Alias Name' and google.com as the FQDN. *A CNAME record essentially creates a mapping of a cononical Name to a Domain Name.* On Client-1's VM, enter 'ping search' once more to observe how google.com's public IP address returns. 
</p>
<br />
