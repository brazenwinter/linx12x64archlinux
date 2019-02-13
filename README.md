# linx12x64archlinux
Short guide to setup Archlinux on a Linx 12x64 Cherry Trail Tablet

What doesnt work:

Bluetooth Audio (problem with setting bitrate, sending and receiving files 
works)
Cameras front and rear

Installing Arch Linux

Set up arch linux on a bootable USB stick/SD card and copy the files in this 
repository to the card as you will need them later, proceed with an install as 
normal. 

Wifi Drivers

I used a microusb to Ethernet dongle for connecting to the internet during 
install, however if you do not have one you can set up wifi drivers by copying 
4345r6nvram.txt to /lib/firmware/brcm/brcmfmac43455-sdio.txt and copy 
brcmfmac43455-sdio.clm_blob to /lib/firmware/brcm/. restart the driver with 
modprobe -r brcmfmac && modprobe brcmfmac.

Grub bootloader

If using Grub as a bootloader use the 64 bit EFI setup method (older 
models use 32 bit EFI so you will need to check) use 
https://wiki.archlinux.org/index.php/GRUB#UEFI_systems as a guide to installing 
the bootloader.

Before Restarting after Install

Tablet has habit of suspending every few seconds wen used with the foldable 
keyboard. Editing /etc/systemd/logind.conf handlesuspendkey and handlelidswitch 
to ignore fixes this issue (though it makes it impossible to suspend by closing 
the lid unfortunately, maybe there's a workaround?) 

For screen rotation to work properly in Gnome or KDE copy 
61-sensor-local.hwdb to /etc/udev/hwdb.d/61-sensor-local.hwdb

Reboot the Tablet
