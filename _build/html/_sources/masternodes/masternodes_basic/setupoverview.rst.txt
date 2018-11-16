.. _setupoverview:

==============
Setup Overview
==============

This guide will walk you through the steps required to setup a Liberty MasterNode on a Linux server and to setup a Cold wallet on a Windows or Mac computer.  
	
This guide assumes that you have a basic understanding of how to navigate the Linux OS for the setup of the MasterNode, and that you have an understanding of either a Windows or Mac OS for the setup of the Cold wallet. 

Common Terminology
------------------

**Hosted masternode**

	* Professional service that manages the installation and maintenance of the MasterNode server.  Running a masternode on your own does require an intermediate understanding of blockchains and server configuration, and while we do provide guides and tools to make this as easy as possible, we understand that many may still prefer to have someone take care of all the setup and maitenance.  Several members of the blockchain community have emerged to provide dedicated hosting solutions for a fee.  No technical experience is required as you need only provide them with payment for the collateral and hosting services to receive the block rewards.

**Self-operated masternode**

	* Personally managing the installation and maintenance of a MasterNode server.  Users with the required skills or the desire to learn more about the inner workings of the Liberty network may choose to run their own MasterNode on a server of their choosing.  There are several steps involved in this process and the user assumes the responsibility to set up, configure, maintain, and secure your masternode collateral.  The following pages will get you started on your journey to understanding the masternode role and setting up your first masternode.

**Hot Wallet**

	In this guide, we refer to the **Hot** wallet as the Liberty wallet that is running on a Linux or Windows VPS.

	* The VPS runs the MasterNode server.  
	* The VPS requires a public IP address statically configured on it.  
	* The Hot wallet provides services to the blockchain network, for which it's rewarded with coins.
	* It's referred to as **Hot** because it's connected to and running on the public internet 24/7, directly accessible on the peer-to-peer port (TCP **10417**).  
	* Because this wallet is always running, it is much more vulnerable to attack than a **Cold** wallet.  This is why is is highly recommended to use a Cold wallet to receive the MasterNode rewards. 

**Cold Wallet**

	On the other side, the **Cold** wallet, running on Windows, OSX, or Linux, holds the XLIB collateral (**50000** XLIB). 
 
	* The Cold wallet is used to both enable the MasterNode server and to collect the rewards for its' services.
	* The Cold wallet is normally run at home, behind a firewall, on a Windows, OSX or Linux computer.  
	* After the MasterNode is enabled, the Cold wallet can even be run without direct connectivity from the internet, making it a more secure wallet. 
	* Once the MasterNode is enabled and verified as working, the Cold wallet can then be closed and the MasterNode rewards will still show up the next time the wallet is started and synchronized.

**MasterNode Address**

	This is the public wallet address that is created in the Cold Wallet.  It is the address you will use to hold the callateral coins, when you create the MasterNode. It will also be the address that receives newly minted coins.
	
**Virtual Private Server (VPS)**

	In this guide, the VPS is referring to the Linux server that will be running the MasterNode Hot wallet.
	
**Block Count**

	The current Liberty Block Count can be verified by browsing to the Liberty Blockchain Explorer and looking for the number in the **Current Block** box in the top left of the website.
	
* http://find.rupx.io
* https://hereismy.rupx.io

**Liberty Wallet Debug Console**

	In the Liberty Cold wallet, click on **Tools** and select **Debug Console**.  
	The Debug Console will allow you to run commands to verify the following:
	
* Current wallet version and how many active connections are established - **getinfo**
* MasterNode status - **getmasternodestatus**
* Remotely start your MasterNode - **startmasternode alias false MN1**
* Check the current Block Count - **getblockcount**
* Check the current Block Hash.  - **getblockhash <blockcount>**
* Export your wallet Private Key - **dumpprivkey <walletaddress>**

.. _dont_do_this_at_home:

Running a MasterNode Hot wallet on a home computer is a bad idea
----------------------------------------------------------------

Some people want to save a few bucks and run a MasterNode Hot wallet at home on a retired PC or Laptop. Here's why that is not a good idea:

* The purpose of a MasterNode is to be a highly available system that is always reachable, has low network latency, and high bandwidth. These are rarely found in the average home.

* Static IP addresses are also harder to get for residential users or they cost extra money.

* You could loose out on MasterNode rewards if your node loses connectivity due to an Internet or computer outage.

* Running old PCs and Laptops at home also costs energy, creates noise and they can be a fire risk when running 24/7.

* Your IP address can be traced back to your home, therefore it is unsafe. This gives potential thieves and hackers a target.


**Recommendation:** Get a $5 a month Linux VPS from a provider such as Digital Ocean, Vultr, or AWS and save yourself from the possible loss of revenue when your home Internet or home computer goes down.