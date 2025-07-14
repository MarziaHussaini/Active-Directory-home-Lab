<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
🔹 Active Directory Domain Services (AD DS) Manages users, computers, and permissions in a centralized way. It authenticates and authorizes access across the network and applies security policies via Group Policy.

🔹 DNS (Domain Name System) Resolves domain names  lab.local to IP addresses, allowing devices to locate domain controllers and other resources using friendly names.

🔹 DHCP (Dynamic Host Configuration Protocol) Automatically assigns IP addresses and network configuration (subnet mask, gateway, DNS) to client devices, simplifying network setup.

🔹 Windows 10 joined to the domain, the PC becomes manageable through AD. Users can log in with domain credentials and receive policies from the server.


<h2>Tools and Utilities Used</h2>
<ul>
  <li><b>Active Directory Domain Services</b></li>
  <li><b>DNS Server</b></li>
  <li><b>DHCP Server</b></li>
</ul>

<h2>Environments Used</h2>
<ul>
  <li><b>VMware</b></li>
  <li><b>Windows Server 2019</b></li>
  <li><b>Windows 10</b></li>
</ul>

<h2>Component Role in the Network</h2>
<ul>
  <li><b>AD DS:</b> Manages users, computers, and security</li>
  <li><b>DNS:</b> Resolves domain names like <i>lab.local</i> to IP addresses</li>
  <li><b>DHCP:</b> Assigns IPs and informs clients about the DNS and domain controller</li>
  <li><b>Windows 10:</b> Acts as a client that joins and interacts with the domain</li>
</ul>

<h2>Windows Server 2019 (Domain Controller + DNS + DHCP)</h2>
<ul>
  <li><b>Hostname:</b> DC1</li>
  <li><b>IP Address:</b> 192.168.100.1 (Static IP)</li>
  <li><b>Roles Installed:</b>
    <ul>
      <li>Active Directory Domain Services (AD DS)</li>
      <li>DNS Server</li>
      <li>DHCP Server</li>
    </ul>
  </li>
  <li><b>Domain Name:</b> lab.local</li>
  <li><b>VMware Adapter:</b> Bridged </li>
</ul>

<h2>Windows 10 Client</h2>
<ul>
  <li><b>IP Address:</b> 192.168.100.51 (via DHCP)</li>
  <li><b>DNS Server:</b> 192.168.100.1</li>
  <li><b>Joined Domain:</b> ✅ lab.local</li>
  <li><b>Logged in with:</b> Domain user account</li>
  <li><b>Ping to lab.local:</b> ✅ Successful</li>
</ul>
<h2>Diagram</h2>


<img width="629" height="467" alt="domain login" src="https://github.com/user-attachments/assets/e533b693-dba3-4034-9e93-8b0ffc7020b4" />


<h2>Program Walkthrough</h2>



<h2>Step 1: Set Static IP for Server</h2>
<ul>
  <li>IP: 192.168.100.1</li>
  <li>Subnet: 255.255.255.0</li>
  <li>No DHCP on the server (IP must stay static)</li>
  <li>Preferred DNS: 192.168.100.1 (self-reference)</li>
</ul>

<h2>Step 2: Install AD DS and Promote to Domain Controller</h2>
<ul>
  <li>Added AD DS role via Server Manager</li>
  <li>Created a new forest: <i>lab.local</i></li>
  <li>Rebooted after promotion</li>
</ul>

<h2>Step 3: Install DNS Server</h2>
<ul>
  <li>DNS role auto-installed with AD DS</li>
  <li>Zone <i>lab.local</i> created automatically</li>
  <li>Supports domain services </li>
</ul>

<h2>Step 4: Install DHCP Server</h2>
<ul>
  <li>Created a new DHCP Scope:</li>
  <ul>
    <li>Range: 192.168.100.50 – 192.168.100.100</li>
    <li>Subnet: 255.255.255.0</li>
    <li>Default Gateway: (optional – router or blank)</li>
    <li>DNS Server: 192.168.100.1</li>
    <li>Domain Name: lab.local</li>
  </ul>
  <li>Authorized the DHCP server in Active Directory</li>
</ul>

<h2>Step 5: Configure Windows 10</h2>
<ul>
  <li>Network set to DHCP</li>
  <li>Received IP: 192.168.100.51</li>
  <li>Received DNS: 192.168.100.1</li>
  <li>Joined domain: <i>lab.local</i></li>
  <li>Restarted and logged in </i></li>
</ul>

<h2>Windows Server 2019 instalation </h2>

<img width="956" height="466" alt="1" src="https://github.com/user-attachments/assets/c5b09289-8fef-43a5-9437-aeecd8e9dff0" />



<img width="954" height="476" alt="222222" src="https://github.com/user-attachments/assets/978c6793-8fb5-4dfd-943c-b7fb96d2321f" />

<img width="943" height="482" alt="3333" src="https://github.com/user-attachments/assets/f6f32e58-0671-4c72-94e0-456b88adc4fe" />


<img width="956" height="478" alt="5" src="https://github.com/user-attachments/assets/e710cd17-99ec-470d-880c-8dd3d9562398" />




