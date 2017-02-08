# Formatting an SDXC card for use with NOOBS

According to the [SD specifications](https://www.sdcard.org/developers/overview/capacity/), any SD card larger than 32GB is an SDXC card and has to be formatted with the exFAT filesystem. This means the official SD Formatter tool will *always* format cards that are 64GB or larger as exFAT.

The Raspberry Pi's bootloader, built into the GPU and non-updateable, only has support for reading from FAT filesystems (both FAT16 and FAT32), and is unable to boot from an exFAT filesystem. So if you want to use NOOBS on a card that is 64GB or larger, you need to reformat it as FAT32 first before copying the NOOBS files to it.

## Linux and Mac OS

The standard formatting tools built into these operating systems are able to create FAT32 partitions; they might also be labelled as FAT or MS-DOS. Simply delete the existing exFAT partition and create and format a new FAT32 primary partition, before proceeding with the rest of the [NOOBS instructions](noobs.md).

## Windows

The standard formatting tools built into Windows are limited, as they only allow partitions up to 32GB to be formatted as FAT32, so to format a 64GB partition as FAT32 you need to use a third-party formatting tool. A simple tool to do this is [FAT32 Format](http://www.ridgecrop.demon.co.uk/guiformat.htm) which downloads as a single file named `guiformat.exe` - no installation is necessary.

Run the [SD Formatter](https://www.sdcard.org/downloads/formatter_4/) tool first with "FORMAT SIZE ADJUSTMENT" set to "ON", to ensure that any other partitions on the SD card are deleted. Then run the FAT32 Format (guiformat.exe) tool, ensure you choose the correct drive letter, leave the other options at their default settings, and click "Start". After it has finished, you can proceed with the rest of the [NOOBS instructions](noobs.md).

If the FAT32 Format tool doesn't work for you, alternative options are [MiniTool Partition Wizard Free Edition](http://www.minitool.com/partition-manager/partition-wizard-home.html) and [EaseUS Partition Master Free](http://www.easeus.com/partition-manager/epm-free.html) which are "home user" versions of fully featured partition editor tools, and so not as straightforward to use.

Another way to format it under windows without using any extra software
First, make sure your SD Card is plugged in
Search and open Command Prompt as an administrator
Next, you’ll have to open the disk management utility using CMD (Command Prompt) – to do that, type in diskpart and hit enter
After that, you will have to display the connected disks that are available – to do that, type in list disk and hit enter
Then, you’ll need to select your SD Card – to do that, type select disk # and hit enter – you’ll have to replace the # with your disk number
Next, you’ll have to clean the SD Card – to do that, type clean and hit enter
Then you’ll need to create a bootable partition – type in create partition primary and hit enter
You will now need to select the partition that you just created. To do that, type in select partition 1 
After that, type active and hit enter
Next, you’ll need to format the USB drive – just type in format fs=fat32 quick and hit enter
You’ll now need to assign your USB drive a letter, to do that, just type in assign
Thats all.
