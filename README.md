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
CPU: Allocate 2 cores.
Leave other settings as default.

Configure Storage
Create a virtual hard disk:
Select Create a virtual hard disk now.
Use the VDI (VirtualBox Disk Image) format.
Choose Dynamically allocated storage.
Set the size to at least 20 GB.
Click Finish




Here’s the documentation in a similar style for OPNsense. This step-by-step guide ensures clarity and professionalism.

Download OPNsense
Go to the official download link:
OPNsense Download Page

Select the following options:

Architecture: amd64 (most modern machines support this).
Image Type: DVD (ISO format).
Mirror: Select a server closest to your location for faster download.
Download the latest version of OPNsense:
As of writing, the latest version is 23.7.5.

The downloaded file will have the extension .iso.bz2. Use a decompression tool like 7-Zip or WinRAR to extract it.

After extraction, you will have a file with the .iso extension.

OPNsense VM Creation
Step 1: Launch VirtualBox
Open VirtualBox.
Click on Tools from the sidebar and select New from the toolbar.
Step 2: Create the VM
For Name, enter a descriptive name like OPNsense Firewall.
For Folder, specify where you want the VM files to be saved.
Select the ISO Image dropdown and click Other to locate and select the .iso file downloaded earlier.
Choose the following settings:
Type: BSD
Version: FreeBSD (64-bit)
Click Next.
Step 3: Configure Resources
RAM: Allocate at least 2 GB.
CPU: Allocate 2 cores.
Leave other settings as default.
Click Next.
Step 4: Configure Storage
Create a virtual hard disk:
Select Create a virtual hard disk now.
Use the VDI (VirtualBox Disk Image) format.
Choose Dynamically allocated storage.
Set the size to at least 20 GB.
Click Create.
Step 5: Finalize the VM
Once done, you will see the newly created VM in the sidebar.
OPNsense VM Configuration
Before booting the VM, you need to configure some settings.

System Configuration
Select the OPNsense VM and click on Settings.
Go to System > Motherboard:
Boot Order: Move Hard Disk to the top, followed by Optical.
Ensure Floppy is unchecked.
Click OK.


Network Configuration
OPNsense requires at least two network adapters for WAN and LAN. Configure as follows:

Adapter 1:

Go to Network > Adapter 1.
Tick Enable Network Adapter.
Set Attached to: NAT.
Expand Advanced:
Set Adapter Type: Paravirtualized Network (virtio-net).
Adapter 2:

Go to Network > Adapter 2.
Tick Enable Network Adapter.
Set Attached to: Internal Network.
For Name, enter LAN 0.
Expand Advanced:
Set Adapter Type: Paravirtualized Network (virtio-net).
Click OK to save the changes.


Adapter 1 (WAN):

Attached to: Bridged Adapter
Name: Your physical network interface (e.g., Ethernet or Wi-Fi)
Promiscuous Mode: Allow All
MAC Address: Leave it as is or set a custom MAC address
Adapter 2 (LAN):

Attached to: Host-only Adapter
Name: vboxnet0 (or any other host-only network interface)
Promiscuous Mode: Allow All
MAC Address: Leave it as is or set a custom MAC address
Adapter 3 (Optional):

Attached to: Internal Network
Name: opnsense-internal (or any other internal network interface)
Promiscuous Mode: Allow All
MAC Address: Leave it as is or set a custom MAC address



boot the machine opnsense firewall, then after it starts, Let it load automatically until it asks for login and password, login:root and password:opnsense.

login:installer and password:opnsense to install it

select your keyboard i selected german as it is my keymap, then continue, then select install ztf, then select stripe, then press space and then ok (enter), then press yes

then you change you password, and then exit and reboot.
