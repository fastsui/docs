.. _masternodeconfig:

=========================================
Cold Wallet Masternode Configuration File
=========================================

This section is to provide MasterNode users with a template to use for the Cold wallet file **masternode.conf**.  This file is updated during the setup of the Cold wallet.  This section contains both a template and an example of what the file should look like once it is updated.

* The file **masternode.conf** is located on the computer running the Cold wallet and can be found in the following directory:

	* Mac: ~/Library/Application Support/Liberty
	* Windows: ~/AppData/Roaming/Liberty

**TEMPLATE**
	
Below is a template for the **masternode.conf** file.  Every word in this template is a variable that needs to be replaced with your specific information::

	alias IP:port masternodeprivkey collateral_output_txid collateral_output_index 

* Replace **alias** with the node alias that you wish to use.  For consistency sake, we recommend using **MN1** 
* Replace **IP** with the external IP address of the Linux VPS MasterNode server.
* Replace **port** with **10417** which is the TCP port that is used by the wallet to establish connections.
* Replace **masternodeprivkey** with the masternode private key (aka GenKey) that you received as output from the **liberty-cli createmasternodekey** command on the Linux VPS.
* Replace **collateral_output_txid** with the **txhash** that you received as output from the **getmasternodeoutputs** command in the Cold wallet Debug Console.
* Replace **collateral_output_index** with the **outputidx** that you received as output from the **getmasternodeoutputs** command in the Cold wallet Debug Console.

**EXAMPLE**

Below is an example of what the newly added line in the **masternode.conf** file will look like once you have updated it will all of the required information.  All of the information should be contained in a single line with no carriage returns::

	MN1 199.247.10.25:10417 87LBTcfgkepEddWNFrJcut76rFp9wQG6rgbqPhqHWGvy13A9hJK c19972e47d2a77d3ff23c2dbd8b2b204f9a64a46fed0608ce57cf76ba9216487 1


