.. _hotwalletconfig:

=============================
Hot Wallet Configuration File
=============================

This section is to provide MasterNode users with a template to use for the Hot wallet file **liberty.conf**.  This file is updated during the setup of the Linux VPS and the Hot wallet.  This section contains both a template and an example of what the file should look like once it is updated.

* The file **liberty.conf** is located on the Linux VPS in the following directory:

	* ~/.liberty/liberty.conf

**TEMPLATE** 

Below is the template for the Hot wallet **liberty.conf** file.  Copy and paste this template into a text editor, and update the variables manually.  All variables that need to be updated manually are identified with the **<>** symbols around them::
	
	rpcuser=libertyrpc 
	rpcpassword=<alphanumeric_rpc_password> 
	rpcport=10416 
	rpcallowip=127.0.0.1 
	rpcconnect=127.0.0.1 
	rpcbind=127.0.0.1 
	maxconnections=512 
	listen=1 
	daemon=1
	masternode=1
	externalip=<public_mn_ip_address_here>:10417 
	masternodeaddr=<public_mn_ip_address_here> 
	masternodeprivkey=<your_masternode_genkey_output> 
	
* Update the variable after **rpcpassword=** with a 40 character RPC rpcpassword.
* You will need to generate the rpcpassword yourself.
* Use the **ifconfig** command, on the Linux VPS, to find out your Linux VPS IP address.  It is normally the address listed after the **eth0** interface after the word **inet addr:** 
* Update the variable after **externalip=** with your Linux VPS IP.  Ensure that there are no spaces between the IP address and the port **:10417**
* Update the variable after **masternodeaddr=** with your Linux VPS IP 
* Update the variable after **masternodeprivkey=** with your MasterNode private key (GenKey) 

**EXAMPLE**

Below is what the file should look like once it is updated and pasted into the **~/.liberty/liberty.conf** file on the Linux VPS.

* This is a real example of what the configuration file should look like when you are done updating the variables.
* The **rpcpassword**, **IP address** (`199.247.10.25` in this example), and **masternodeprivkey** will all be different in your configuration file::
	
	rpcuser=xlibuser 
	rpcpassword=someSUPERsecurePASSWORD3746375620 
	rpcport=10416 
	rpcallowip=127.0.0.1 
	rpcconnect=127.0.0.1 
	rpcbind=127.0.0.1 
	maxconnections=512 
	listen=1 
	daemon=1 
	masternode=1 
	externalip=199.247.10.25:10417 
	masternodeaddr=199.247.10.25
	masternodeprivkey=87LBTcfgkepEddWNFrJcut76rFp9wQG6rgbqPhqHWGvy13A9hJK 