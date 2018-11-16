.. _hotwalletautostart:

============================
Enable Hot Wallet Auto Start
============================


This section is intended for MasterNode users that want to configure the Linux VPS to automatically start the MasterNode Hot wallet when the Linux VPS is rebooted.

1. Connect to your Linux VPS and login as **xlibmn**.

2. Elevate to **root** level privelege::

	sudo -i

3. Run the following command to create and edit the file **/etc/cron.d/resetliberty**.  This file will be used to tell the server to restart the Hot wallet upon bootup::

	nano /etc/cron.d/resetliberty
	
4. Copy the following text and paste it into the resetliberty file.  This will create a cronjob that will start the Hot wallet automatically in the event that the server is rebooted::

	@reboot xlibmn sleep 5 && /usr/local/bin/libertyd

* Save and close the file by hitting **Ctrl-X**, and then type **Y** to confirm that you want to save it, and then hit **ENTER** to confirm the file name.

5. Reboot the Linux VPS to test and verify that the Hot wallet will restart upon boot::

	reboot

6. Wait a couple minutes and then reconnect your Linux VPS and login as **xlibmn**.  

* It will take a couple of minutes for the Linux VPS to reboot.

7. Run the command **ps -ef |grep libertyd** to verify the Hot wallet is running::

	ps -ef |grep libertyd
	
* You should get two lines of output, and one of the lines will have the text **/usr/local/bin/libertyd**.  
* If you only get one line of text with the output **grep --color=auto liberty** then the wallet is not running and you will need to walk through the above steps again.

8. Run the command **liberty-cli getblockcount** to verify that your Hot wallet is indeed running and that your block count is increasing::

	liberty-cli getblockcount

9. Verify that your MasterNode is still showing up on the MasterNode tracker website.  The site is refreshed every 5 minutes so check it a few times just to be sure.

* http://liberty5.mn.zone/

**If the MasterNode Hot wallet automatically restarts after a reboot then you have successfully completed this section.  CONGRATULATIONS!!  The setup of your MasterNode is now fully complete!**  

**NOTE: There is no need to proceed to the next section since all of the configuration steps have been completed.** 