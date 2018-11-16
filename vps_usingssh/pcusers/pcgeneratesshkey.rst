.. _pcgeneratesshkey:

========================
Generating a New SSH Key
========================

These instructions are intended for PC users that want to generate an SSH key on a Windows computer.  This step is to be completed on the computer that you will be using to connect to and manage the Linux VPS.  

* If you have already generated an SSH key, then proceed to the next section to :ref:`download and install the Putty terminal emulator<downloadputty>`.  
* If you already have a terminal emulator installed, and are using SSH keys, then you can proceed to the section to :ref:`disable password logins and root login access<disablepasswordlogins>`.

**Implementation Steps**

.. _downloadkeygen_advanced:

1. Download the PuttyGen SSH key generator.

	* `Windows 64 PuttyGen Download <https://the.earth.li/~sgtatham/putty/latest/w64/puttygen.exe>`_
	* `Windows 32 PuttyGen Download <https://the.earth.li/~sgtatham/putty/latest/w32/puttygen.exe>`_

.. _locateputtygen_advanced:
	
2. Locate the puttygen.exe file in your Downloads folder.

.. _doubleclickputtygen_advanced:

3. Double click the puttygen.exe file to open the Putty key generator.

.. _generatekey_advanced:

4. Click **Generate** to generate a new RSA 2048 bit key.

	* Be sure to check the **Parameters** to verify that **RSA** is selected.
	* Speed up the key generation process by moving your mouse around the blank area under the green loading bar.
	
.. _highlightkey_advanced:

5. Highlight and copy all of the text in the box called **Public key for pasting into OpenSSH authorized_keys file**.

	* You have to scroll down to get the whole key copied.
	* The SSH key should begin with the word **ssh-rsa** and it should end with a date, such as **rsa-key-20180406**.  
	* **NOTE: IT IS CRITICAL THAT YOU COPY THE ENTIRE SSH KEY NOT JUST WHAT YOU SEE IN THE PUTTYKEY WINDOW.**

.. _savepublickey_advanced:

6. Save the copied SSH public key in a very safe location such as a password repository.

	* You can paste this into a txt file temporarily, but be sure **NOT** to save it on your local computer to reduce the chances of it being vulnerable to being hacked. 
	* You will need this SSH public key again later in the process when adding it to the Linux VPS server.
	
.. _saveprivatekey_advanced:

7. Save the new SSH private key by clicking the button **Save private key**.

	* Click **Yes** when prompted **"Are you sure you want to save this key without a passphrase to protect it?"**
	* Type in the name **sshprivatekey** in the **File name:** field. 
	* Click Save to save the new sshprivatekey.ppk file in an easy to locate folder.  You will need to reference this file again later in the setup process.

**You are now done generating the new SSH Private Key. You can proceed to the next step to download and install the Putty terminal emulator.**
