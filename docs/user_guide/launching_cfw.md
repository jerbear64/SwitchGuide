# Launching CFW

Now that the preparation work is out of the way, we're finally ready to launch custom firmware on the Switch.

Unlike systems such as the DSi, Wii, or 3DS, Switch CFW is currently volatile- it will only work as long as your Switch is on. As soon as your Switch crashes, is shut down, or restarted, CFW will no longer function and you will need to follow these instructions again.

&nbsp;

### Instructions

!!! tip ""
    1. Power on your Switch into RCM, and upload the Hekate payload
    2. Navigate to `Launch firmware` with the volume buttons, and press the power button to confirm
    3. Navigate to `Atmosphere FSS0` with the volume buttons, and press the power button to confirm

Your switch is now booting into Atmosphere.

To verify Atmosphere launched properly, open the Settings applet, and navigate to System. You should see `AMS` next to the version number.

&nbsp;

!!! tip ""
    ![Atmosphere version string](../user_guide/img/launching_cfw_atmosphere_version_string.jpg)

&nbsp;

### Launching the Homebrew Menu

You will now be able to launch the Homebrew Menu by by holding the R button while launching any game (including demos/cartridges), application (e.g. Youtube/Hulu), or the album. If R is not held, the album, game, or application will launch like normal.
    
!!! warning "A note about using the album for the Homebrew Menu"
    - Using the album for the Homebrew Menu instead of a game or application has several limitations, including but not limited to: a smaller amout of available memory (RAM), as well as being unable to launch a full-featured web browser. It is strongly recommended to launch homebrew through applications or games instead.
    
!!! tip "Adding new applications"
    - Place homebrew applications (`.nro` files) into the `switch` folder on your SD card.

&nbsp;

### What the included homebrew applications do

!!! tip ""
    - Checkpoint is a save manager, it can dump and restore saves from/to your system. For more information, see [Save Management](../extras/save_management.md)

    - FTPD is a ftp tool for connecting your switch's sd card wirelessly to your pc. Tools like Filezilla can connect to your switch on `(ip of switch):5000`

    - NX-Shell is a file explorer for the switch. You can move files, listen to mp3's, view images etc.