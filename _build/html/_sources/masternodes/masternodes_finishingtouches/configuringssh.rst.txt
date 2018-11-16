.. _configuringssh_finishingtouches:

=========================================
Configure the User xlibmn to Use SSH Keys
=========================================

These instructions will walk you through the steps to configure the Linx VPS to allow the user **xlibmn** to login using an SSH key rather than the user password.  These steps are crucial for properly securing your Linux VPS from brute force password attacks.

Prerequisites
-------------

1. Generate an SSH key:
	
	* :ref:`Mac Users - Generate an SSH Key<macgeneratesshkey>`
	* :ref:`PC Users - Generate an SSH Key<pcgeneratesshkey>`
	
2. Configure your terminal emulator to use the SSH Key:

	* :ref:`Mac Users - Configure Terminal to use the SSH Key<open2ndterminal_macgeneratesshkey>`
	* :ref:`PC Users - Configure Putty to use the SSH Key<puttyimportprivkey_downloadputty>`
	
.. warning::  Do not proceed with the following steps until the above prerequisites have been completed successfully.  You will need to already be able to login to the Linux VPS, as the **root** user, using an SSH key for the following steps to work properly.

Implementation Steps
--------------------

1. Login to the Linux VPS as the **root** user.

2. Create a directory named **.ssh** in the **/home/xlibmn/** directory::

	mkdir /home/xlibmn/.ssh
	
3. Copy the file named **authorized_keys** from the directory **/root/.ssh** to the directory **/home/xlibmn/.ssh**::

	cp /root/.ssh/authorized_keys /home/xlibmn/.ssh
	
4. Change ownership of the **authorized_keys** file from **root** to the user **xlibmn**::

	chown xlibmn:xlibmn /home/xlibmn/.ssh/authorized_keys
	
**Let's test it!**

5. Open a duplicate session to the Linux VPS and login as the user **xlibmn**.  

* You should now be logged in without having to enter your password.
* For PC users, be sure that the Putty session has the SSH key saved, or this step will fail.
  
**If you are able to login to the Linux VPS with the user xlibmn, without having to type in your password, then you can proceed to the next section to disable password logins and root login access.**