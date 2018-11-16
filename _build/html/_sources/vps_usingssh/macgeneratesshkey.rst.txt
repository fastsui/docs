.. _macgeneratesshkey:

=======================================================
Mac Users - Generating and Using SSH Keys with Terminal
=======================================================

These instructions are intended for Mac users that want to generate an SSH key and start using it to connect to the Linux VPS.  This step is to be completed on the computer that you will be using to manage the Linux VPS.  

* If you have already generated an SSH key and are already using it to connect to the Linux VPS then proceed to the section to :ref:`disable password logins and root login access<disablepasswordlogins>`.

.. _openterminal_macgeneratesshkey:

Generating an SSH Key
=====================

1. Open the application named Terminal

* Launch terminal by using Spotlight search in OS X, searching for **terminal**

.. _mackeygen_macgeneratesshkey:

2. Generate an ssh key on the Mac by running the **ssh-keygen** command in Terminal::
	
	ssh-keygen
	
* Hit **ENTER** to confirm the default file name.
* Hit **ENTER** two times, without typing anything in, when prompted for an SSH Key Passphrase.

.. _sshintovps_macgeneratesshkey:

3. Login to your Linux VPS via SSH by running the following command in Terminal::

	ssh root@<public_mn_ip_address_here>
	
* Replace the variable **<public_mn_ip_address_here>** with your Linux VPS IP address
* Type **yes** to confirm that you want to connect using SSH

.. _linuxkeygen_macgeneratesshkey:

4. Generate an SSH key on the Linux VPS with the following command::

	ssh-keygen
	
* Hit **ENTER** to confirm the default file name
* When prompted for an SSH Key Passphrase, do not type anything in and hit **ENTER** two times to skip this step.

.. _open2ndterminal_macgeneratesshkey:

Using the SSH Key to Connect to the Linux VPS
=============================================

1. Open a new Terminal window on your Mac::

	ssh root@<public_mn_ip_address_here>
	
* Replace the variable **<public_mn_ip_address_here>** with your Linux VPS IP address
* Type **yes** to confirm that you want to connect using SSH

.. _copykeytoidrsa_macgeneratesshkey:

2. Copy the SSH key from your Mac to your Linux VPS by running the following command on your Mac Terminal window::

	scp ~/.ssh/id_rsa.pub root@<public_mn_ip_address_here>:/root/.ssh/authorized_keys
	
* Replace the variable **<public_mn_ip_address_here>** with your Linux VPS IP address
* Type in the root password when prompted and hit **ENTER**
	
**Now it's time to test that your new SSH key is indeed working!**

.. _loginwithkeymac_macgeneratesshkey:

3. Login to the Linux VPS using the new SSH key::

	ssh root@<public_mn_ip_address_here>

* Replace the variable **<public_mn_ip_address_here>** with your Linux VPS IP address
* You should no longer be prompted to enter a password.
* If you were prompted for a password then one of the previous steps failed and you will need to try again.

**If you are able to login to the Linux VPS without being prompted for a password then this process is complete and you can proceed to next section to** :ref:`disable password logins and root login access<disablepasswordlogins>`.
