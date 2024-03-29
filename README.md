# divergence-home-lab
<h1>Creating a small home lab in GNS3</h1>
<head> </head> In this project the client has requested the following </head>
<ol></ol>
<li>A secure network</li>
<li>An internal windows Domain</li>
<li>An internal Microsft 10 workstation</li> 
<li>A public webserver</li>
<li>A public FTP server</li>
<li>A LAN network on 10.128.0.0/24</li>
<li>A DMZ network on 10.128.10/24</li>
<li>A Guest network on 10.128.99.0/24</li>
<br>
<h3>Stage 0 Topology: Starting from Zero</h3>

![STAGE 0](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/2960e05e-27ed-4ae0-b405-91613a56d3bc)

<h3>Stage 1 Topology: Network Setup</h3>

![STAGE 1](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/d4816747-1b83-4f80-8ef5-64c1a8949d41)

<h5> In stage 1 I had to: </h5>

  <li>Configure the Lan Network</li>
  <li>Add a Win10 workstation</li>
  <li>Connect to the firewall GUI</li>
  <lI>Complete the network setup</lI>
<br>
Stage 1: Network Setup: Configuring The Lan network

</head>the first time you log into the firewall it may take a few minutes to boot up, but Once the setup is complete, you will see the loging screen</head>

Login to the console:
<li>username: admin</li>
<li>password: by default there is no password</li> 
    <li>then created a password: Passw0rd!</li>
<br>

<head>Confiure the Lan interface</head>
Per The clients request I will configure 10.128.0.0/24 as the LAN network
<br>
<br>
<li>The LAN gateway will be 10.128.0.1/24</li>
<li>The LAN interface is named port2 on the FortiGate firewall</li>

![2024-01-24 10_10_53-stage1-instructions-config-lan-network  ntt-wiki  - Brave](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/c86fea8e-a062-45e2-a2ca-a86fb6a658e5)
<br> 
Verified the configuration is correct by using the command:
<li>Show sys int port2</li>
<br>

![2024-01-24 10_42_27-stage1-instructions-config-lan-network  ntt-wiki  - Brave](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/00ccb984-24b7-4c6b-bffb-1616f2119966)
<br>
<h5>Configure the DHCP server for the LAN interface:</h5>
<li>Enable the DHCP sever on the LAN interface</li>
<li>The firewall will perform DHCP services for the devices on the LAN network</li>
<br>

![2024-01-24 11_13_05-stage1-instructions-config-lan-network  ntt-wiki  - Brave](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/7d9c1721-e2f8-41cb-94b3-609dd7ca7200)

Verified the configuration was correct:
<li>show sys dhcp server 1</li>
<br>

![2024-01-24 11_17_55-stage1-instructions-config-lan-network  ntt-wiki  - Brave](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/23920863-0c29-43d9-9043-8fe5ddaadfbe)


<h3>Stage 1: Network Setup : Add a Win10 workstation</h3>
<h5>Scope:</h5>
<ul>
  <li>Verify that Win10 warokstation has leased a DHCP address from the LAN network</li>
  <li>Test network Connectivitiy</li>
  </ul>
<head>Login with the defualt credentials:</head>
 <ul> 
   <li>Username:IEUser</li>
     <li>password: Passw0rd!</li>
 </ul>
 <br>
 <head>Verified that Win10 workstastion has leased a DHCP addresss from the LAN network</head>
  <li>Use Command: ipconfig /all </li>
 <ul>
      <li>valid IP range: 10.1289.0[100-199]/24</li>
      <li>Gateway: 10.128.0.1</li>
      <li>DHCP server: 10.128.0.1</li>
    </ul>    
    <br>
    
![2024-01-24 12_08_39-stage1-instructions-add-win10-workstation  ntt-wiki  - Brave](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/d2987c3c-926d-48f4-b27c-b930403daa59)
<br>
<br>
<h3>Stage 1: Network Setup: Connect to the firewall GUI</h3>
<br>
<head>Connect to the GUI</head>
<ul>
<li>Open the webbrowser on the Win10 and connect to the firewall GUI</li>   
  <Ul>Http://10.128.0.1/</Ul>
</ul>
<br>

![2024-01-25 08_25_23-stage1-instructions-connect-to-fw-gui  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/c2abf402-d97a-41b5-a36b-034add1468b2)
<head>Make system chages:</head>
<ul>
  <li>Hostname=firewall</li>
  <li>timezone=GMT -6:00 Centeral Time (US& Canada)</li>
  <li>Setup device as local NTP server= enabled</li>
  <ul>List on interface = port2, port 4</ul>
  <li>idle time out = 60</li>
  <li> auto file system check = enabled</li>
