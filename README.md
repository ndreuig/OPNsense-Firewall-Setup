# OPNsense Firewall Setup


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

### remove iso
Open VirtualBox and select the OPNsense virtual machine.
Click on "Settings" (or press Ctrl+S).
In the Settings window, click on the "Storage" tab.
Under the "Controller: IDE" section, you should see the OPNsense ISO file listed.
Click on the ISO file and then click on the "Remove disk from virtual drive" button (it looks like a minus sign).
Confirm that you want to remove the disk by clicking "OK".
Click "OK" again to close the Settings window.


## Determining the IP Address for OPNsense Firewall

### Understand the Existing Network Infrastructure

1. Identify the Current Subnet: Before assigning an IP address to the OPNsense firewall, it is essential to identify the existing subnet of the network. For example, if your network uses the 192.168.1.x range, ensure that the firewall's IP address is compatible with this subnet.

2. Check the Router's IP Address: Determine the IP address of the existing router (e.g., 192.168.1.1). This information will help you decide the appropriate IP address for the firewall.

### Choose an Appropriate IP Address

1. Avoid Conflicts: Select an IP address for the OPNsense firewall that does not conflict with any existing devices on the network. For instance, if the router is at 192.168.1.1, you might choose 192.168.1.2 or another address that is not currently in use.



Here's a rewritten version of the section with the explanation:

## Assign WAN and LAN interfaces

1. Login with the OPNsense default username and password:
	* Username: root
	* Password: opnsense
2. Enter option 1 to assign the interfaces: 1 Assign interfaces
3. Answer "No" to the following prompts:
	* Do you want to configure LAGGs now? No
	* Do you want to configure VLANs now? No
4. After answering "No" to the above prompts, OPNsense will display a list of valid interfaces. To identify which interface corresponds to which network adapter, we need to match the MAC addresses.
5. To do this, follow these steps:
	* Go to the VirtualBox settings for the OPNsense virtual machine.
	* Click on "Network" and then select "Adapter 1".
	* Click on "Advanced" and look for the MAC address without colon separation (e.g., 080027111111).
	* Note down the MAC address.
6. Now, look at the list of valid interfaces displayed in the OPNsense command line. Find the interface that matches the MAC address you noted down in step 5. This interface corresponds to Adapter 1.
7. Repeat steps 5-6 for Adapter 2 to find the corresponding interface.
8. Enter the interface names for WAN and LAN:
	* Enter the WAN interface name: em0 (this corresponds to Adapter 1)
	* Enter the LAN interface name: em1 (this corresponds to Adapter 2)
9. Enter the optional interface name - press [Enter] for none
10. Confirm the interface assignments:
	* Interfaces will be assigned as follows:
		+ WAN -> em0
		+ LAN -> em1
11. Answer "Yes" to proceed.




Here's a rewritten version of the section with LAN and WAN separate:

## Configure WAN Interface IP Address

1. Enter option 2 to Set interface IP address.
2. Configure the WAN interface IP address:
	* Answer "No" to Configure IPv4 address WAN interface via DHCP?
	* Enter the new WAN IPv4 address: 192.168.1.13
	* Enter the new WAN IPv4 subnet bit count (subnet mask): 24
	* Leave the upstream gateway address blank (press [Enter] for none)
3. Configure the WAN interface IPv6 address:
	* Answer "No" to Configure IPv6 address WAN interface via DHCP6?
	* Press [Enter] to leave the WAN IPv6 address blank
4. Answer "No" to change the web GUI protocol from HTTPS to HTTP.
5. Answer "Yes" to generate a new self-signed web GUI certificate.
6. Answer the prompt to restore web GUI access defaults.

## Configure LAN Interface IP Address

1. Enter option 1 to set the LAN interface IP address.
2. Configure the LAN interface IP address:
	* Answer "No" to Configure IPv4 address LAN interface via DHCP?
	* Enter the new LAN IPv4 address: 192.168.1.12
	* Enter the new LAN IPv4 subnet bit count (subnet mask): 24
	* Leave the upstream gateway address blank (press [Enter] for none)
3. Configure the LAN interface IPv6 address:
	* Answer "No" to Configure IPv6 address LAN interface via DHCP6?
	* Press [Enter] to leave the LAN IPv6 address blank
4. Answer "No" to enable the DHCP server on LAN.
5. Answer "No" to change the web GUI protocol from HTTPS to HTTP.
6. Answer "Yes" to generate a new self-signed web GUI certificate.
7. Answer the prompt to restore web GUI access defaults.




## OPNsense Initial Setup Wizard

After configuring the WAN and LAN interfaces, you can now access the web GUI by opening the following URL in your web browser: https://192.168.1.12

### Login to OPNsense

* Login with the OPNsense default username and password:
	+ Username: root
	+ Password: opnsense

### General Setup

1. Click Next to start the setup wizard.

### General Information

1. Change the hostname (optional).
2. Leave the other settings at the defaults.

### Time Server Information

1. Set the timezone.

### Configure WAN Interface

You can configure the WAN interface using either DHCP or a static IP address. For this setup, we will use DHCP, but if you have obtained the necessary IP addressing details from your Internet provider, you can also use a static IP address.

#### Configure WAN Interface using DHCP

1. Select DHCP as the configuration method.
2. This is usually the default setting for most home broadband connections with a dynamic WAN IP address.

#### Configure WAN Interface using Static IP Address (Optional)

1. Select Static as the IPv4 configuration method.
2. Enter your WAN IP address in CIDR format and upstream gateway IP address.
3. You should obtain these IP addressing details from your Internet provider.
4. Leave the other settings as the defaults.

### Configure LAN Interface

1. Set the LAN IP address to 192.168.1.12.
2. Set the Subnet Mask to 24.

### Set Root Password

1. Change the root password.

### Reload Configuration

1. Click reload to apply the changes.
