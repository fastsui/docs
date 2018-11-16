.. _swapbotsteps:

=========================================
Swap Bot - Steps to Perform the Coin Swap
=========================================

These instructions are intended for those that will be using the Swap Bot to perform the coin swap.  There are simple instructions for advanced users and detailed instructions for those of you that would like a more in depth explanation of each step. 


Simple Instructions for Advanced Users
======================================

Below are the simplified instructions for those advanced users that don't require detailed steps.  These are the same instructions that you will be receiving direclty from the Swap Bot by typing the **$simple** command in the Swap Bot Discord channel.

Each of the sentences that start with the **$** symbol are commands that you will be sending directly to the SwapBot::

	$start [oldwalletaddress]
	VERIFY: Confirm the balance amount.
	$sent [netamountsent] [txid]
	$status
	$address [newwalletaddress]
	VERIFY: Triple check the new Liberty receiving address before proceeding.
	$agree
	VERIFY: Verify that .01 XLIB was received in the new wallet.
	$confirm [txid]
	$status

	Congratulations, your coin swap is complete!  When you perform the final $status command your swap will be marked as completed by the bot.

Detailed Instructions
=====================

Below are the detailed instructions for performing a successful coin swap utilizing the Swap Bot.  These are the same instructions that you will be receiving direclty from the Swap Bot by typing the **$instructions** command in the Swap Bot Discord channel.

Each of the sentences that start with the **$** symbol are commands that you will be sending directly to the SwapBot::

	1.  1st Command: $start [oldwalletaddress]
		a.  Example: $start LFCFtD4scWXUDswzZTvWQHgCyzfiryGguX
		b.  Explanation: To initiate the swap, please respond with the $start command and your 
			consolidated wallet address.  I will respond with the coin swap receiving address 
			and the approved balance for your registered LBRT address.  
			Only the balance displayed will be accepted on the new chain.  
			If you have a discrepancy with the balance that the snapshot is reporting, 
			then issue the $alert command to be placed into the queue for manual administrative 
			intervention.

	2.  VERIFY: Confirm the balance is correct and send the full Liberty balance in a single transaction 
		to the address that I provided.

	3.  2nd Command: $sent [amountsent] [txid]
		a.  Example: $sent 15 138173567d430b154877e4e004ebafefce90c38038f920a0aacb03055c72514b
		b.  Explanation: After sending all Liberty in a single transaction, respond with 
			the $sent command using the After Fee amount and txhash for the transaction.
		c.  NOTE: If you copy and paste your transaction, be sure to remove any spaces in the 
			thousands place. 1000 is okay, 1 000 is not okay

	4.  3rd Command: $status
		a.  Example: $status
		b.  Explanation: Check your current status by responding with the $status command. 
			I will indicate if I have successfully confirmed the transaction.
			Upon enough successful confirmations you will be instructed to download the 
			new wallet - https://github.com/Liberty-project/LBRT/releases.

	5.  4th Command: $address [newwalletaddress]
		a.  Example: $address XANLeD7efUBtVxMWEiYyYfiewGypspSMFj
		b.  Explanation: After installing the new wallet, syncing the wallet fully, and 
			generating a new address, respond with the $address command with your new address.  
			This will confirm the wallet address that the bot will be sending the new coins to.

	6.  VERIFY: Triple check my confirmation of the new address received and read the disclaimer 
		before proceeding.

	7.  5th Command: $agree
		a.  Example: $agree
		b.  Explanation: Respond with $agree to confirm the new receiving address is correct 
			and that the disclaimer has been read.

	8.  VERIFY:  Verify that .01 XLIB was received in the new wallet. 

	9.  6th Command: $confirm [txid]
		a.  Example: $confirm 138173567d430b154877e4e004ebafefce90c38038f920a0aacb03055c72514b
		b.  Explanation: Confirm the test transaction by issuing the $confirm command along with 
			the txid (txhash) of the test transaction.  
			Once the test transaction has been confirmed, then your remaining balance will begin 
			to transfer.
		c.  NOTE: You may need to enter this command multiple times until all confirmations have 
			been completed.  Expect this wait time to be around 75 minutes.

	10. 7th Command: $status
		a.  Example: $status
		b.  Explanation: Respond with $status to check that the final transaction has been 
			completed successfully.

	Congratulations, your coin swap is complete!  When you perform the final $status command your swap will be marked as completed by the bot.
	
**Once completed, you can move on to the next step to either update your existing Linux VPS Masternode or setup a fresh install of the VPS and Hot wallet using the** :ref:`basic setup guide<basicsetup>`.