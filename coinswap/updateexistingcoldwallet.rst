.. _updateexistingcoldwallet:

=========================================
Update an Existing MasterNode Cold Wallet
=========================================

These instructions are intended for those that were already running a MasterNode Cold wallet and want to update the existing wallet to start running the MasterNode again.  

**Prerequisites:**
	* :ref:`Install the New Liberty Coin Wallet<installnewwallet>`
	* :ref:`Upgrade an Existing MasterNode VPS Hot Wallet<upgradehotwallet>`

Implementation Steps
--------------------

1. :ref:`Create a receiving address for the MasterNode collateral funds<createmnaddressexisting>`
2. :ref:`Send EXACTLY 50000 XLIB coins to the MN1 address<sendburncoins_updateexisting>`
3. :ref:`Open the debug console of the wallet in order to type a few commands<opendebugconsole_updateexisting>`
4. :ref:`Run the getmasternodeoutputs command to retrieve the transaction ID of the collateral transfer<outputtxhash_updateexisting>`
5. :ref:`Copy and save the txhash and outputidx<copysavetxhash_updateexisting>`
6. :ref:`Go to Tools -> Open MasterNode Configuration File and add a line in the newly opened masternode.conf file<masternodeconf_updateexisting>`
7. :ref:`Restart the Cold wallet to pick up the masternode.conf changes<restartcoldwallet_updateexisting>`
8. :ref:`Open the Debug console to verify that the output from the masternode list-conf command<listconf_updateexisting>`
9. :ref:`Go to the MasterNodes tab and check if your newly added masternode is listed<masternodetab_updateexisting>`
10. :ref:`Run the startmasternode alias false MN1 command, in the Cold Wallet debug console, in order to enable the MasterNode<startmasternode_updateexisting>`

Create a MN1 Wallet Address and send it the required burn coins
---------------------------------------------------------------

.. _createmnaddressexisting:

1. Create a receiving address for the MasterNode collateral funds.

	* Go to **File -> Receiving addresses**
	* Click **New**, type in a label and press **Ok**.
	* Select the row of the newly added address and click **Copy** to store the destination address in the clipboard.
	* You can name the wallet with a description such as "**MN1**" by right clicking it and selecting **Edit**.
	
.. _sendburncoins_updateexisting:

2. Send **EXACTLY 50000 RUPX** coins to the MN1 wallet address. Double check you've got the correct address before transferring the funds.

	After sending, you can verify the balance in the Transactions tab. This can take **a few minutes** to be confirmed by the network. Go get a glass of water. No alcoholic beverages please, we are not out of the woods yet.

.. warning::	If you are sending from an exchange, make sure you account for the withdrawal fee so that you get EXACTLY EXACTLY EXACTLY 50000 RUPX in the new wallet address. This is a common error that will cause the next step to not give you the transaction id that is needed. 

Output your MN TXhash and Outputidx and update the MasterNode configuration file
--------------------------------------------------------------------------------

.. _opendebugconsole_updateexisting:

3. Open the Debug console of the wallet in order to type a few commands. 

	Go to **Tools -> Debug console**

.. _outputtxhash_updateexisting:

4. Run the **getmasternodeoutputs** command to retrieve the transaction ID of the collateral transfer::

	getmasternodeoutputs
	
* You should see an output that looks like this in the Debug console:
   
	'"txhash" : "c19972e47d2a77d3ff23c2dbd8b2b204f9a64a46fed0608ce57cf76ba9216487",'
	'"outputidx" : 1'

* **NOTE: If you do not get output resembling the above example then you likely do not have EXACTLY 50000 XLIB in the MN1 wallet address.  You will need to resolve this issue and ensure that ONLY and EXACTLY 50000 XLIB is in the MN1 address and that it is in a single input.**

.. _copysavetxhash_updateexisting:

5. Copy and save the `txhash` and `outputidx`.  Both the `txhash` and `outputidx` will be used in the next step. The `outputidx` will be either a `0` or `1`, both are valid values.

.. _masternodeconf_updateexisting:

6. Go to `Tools` -> `Open MasterNode Configuration File` and add a line in the newly opened `masternode.conf` file.  If you get prompted to choose a program, select a text editor like Notepad/TextEdit to open it.
	
* These are the default directories for the Liberty data directory where this file is stored:
	
	* Mac: ~/Library/Application Support/Liberty
	* Windows: ~\\AppData\\Roaming\\Liberty

* Below is an example of what you need in the `masternode.conf` file, all on a single line with no carriage returns.  The file contains an example that is commented out(with a **#** symbol in front). Read it for reference. Based on the output example from the **masternode outputs** command, you would add this line in::

	MN1 199.247.10.25:10417 87LBTcfgkepEddWNFrJcut76rFp9wQG6rgbqPhqHWGvy13A9hJK c19972e47d2a77d3ff23c2dbd8b2b204f9a64a46fed0608ce57cf76ba9216487 1

* **MN1** is the node's alias. 
* **199.247.10.25** is the external IP of the masternode server that will provide services to the network. 
* **87LBTcfgkepEddWNFrJcut76rFp9wQG6rgbqPhqHWGvy13A9hJK** is your masternode private key (aka GenKey), which is the value used for `masternodeprivkey=` in **/root/.liberty/liberty.conf**. 
* **c19972e47d2a77d3ff23c2dbd8b2b204f9a64a46fed0608ce57cf76ba9216487** is your TXhash from `masternode outputs`. 
* **1** is your 'outputidx' (aka Index) from `masternode outputs`.

.. _restartcoldwallet_updateexisting:

7. Restart the Cold wallet to pick up the `masternode.conf` changes.

.. _listconf_updateexisting:

8. Open the Debug console (Open **Tools > Debug console**) and run the command **listmasternodeconf**::

	listmasternodeconf

* Verify that the output matches what you entered in the `masternode.conf` file.

.. _masternodetab_updateexisting:
	
9. Go to the 'Masternodes' tab and check if your newly added masternode is listed.

	You should now see the newly added MasterNode with a status of `MISSING`.
	If you want to control multiple MasterNode Hot wallets from this Cold wallet, you will need to repeat steps 1-7. The `masternode.conf` file will contain an entry for each masternode that will be added to the network.
 

Starting the MN from the Cold Wallet
------------------------------------

.. warning:: It is very important that you let the MasterNode Hot wallet synchronize for a couple of hours prior to starting it from the Cold wallet.  If you attempt to start it before it is fully synchronized then it will fail.

.. _startmasternode_updateexisting:
	
10. Run the **startmasternode alias false MN1** command, in the Cold wallet Debug console, in order to enable the MasterNode::

	startmasternode alias false MN1

* In the example above, the alias of my MasterNode was MN1. In your case, it might be different and is based on what you entered as the first word in the masternode.conf file.
* You should get multiple lines of output.  If one of the lines of output says **"result" : successful"** then you can proceed to the next step to verify the MasterNode started correctly on the VPS Hot wallet.  If you did not get the **successful** output then there is likely an issue with the masternode.conf file that needs to be resolved first.
	
**If you received the output that shows the MasterNode started successfully then you can proceed to the next step to verify that your MasterNode started correctly from the VPS Hot wallet.**