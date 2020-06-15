# Pendru
Pendru is an hack to create multi boot usb drive. 
Just format once and copy bootble ISO files into a specific directory(/bootable/iso) in your flash drive.
No need to reformat your drive everytime to create boot pendrive only replace/add ISO into the directry(/bootable/iso) and add/update the ISO file entry in /bootable/grub.cfg then your are good to boot.


# Setup
- git clone <this repo> 
- grub.iso is a bootable image just create a bootable flash drive using any utility(fedora-media-writter or rufus or dd utility)
-- sudo dd bs=4M if=grub.iso of=/dev/sdX (x your usb device entry)
- Above step will create a bootable usb flash drive which only uses upto 20MB on your device and rest is unallocated space
- Now use any CLI or disk partition utility to format the unallocated space to FAT partition
-- NOTE: The FAT partition should be labeled as "PENDRU", this lable is internally used by the grub bootloder(grub.iso) to locate grub.cfg and bootable ISO files.
- Last step is to copy the bootable directory into the USB drive.
├── bootable
│   ├── grub.cfg
│   └── iso

##### Now above steps have made you flash drive multi boot usb device, you just have to takecare of two things:
1. /bootable/iso/: copy your bootable linux ISO files into this directroy
2. /bootable/grub.cfg: add/update the ISO file entry into this grub config file
-- NOTE: kernel and initrd service entry might differ for distro to distro just locate isolinux.cfg file(isolinux/isolinux.cfg) in your ISO and search for KERNEL and INITRD entries and update accordingly in the grub.cfg    


### NOTE:
- This device is now caplable of booting any and many OS from single
- No need to reformat the drive to change the OS
- Also you may use this flash drive for normal usage (transfer file and etc)
- Only make sure you dont change the /bootable directrory entries unless required


###### Keep Hacking :)
