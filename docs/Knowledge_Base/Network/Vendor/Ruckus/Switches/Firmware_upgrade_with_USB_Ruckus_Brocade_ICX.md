!!! info ""

### Ruckus Switch Firmware Upgrade – Quick Steps

download the new firmware from the this link [Ruckus support site].
Unzip the firmware files into the USB flash drive.mceclip1.png
Plug the flash drive into your switch’s USB port.
Console into the switch and make sure the USB drive mounts                                                      mount disk0
Copy the bootloader software to the switch’s bootrom                                                                    copy disk0 flash mnzXXXXX.bin bootrom
Copy the firmware on your switches to the primary partition                                                              copy disk0 flash SPSXXXXX.bin primary
Verify that the flash contents are correct                                                                                            show flash
Make sure the switch is configured to boot from the primary flash partition                               ("configuration terminal” then “boot system flash primary”).
Verify that the configuration is set to boot from the desired partition                                                 show run | include boot
Save the configuration                                                                                                                         write memory
Reboot the switch                                                                                                                           reload
Once reloaded, verify the proper firmware version is running                                                             show version
 
!!! info ""

### Ruckus Switch Firmware Upgrade – Detailed Steps

If you already completed the steps in the Quick Steps then no need to do this. These are the same steps, however more detailed in case needed.

1. Download firmware
Confirm the current approved DCD firmware version from [Here] and find it and download it from [Ruckus support site]

 

2. Unzip the firmware and put it on a flash drive
mceclip0.png
Sample file structure of a Ruckus switch firmware package

A Ruckus switch firmware package will generally include files for lots of different hardware platforms but you really only need two at a time – a bootrom (bootloader) file and a firmware image.  First, extract the .zip file and navigate to the folder matching your Ruckus ICX switch family.  Then copy the bootloader file from the “Boot” folder and the proper firmware files out of the “Images” folder.  Remember to always upgrade the switch bootloader when you upgrade your primary firmware!  If you don’t you could crash your switch.  In the end you should have three files on your USB drive that look similar to the following.  I’ll give more details on why you need all these a little further down in the instructions.

spzXXXX.bin – Bootloader
SPSXXXXX.bin – Layer 2 firmware image (switching only)
SPRXXXXX.bin – Layer 3 firmware image (routing and switching – L3 features generally require an additional license)
One final but important note – larger, modern flash drives may not work with your switch!  For some reason Ruckus switches have a hard time reading drives that are 8+ GB in capacity.  Ruckus switch firmware is small so I’d recommend you use the oldest and smallest flash drive you have for this process – 4GB or less in size.  Also make sure your flash drive is formatted as FAT32, otherwise you might see the following error:

ICX7150-24P Switch#mount disk0
Are you sure?(enter 'y' or 'n'): y
ls: /dev/exusb: No such file or directory
External USB disk is not plugged in or not formatted with VFAT/FAT32 .
 
3. Plug the USB flash drive into your switch’s USB port
This is somewhat self-explanatory.

 

4.  Console into the switch and verify the USB flash drive has mounted
Usually if your flash drive is formatted properly as FAT32 it will mount automatically.  Try using the “show flash disk0” command to find out.  If the flash drive is already mounted you should see something like this:

ICX7150-24P Switch#show files disk0
F 786944 mnz10110.bin
F 28314668 SPR08061a.bin
F 24723488 SPS08061a.bin
D 4096 
[----] disk0/System Volume Information
53825100 bytes 3 File(s) in disk0
If it’s NOT already mounted, try “mount disk0” and that should do the trick. If you get a mounting error then 1) make sure the flash drive is formatted as FAT32 and 2) make sure the flash drive       

has < 4GB total capacity. If both those conditions are true and the drive STILL won’t mount try rebooting the switch.

 

5. Copy the bootloader software to the switch’s bootrom
Copy with below command

copy <source device> <destination device> <filename> <destination partition>
For example: copy disk0 flash mnzXXXXX.bin bootrom 

 ICX7150-24P Switch#copy disk0 flash mnz10110.bin bootrom
Flash Memory Write (8192 bytes per dot)
ICX7150-24P Switch#.................................................................................................
SYNCING IMAGE TO FLASH. DO NOT SWITCH OVER OR POWER DOWN THE UNIT(65536 bytes per dot)...
............
Copy Done.
 