</ul>
<br>

<head>Backup the configuration and reboot the firewall</head>
<br>
<br>
<head5>Stage 1: Network setup: compklete the network setup</head5>
 <br>
  <ul>
      <li>connect to the GUI</li>
      <li>Backup the firewall config</li>
      <li>configure network interfaces</li>
   <ul>     
        <li>port 1 WAN</li>
        <li>prot 2 LAN</li>  
        <li>Port 3 Guest</li>
        <li>port 4 DMZ</li>
   </ul>
    <li>Enable DNS</li>
    <li>Configure the firewall system DNS</li>
    <li>Configure Network DNS</li>
    <ul>
      <li>LAN DNS</li>
      <li>GUEST DNS</li>
      <li>DMZ DNS</li>
    </ul>
    <il>Create Service Objects</il>
    <ul> 
      <li>LAN service</li>
      <li> DMZ service</li>
    </ul>
    <li>Configure firewall Rules</li>
    <ul>
        <li>LAN-to_WAN policy</li>
        <li>DMZ-to-WAN policy</li>
        <li>LAN-to_DMZ policy</li>
        <li>DMZ-to-LAN policy</li>
        <li>WAN-to-DMZ policy</li>
    </ul>
    <li>Backup the firewall Config</li>
  </ul>
  <br>
  <h5>Connet to The GUi</h5>
  
  ![2024-01-25 09_03_23-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/33bb4ac3-6f73-42c7-8f26-72526ed109ca)

  <h5>Port1 WAN</h5>
  
  ![2024-01-25 09_03_38-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/fc1ccb8c-aa80-4024-91f8-15abc0c726bb)

  <h5>Port2 LAN</h5>
  
  ![2024-01-25 09_03_44-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/e1bbef22-624a-47d8-8359-c57a164d273d)

  <h5>Port2 Guest</h5>
  
  ![2024-01-25 09_03_52-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/a3f5f559-0ac6-481e-811e-8ef8758a1deb)

  <h5>Port4 DMZ</h5>
  
  ![2024-01-25 09_04_01-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/5baa93a5-35b0-475c-892c-ef6a3c790668)

  <h5>Enable DNS</h5>
  
  ![2024-01-25 09_04_07-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/710b97d4-a87c-420e-8f72-9be6a2c4b45c)

  <h5>Configure the firewall system DNS</h5>
  
  ![2024-01-25 09_04_14-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/72a9c671-40f5-478a-a016-9ab33025100c)

  <h5>Configure Network DNS</h5>

  ![2024-01-25 09_04_19-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/94a4198a-a48a-4379-9a72-2dc4163fac61)

  <h5> LAN DNS</h5>
  
  ![2024-01-25 09_04_19-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/7f0945ff-61a2-48b6-b591-09798310e043)

  <h5>Guest DNS</h5>
  
  ![2024-01-25 09_04_26-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/b9ebfdf0-27de-4687-a2c8-89563fad0031)

  <h5>DMZ DNS</h5>
  
  ![2024-01-25 09_04_32-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/ee96742b-8b10-4df1-9f6b-435e74c95dd0)

  <h5>LAN services</h5>
  
  ![2024-01-25 09_04_37-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/cea742c5-8eee-4880-9373-b75d257bc570)

  <h5>DMZ services</h5>
  
  ![2024-01-25 09_04_44-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/34e8ff24-db38-49bc-bc10-6f239a8ee101)

  <h5>LAN-to-WAN policy</h5>

  ![2024-01-25 09_04_50-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/23e38ce0-a75b-4f87-908e-0f1a913bf0e5)

  <h5>LAN-to-DMZ policy</h5>
  
  ![2024-01-25 09_04_55-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/a187aaf5-0a41-4aa2-87f8-51faa5d41ca0)

  <h5>DMZ-to-LAN policy</h5>
  
  ![2024-01-25 09_05_04-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/94f04715-91e4-4a0d-b166-2f99f1bdddb0)

  <h5>WAN-to-DMZ policy</h5>
  
  ![2024-01-25 09_05_10-stage1-instructions-complete-network-setup  ntt-wiki](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/439b6476-f3cd-48da-9cd4-2e7b841509a4)

  <br>
  <head> Backup the firewall Config</head>




     

