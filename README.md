# divergence-home-lab
creating a small home lab in GNS3
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



Stage 0 Topology: Starting from Zero

![STAGE 0](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/2960e05e-27ed-4ae0-b405-91613a56d3bc)

Stage 1 Topology: Network Setup

![STAGE 1](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/d4816747-1b83-4f80-8ef5-64c1a8949d41)

</head> In stage 1 I had to: </head>

  <li>Configure the Lan Network</li>
  <li>Add a Win10 workstation</li>
  <li>Connect to the firewall GUI</li>
  <lI>Complete the network setup</lI>
-----

Stage 1: Network Setup: Configuring The Lan network
</head>the first time you log into the firewall it may take a few minutes to boot up, but Once the setup is complete, you will see the loging screen</head>

Login to the console:
<li>username:admin</li>
<li>password:none </li> 
    <li>then created a password: Passw0rd!</li>

<head>Confiure the Lan interface</head>
Per The clients request I will configure 10.128.0.0/24 as the LAN network

<li>The LAN gateway will be 10.128.0.1/24</li>
<li>The LAN interface is named port2 on the FortiGate firewall</li>

![2024-01-24 10_10_53-stage1-instructions-config-lan-network  ntt-wiki  - Brave](https://github.com/notsilentxd/divergence-home-lab/assets/157625570/c86fea8e-a062-45e2-a2ca-a86fb6a658e5)
