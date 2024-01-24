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
<li>password: none </li> 
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
<br> 
<li>Login with the defualt credentials:</li>
 <ul> 
   <li>Username:IEUser</li>
     <li>password: Passw0rd!</li>
 </ul>
    
     

