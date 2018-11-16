.. _verifymnstarted:

=====================================================
Verify the MasterNode Hot Wallet Started Successfully
=====================================================

1. Login to the Linux VPS console, via Putty or Terminal, as the user **rupxmn** (or the user that you used to install the Hot wallet).

2. Run the command **cat ~/.liberty/debug.log | grep HotCold**::
	
	cat ~/.liberty/debug.log | grep HotCold

* If the MasterNode started correctly then you will receive the following output: **"CActiveFundamentalnode::EnableHotColdFundamentalNode() - Enabled! You may shut down the cold daemon."** 
* Output from this command will only show up if your MasterNode started successfully.  If you do not receive the expected output, then your MasterNode did not start successfully. 
* The most common cause of this issue is attempting to start the MasterNode before the Hot wallet is fully synchronized.  Wait a couple of hours and then try to start it from the Cold wallet again.

3. Run the following command to verify the status of the MasterNode::

	liberty-cli getmasternodestatus

* If you see status **Not capable masternode: Hot node, waiting for remote activation**, you need to wait a bit longer for the blockchain to reach consensus. It's common to take 60 to 120 minutes before the activation can be done.

* If you see status **MasterNode successfully started** as well as the **HotCold** output from the first command then **CONGRATULATIONS** your MasterNode Hot wallet is now successfully enabled.
	
	* **NOTE: It will take a few hours until the first rewards start coming in.  The time before the first payout will increase as more MasterNodes come online.** 

4. Check the MasterNode tracker website http://liberty5.mn.zone to see that your MasterNode(s) are showing up on the site.  

* You will need to search by your **MN1** wallet address or your Linux VPS IP address to locate it on the website.  
* The site is refreshed every 5 minutes so don't be surprised if it takes up to 5 minutes to show up on the website.

**Congratulations! The initial setup process is complete and your MasterNode is fully operational! You can proceed to the** :ref:`Finishing Touches<masternodes_finishingtouches>` **section to enable logrotate and Hot wallet auto start.**