6.  Copy the primary firmware to the switch’s primary flash partition
Use “show version” to find out your current firmware version, then use “show flash” to find out where that firmware is stored.
Use the copy command “copy flash flash [primary | secondary]” to put a copy of your firmware into the unused flash partition.
Example:

copy disk0 flash SPSXXXXX.bin primary

copy disk0 flash SPSXXXXX.bin secondary

ICX7150-24P Switch#copy disk0 flash SPS08061a.bin primary
ICX7150-24P Switch#Load to buffer (8192 bytes per dot) .........................................
SYNCING IMAGE TO FLASH. DO NOT SWITCH OVER OR POWER DOWN THE UNIT(65536 bytes per dot)...
.................................................................................................
Copy Done.
ICX7150-24P Switch#copy disk0 flash SPR08061a.bin secondary
ICX7150-24P Switch#Load to buffer (8192 bytes per dot) .......................................
SYNCING IMAGE TO FLASH. DO NOT SWITCH OVER OR POWER DOWN THE UNIT(65536 bytes per dot)...
................................................................................................
Copy Done.
 

7.  Verify the Flash Contents are Correct
After you’re done copying the firmware over, make sure everything is where you want it to be.

Run show flash

ICX7150-24P Switch#show flash
Stack unit 1:
Compressed Pri Code size = 24723488, Version:08.0.61aT211 (SPS08061a.bin)
Compressed Sec Code size = 28314668, Version:08.0.61aT213 (SPR08061a.bin)
Compressed Boot-Monitor Image size = 786432, Version:10.1.10T225
Code Flash Free Space = 1306935296
 

8.  Force the Switch to Boot from Primary Flash
By default, a Ruckus switch will boot any valid firmware found in its primary flash partition but It's prefered to always specify which partition to use. Use the commands below to force the switch to boot from your primary partition. Run the below:

configure terminal

boot system flash primary

write memory

ICX7150-24P Switch#configure terminal
ICX7150-24P Switch(config)#boot system flash primary
ICX7150-24P Switch(config)#write memory
 

9.  Verify the Switch will Boot from the Desired Partition
Before reloading the switch confirm which flash partition the switch will be booting from.

Run show running-config | include boot

ICX7150-24P Switch#show running-config | include boot
boot sys fl pri
ICX7150-24P Switch(config)#
 

10.  Save the Running Configuration
Make sure to save your configuration write memory This will make sure your boot settings from the previous step are saved through the reboot.

ICX7150-24P Switch#write memory
There is no startup config file, unable to save legacy config
Flash Memory Write (8192 bytes per dot)
.
Write startup-config done.
Copy Done.
ICX7150-24P Switch#
 

11.  Reload the Switch
For the firmware upgrade to take effect you have to reboot the switch, use reload

ICX7150-24P Switch#reload
Are you sure? (enter 'y' or 'n'): y
Could not verify if the Running Config data has been changed.
Do you want to continue the reload anyway? (enter 'y' or 'n'): y
ICX7150-24P Switch#Unmounting the External USB
The system is going down NOW!
!
!Reload output snipped
!
 

12.  Confirm the Upgrade
Once the switch has reloaded make sure the correct firmware version is active. Run show version

ICX7150-24P Switch#show version
Copyright (c) 1996-2017 Brocade Communications Systems, Inc. All rights reserved.
UNIT 1: compiled on Aug 14 2017 at 06:54:44 labeled as SPS08061a
(24723488 bytes) from Primary SPS08061a.bin
SW: Version 08.0.61aT211
Compressed Boot-Monitor Image size = 786944, Version:10.1.10T225 (mnz10110)
Compiled on Sun Jun 25 09:25:15 2017

HW: Stackable ICX7150-24-POE
==========================================================================
UNIT 1: SL 1: ICX7150-24P-4X10GR POE 24-port Management Module
Serial #:FEA3217N0LA
Current License: 4X10GR
P-ASIC 0: type B160, rev 11 Chip BCM56160_B0
==========================================================================
UNIT 1: SL 2: ICX7150-2X1GC 2-port 2G Module
==========================================================================
UNIT 1: SL 3: ICX7150-4X10GF 4-port 40G Module
==========================================================================
1000 MHz ARM processor ARMv7 88 MHz bus
8192 KB boot flash memory
2048 MB code flash memory
1024 MB DRAM
STACKID 1 system uptime is 1 minute(s) 19 second(s)
The system started at 02:06:21 GMT+00 Wed Jan 05 2000

The system : started=cold start
 