# Changing SD cards

The goal of this page is to transfer the contents from one SD card to another one. The method to do this will differ, depending on whether you're using a partition based emuMMC on your SD card or not.

We will be using [hekate](https://github.com/CTCaer/hekate/releases/) to both backup and restore the emuMMC, so make sure that you have its latest files on your SD card already.

## Instructions

You should first check whether you have a file or partition based emuMMC:
    
1.  Inject the hekate payload.
2.  Tap on `emuMMC`.
3.  Under `emuMMC Info & Selection`, check the text next to `Type`.
    - If you have one it should be either `SD Raw Partition` or `SD File`.

-----
### If you are using a file based emummc or are using no emummc at all:
        
1.  Remove your SD card.   
2.  Insert your old SD card into your computer.
3.  Copy the contents of your SD card somewhere to your PC.
4.  Eject the SD card and insert your new one.
5.  Format your new SD card to FAT32 if it isn’t already.
    - To do this, use [guiformat](http://ridgecrop.co.uk/index.htm?guiformat.htm) for example (Windows).
6.  Copy the files from your PC to your new SD card and you’re done.

!!!note "Note for macOS users"
	If you perform this copy on macOS, you may find that Switch titles can no longer start and error with `Could not start the Software`, or other issues relating to the SD card. This is due to a quirk with how macOS handles FAT32 file systems. Fortunately, the fix is simple:

    1. Boot into hekate
    2. In the main menu, tap on `Tools`, then `Arch bit • RCM • Touch • Pkg1/2`
    3. Tap on `Fix Archive Bit`

-----
### If you are using a partition based emummc:

!!!warning "Space for the backup"
    You need at least 30GB of free space to be able to backup and restore the emuMMC!

1.  Inject the hekate payload.
2.  In the main menu, tap on `Tools`, then `Backup eMMC` and set `SD emuMMC Raw Partition` at the bottom of your screen to `ON`.
3.  Backup both `SD emuMMC BOOT0 & BOOT1` and `SD emuMMC RAW GPP` (Note: raw gpp may take a while).
4.  Once both are done, go back to the main menu, remove your SD card and insert it into your PC.
5.  If Windows asks you to format a drive, discard it and select the drive with your SD contents.
6.  Copy the contents of your SD card somewhere to your PC.
7.  Follow only [this page](https://switchgui.de/switch-guide/user_guide/emummc/partitioning_sd/) to partition the new SD card for an emuMMC setup.
8.  After it’s done, exit and insert your new SD card into your PC.
9.  Copy the contents of your old SD card to your new one.
10. Navigate to `/backup/<some characters>/` on your SD card and move `BOOT0`, `BOOT1` and the `rawnand.bin.xx` files to the `/backup/<some characters>/restore/emummc` folder.
11. Eject the SD card and insert it into your switch.
12. Inject the hekate payload once again.
13. Tap on `Tools`, `Restore eMMC`, set `SD emuMMC Raw Partition` at the bottom of your screen to `ON`.
14. Restore the backup by tapping on both `SD emuMMC BOOT0 & BOOT1` and `SD emuMMC RAW GPP` (Note: raw gpp may take a while).
    - It is very important that for both of these the `SD emuMMC Raw Partition` option is enabled, otherwise you will be altering your sysMMC
      which is not what you want.
15. Your emuMMC is now restored on the new SD card and you should be able to launch it from `Launch` -> `Atmosphere FSS0 emuMMC` in hekate.

!!!note "Note for macOS users"
	If you perform this copy on macOS, you may find that Switch titles can no longer start and error with `Could not start the Software`, or other issues relating to the SD card. This is due to a quirk with how macOS handles FAT32 file systems. Fortunately, the fix is simple:

    1. Boot into hekate
    2. In the main menu, tap on `Tools`, then `Arch bit • RCM • Touch • Pkg1/2`
    3. Tap on `Fix Archive Bit`
