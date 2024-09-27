# Keeping your system up-to-date

This page documents how you can keep your system up-to-date.

After following our guide, your system will consist of three core elements that can be updated. Atmosphere, Hekate and your system firmware.

### **Updating Atmosphere**

When updating Atmosphère, always make sure to _read the release notes_. They may list important changes and modifications to your system.

!!! warning "Updating from below Atmosphère 1.0.0"
    If you update from below Atmosphère 1.0.0, there are additional steps to follow. You will have to delete the `sept` folder from your microSD, delete `fusee-secondary.bin` from your `atmosphere` folder and update your Hekate config file: <a href="../../files/emu/hekate_ipl.ini" download>hekate_ipl.ini</a> in the `bootloader` folder.

When a new version of Atmosphère releases, you can update Atmosphère by following these steps:


1. Enter RCM and inject the Hekate payload.
    - If you use a modchipped Switch, you can simply just turn your Switch on with the Hekate payload renamed to `payload.bin` on the root of your microSD card.
1. Navigate to `Tools` > `USB Tools` > `SD Card` and plug your Switch into your PC via USB.
1. Download the latest release of [Atmosphere](https://github.com/Atmosphere-NX/Atmosphere/releases) (Download the `atmosphere-(version)-master-(version)+hbl-(version)+hbmenu-(version).zip` release of Atmosphere.)
1. Copy *the contents of* the Atmosphere `.zip` file to the root of your microSD card.
    - If you are prompted to overwrite files, do so.
1. Eject the `UMS` device safely from within your computer's operating system.
1. (If your Hekate is not on the latest version) update Hekate via the steps below.

### **Updating Hekate**

When updating Hekate always make sure to _read the release notes_. They may list important changes and modifications to your system.

When a new version of Hekate releases, you can update by following these steps:

1. Enter RCM and inject the Hekate payload.
    - If you use a modchipped Switch, you can simply just turn your Switch on with the Hekate payload renamed to `payload.bin` on the root of your microSD card.
1. Navigate to `Tools` > `USB Tools` > `SD Card` and plug your Switch into your PC via USB.
1. Download the latest version of [Hekate](https://github.com/CTCaer/Hekate/releases/) (Download the `hekate_ctcaer_(version).zip` release of hekate).
1. Copy the `bootloader` folder from the Hekate `.zip` file to the root of your microSD card. If you are asked to overwrite or merge files while copying, say yes to merge/overwrite them.
1. Eject the `UMS` device safely from within your computer's operating system.
1. Go back to Hekate's main menu and press `Reload` > `Reload` to reload Hekate from your microSD card.
1. From here, you're done and you can boot into CFW.

### **Updating your firmware**

Always check _before_ updating your system firmware if the latest version of Atmosphère _as well_ as the latest version of Hekate support the firmware version you are updating towards.

In addition, updating to or past some firmwares update the gamecard firmware. Reference the table below for information about these.

| Updating from                        | Updating towards                              | Updates gamecard firmware |
| ------------------------------------ | --------------------------------------------- | ------------------------- |
| Below 4.0.0                          | Below 4.0.0                                   | No                        |
| Below 4.0.0                          | 4.0.0 or above                                | Yes                       |
| On or above 4.0.0, but below 9.0.0   | At least 4.0.1 but below 9.0.0                | No                        |
| On or above 4.0.0, but below 9.0.0   | 9.0.0 or above                                | Yes                       |
| On or above 9.0.0, but below 11.0.0  | At least 9.0.1 but below 11.0.0               | No                        |
| On or above 9.0.0, but below 11.0.0  | 11.0.0 or above                               | Yes                       |
| On or above 11.0.0 but below 12.0.0  | At least 11.0.1 but below 12.0.0              | No                        |
| On or above 11.0.0 but below 12.0.0  | 12.0.0 or above                               | Yes                       |
| On or above 12.0.0 but below 14.0.0  | At least 12.0.1 but below 13.2.1              | No                        |
| On or above 12.0.0 but below 14.0.0  | 14.0.0 or above                               | Yes                       |
| On or above 14.0.0                   | Latest supported Atmosphère & Hekate revision | No                        |

If at least one of the versions you are updating towards also updates the gamecard firmware, you will not be able to downgrade below that version without making the gamecard slot unusable until you update.

Atmosphere (and Hekate) come bundled with patches that automatically disable the gamecard slot if it is detected that the system has an older gamecard firmware that would be updated. If you boot into RCM on each boot (for example by using AutoRCM), this means that the gamecard slot will not be updated and you can downgrade below that version. If this happens, you will not be able to use the gamecard slot as long as you are on the newer firmware.

Otherwise, you can safely update your system firmware through the system settings.

!!!warning "Note about autoRCM"
    If you have autoRCM enabled and you're updating your system while in stock firmware, **updating will disable autoRCM** and you will need to enter RCM manually to boot custom firmware again.
    To prevent autoRCM from being disabled, boot CFW on sysMMC and update through settings from there, as booting without AutoRCM <ins>will burn any preserved fuses</ins>.

### **About emuMMC**

sysMMC and emuMMC have separate system firmwares and need to be updated separately.

If you keep your emuMMC offline, you will have to use a gamecard to update your system firmware, synchronize it with another Nintendo Switch or dump an updated firmware from your sysMMC.

### **Updating emuMMC by dumping an updated firmware from your sysMMC**

!!! warning "Do you have an eMMC backup yet?"
    Please do not start this guide without doing a RAW GPP and a BOOT 0/1 eMMC backup!

    You can learn how to make one [here](../user_guide/all/making_essential_backups.md).

!!! danger "Downgrading"
    This guide is made for updating your emuMMC. It is **not** for downgrading. Downgrading at all, sysMMC or emuMMC, is not recommended and not worth it. Downgrading is also very dangerous and can lead to serious complications even when performed correctly.

#### **What you need:**
- The latest release of [TegraExplorer](https://github.com/suchmememanyskill/TegraExplorer/releases)
- The latest release of [Atmosphere](https://github.com/Atmosphere-NX/Atmosphere/releases)

#### **Preparing your microSD card**

1. Boot into Hekate.
1. Go to `Tools` > `USB Tools` > `SD Card` and connect your Switch to your PC via USB.
1. Download the latest release of `TegraExplorer.bin` and place it `sd:/bootloader/payloads`.

Make sure your sysMMC is updated before moving onto the instructions below.

#### **Dumping your sysMMC firmware**

1. Make sure your sysMMC is up to date. If your sysMMC is not up-to-date, boot into Stock or sysCFW and update it through the System Settings.
    - sysCFW is recommended since it preserves e-fuses and preserves AutoRCM (if applicable).
1. Inject `TegraExplorer.bin` using your favourite payload injector (Like you would with Hekate).
    - If you are using a modchipped Switch, you can simply put `TegraExplorer.bin` in `sd:/bootloader/payloads` on your microSD card, then turn on your console and load TegraExplorer via Hekate's payloads menu (`Payloads` > `TegraExplorer.bin`).
1. Using the joystick and the A buttons, select `FirmwareDump.te`, then select `Dump sysmmc`.
    - If navigation doesn't work with your Joycons, navigating using the volume buttons and selecting using the power button also works.
      (This is also required for Switch Lite console users.)
1. Wait about 1-2 minutes for the script to dump your firmware.
1. When the script finishes, press any button.
1. Select `Reboot to bootloader/update.bin`.

#### **Updating your emuMMC with Daybreak**

1. In Hekate go to `Launch -> Atmosphere FSS0 emuMMC`.
1. Once booted, hold `R` while launching a game to boot into the homebrew menu.
1. Find Daybreak in the homebrew menu and launch it.
1. Tap on `Install` and navigate to `sd:/tegraexplorer/Firmware/<latest firmware number>`.
1. Tap on `Continue` and then `Preserve settings`.
    - If you see the message `Warning: exFAT firmware is missing or corrupt`, you likely don't have the exFAT drivers installed on your sysMMC. Just press continue if this is the case.
1. If it is available choose `Install (FAT32 + exFAT)`, otherwise `Install (FAT32)` and then `Continue`.
1. Wait until Daybreak completes installing the dumped firmware.
1. Once it completes, it will ask if you want to reboot. Tap `Reboot`.
1. Once rebooted, launch into emuMMC and verify your system works. You can verify your system has been properly updated in `Settings -> System`.
