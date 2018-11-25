.. _coldwalletconfig:

==============================
Cold Wallet Configuration File
==============================

This section is to provide users with a list of possible options that you can configure in the Cold wallet file **liberty.conf**.  These settings are optional and are not configured by default.  By default, the wallet configuration file is blank.

* The file **liberty.conf** is located on the computer running the Cold wallet and can be found in the following directory:

	* Mac: ~/Library/Application Support/Liberty
	* Windows: ~/AppData/Roaming/Liberty
	

1. Disable staking::

	staking=0
	
2. Enable staking::

	staking=1

3. Disable XLIBz autominting::

	enablezeromint=0

4. Enable XLIBz autominting::

	enablezeromint=1	

5. Configure the wallet to auto mint 20% of staking rewards into XLIBz instead of XLIB.  The number can be modified from 1 - 100::
	
	zeromintpercentage=20	
	
6. Disable the wallet from writing to the debug.log.  This will prevent the debug.log file from growing too large and filling up your hard drive::

	printtoconsole=1



	
