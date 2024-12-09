# OPNsense Firewall Setup


## Download OPNsense
to download the OPNsense, we go to the official link of OPNsense https://opnsense.org/download/
then we select Architechture: amd64, the image type dvd because we will use virtualbox, then we choose the closest loaction LeaseWeb in our case, then hit download

after downloading, go to your downloads folder, then right click on the the downloaded file that is a winrar type, and click the right of the mouse, then click extract here
after extracting the file, we are ready to setup or create the virtual machine in the virtual box.

then we open virtual box, and we click on Tools from the sidebar and select New from the toolbar.

enter name OPNsense Firewall, and for Folder, specify where you want the VM files to be saved.
Select the ISO Image dropdown and click Other to locate and select the .iso file downloaded earlier.
Choose the following settings:
Type: BSD
Version: FreeBSD (64-bit)

Configure Resources
RAM: Allocate at least 2 GB.
CPU: Allocate 1 cores or more depending on your pc.
Leave other settings as default.

Configure Storage
Create a virtual hard disk:
Select Create a virtual hard disk now.
Use the VDI (VirtualBox Disk Image) format.
Choose Dynamically allocated storage.
Set the size to at least 16 GB.
Click Finish



Network Configuration
OPNsense requires at least two network adapters for WAN and LAN. Configure as follows:

Adapter 1:

Go to Network > Adapter 1.
Tick Enable Network Adapter.
Set Attached to: Bridged Network
Expand Advanced:
Set Adapter Type: Default
Promiscuous Mode: Allow All

Adapter 2:

Go to Network > Adapter 2.
Tick Enable Network Adapter.
Set Attached to: Bridged Network
For Name, enter LAN 0.
Expand Advanced:
Set Adapter Type: Default
Promiscuous Mode: Allow All
Click OK to save the changes.




boot the machine opnsense firewall, then after it starts, Let it load automatically until it asks for login and password, login:root and password:opnsense.

login:installer and password:opnsense to install it

select your keyboard i selected german as it is my keymap, then continue, then select install ztf, then select stripe, then press space and then ok (enter), then press yes

then you change you password, and then exit and reboot.



**Downloading OPNsense**

1. Go to the official OPNsense download link: https://opnsense.org/download/
2. Select the following options:
	* Architecture: amd64
	* Image type: dvd (for VirtualBox)
	* Location: Choose the closest location (e.g., LeaseWeb)
3. Click Download and wait for the file to download.

**Extracting the Downloaded File**

1. Go to your downloads folder and right-click on the downloaded file (a .rar file).
2. Click Extract Here to extract the contents.

**Creating a Virtual Machine in VirtualBox**

1. Open VirtualBox and click on Tools from the sidebar.
2. Select New from the toolbar.
3. Enter the following details:
	* Name: OPNsense Firewall
	* Folder: Specify where you want the VM files to be saved.
4. Select the ISO Image dropdown and click Other to locate and select the .iso file downloaded earlier.
5. Choose the following settings:
	* Type: BSD
	* Version: FreeBSD (64-bit)

**Configuring Resources**

1. Allocate at least 2 GB of RAM.
2. Allocate 1 core or more depending on your PC.
3. Leave other settings as default.

**Configuring Storage**

1. Create a virtual hard disk:
	* Select Create a virtual hard disk now.
	* Use the VDI (VirtualBox Disk Image) format.
	* Choose Dynamically allocated storage.
	* Set the size to at least 16 GB.
2. Click Finish.

**Network Configuration**

1. OPNsense requires at least two network adapters for WAN and LAN. Configure as follows:
	* Adapter 1:
		+ Go to Network > Adapter 1.
		+ Tick Enable Network Adapter.
		+ Set Attached to: Bridged Network
		+ Expand Advanced:
			- Set Adapter Type: Default
			- Promiscuous Mode: Allow All
	* Adapter 2:
		+ Go to Network > Adapter 2.
		+ Tick Enable Network Adapter.
		+ Set Attached to: Bridged Network
		+ For Name, enter LAN 0.
		+ Expand Advanced:
			- Set Adapter Type: Default
			- Promiscuous Mode: Allow All
2. Click OK to save the changes.

**Booting and Installing OPNsense**

1. Boot the OPNsense Firewall machine.
2. Let it load automatically until it asks for login and password.
3. Login with the following credentials:
	* Login: root
	* Password: opnsense
4. Login with the following credentials to install OPNsense:
	* Login: installer
	* Password: opnsense
5. Follow the installation prompts:
	* Select your keyboard layout (e.g., German).
	* Continue.
	* Select Install ZTF.
	* Select Stripe.
	* Press Space and then OK (Enter).
	* Press Yes.
6. Change your password and exit.
7. Reboot the machine.
