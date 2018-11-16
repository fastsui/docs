.. _disablepasswordlogins:

===========================================================
All Users - Disabling Password Logins and Root Login Access
===========================================================

These instructions are intended for all users that want to reduce the risk of brute force login attacks by disabling password logins and root login access.  These procedures will improve security on your Linux VPS by requiring the correct SSH Key to be able to login.  After completing these steps, any computer, or SSH session, that does not have the correct SSH Key installed will not be able to login to the Linux VPS, and you will no longer be able to remotely login to the Linux VPS using the root user. 

Disabling password login capabilities
-------------------------------------

.. warning:: Do not perform the following steps until you are able to successfully login to the Linux VPS using an SSH key rather than your username and password.

* You should be logged in to the Linux VPS as the **root** user to complete the following steps:

1. The following commands will edit the SSH file **/etc/ssh/sshd_config** to disable password login capabilities, and will then restart the **sshd** service to apply the change::

	sed -i 's/PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config
	systemctl reload sshd

Disabling root login access
---------------------------

.. warning:: Do not perform the following steps until you have created the user **xlibmn** and are able to login to the Linux VPS using an SSH key with that new user.  
 
* You should be logged in to the Linux VPS as the root user to complete the following steps:

1. The following commands will edit the SSH file **/etc/ssh/sshd_config** to disable root login access, and will then restart the **sshd** service to apply the change::

	sed -i 's/PermitRootLogin yes/PermitRootLogin no/g' /etc/ssh/sshd_config
	systemctl reload sshd

**Let's test it!**
	
2. Open a duplicate session to the Linux VPS and login as **root**.

* **NOTE:** It should no longer allow you to login as **root** and a pop up window should appear with the following error: **Disconnected: No supported authentication methods available**

**If password authentication and root login access have been successfully disabled then you can proceed to the next section to begin the** :ref:`MasterNode Basic Setup<basicsetup>`.