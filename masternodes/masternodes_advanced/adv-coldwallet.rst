.. _adv-coldwallet:

=================
Cold Wallet Setup
=================

These instructions are intended for advanced users that are setting up a Cold wallet and don't want to waste time with all those pesky details and explanations.

Requirements:
--------------
	* Windows 7 or higher, Mac OS, or Linux
	* Outgoing internet access to sync the blockchain and enable the MasterNode remotely

Install the Liberty Cold Wallet
-------------------------------

1. Open the following URL in a web browser to download the appropriate wallet version for your system:

	* https://github.com/project-liberty/wallet/releases

2. Be sure that your existing wallet.dat and private keys are backed up from the old wallet.  We strongly recommend backing up your wallet.dat and private keys prior to starting this process.

3. Rename the old Liberty directory to something like **Liberty4**. This will prevent the new wallet install from conflicting with any of the existing data.  This is only required if the computer contains the old Liberty wallet:

	* Mac: ~/Library/Application Support/Libertycore
	* Windows: ~/AppData/Roaming/Libertycore
	
4. Unzip the wallet files and move the Liberty-cli and Liberty-qt files onto the Desktop or Application folder.  

5.Double click the Liberty-qt file to open and install the new wallet.

Create a MN1 Wallet Address and Send it the 50000 Collateral Coins
------------------------------------------------------------------

1. Create a receiving address named MN1.  This wallet address will be used for the MasterNode collateral funds.

2. Send **EXACTLY 50000 XLIB** coins to the MN1 address. Double check you've got the correct address before transferring the funds.

.. warning::	If you are sending from an exchange, make sure you account for the withdrawal fee so that you get EXACTLY EXACTLY EXACTLY 50000 XLIB in the new wallet address. This is a common error that will cause the next step to not give you the transaction id that is needed. 

Output your MN TXhash and Outputidx and update the MasterNode configuration file
--------------------------------------------------------------------------------

1. Open the Debug console.

2. Run the **getmasternodeoutputs** command to retrieve the transaction ID of the new MN1 wallet that contains the 50000 XLIB collateral::

	getmasternodeoutputs

3. Copy and save the **txhash** and **outputidx**.

4. Go to **Tools** -> **Open Masternode Configuration File** to open the **masternode.conf** file.  

5. Copy the following template and paste it into the **masternode.conf** file, on a new line::

	MN1 <public_mn_ip_address_here>:10417 <your_masternode_genkey_output> <collateral_output_txid> <collateral_output_index>
	
6. Update the **masternode.conf** file variables as instructed below.

* Leave **MN1** as is.  
* Replace the variable **<public_mn_ip_address_here>** with your Linux VPS IP address.
* Leave **:10417** as is and ensure that there are no spaces between the IP address and the port. 
* Replace the variable **<your_masternode_genkey_output>** with your masternode private key (aka GenKey). 
* Replace the variable **<collateral_output_txid>** with the **txhash**.
* Replace the variable **<collateral_output_index>** with the **outputidx**.
* **NOTE:** Below is an example of what the newly added line will look like once you have updated it will all of the required information::

	MN1 199.247.10.25:10417 87LBTcfgkepEddWNFrJcut76rFp9wQG6rgbqPhqHWGvy13A9hJK c19972e47d2a77d3ff23c2dbd8b2b204f9a64a46fed0608ce57cf76ba9216487 1

7. Restart the Cold wallet to pick up the changes to the **masternode.conf** file.

Verify the Masternode.conf File is Configure Correctly
------------------------------------------------------

1. Open the Debug console and run the command **listmasternodeconf**::

	listmasternodeconf

* Verify that the output matches what you entered in the **masternode.conf** file.
	
2. Go to the Masternodes tab and verify that the newly added MasterNode is listed.

	* You should now see the newly added MasterNode with a status of **MISSING**.
	
Start the MasterNode from the Cold Wallet
-----------------------------------------

.. warning:: It is very important that you let the MasterNode Hot wallet synchronize for a couple of hours prior to starting it from the Cold wallet.  If you attempt to start it before it is fully synchronized then it will fail.
	
1. Run the **startmasternode alias false MN1** command, in the Cold wallet Debug console, in order to enable the MasterNode::

	startmasternode alias false MN1

* You should get multiple lines of output.  If one of the lines of output says **"result" : successful"** then you can proceed to the next step to verify the MasterNode started correctly on the VPS Hot wallet.  If you did not get the **successful** output then there is likely an issue with the masternode.conf file that needs to be resolved first.

	
**If you received the output that shows the MasterNode started successfully then you can proceed to the next step to verify that your MasterNode started correctly from the VPS Hot wallet.**