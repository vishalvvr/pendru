# Pendru
Pendru is an hack to create multi boot USB drive. 
Just format once and copy bootable ISO files into a specific directory(/bootable/iso) in your flash drive.
No need to reformat your drive every time to create boot Pendrive; only replace/add ISO file into the directory(/bootable/iso) and add/update the ISO file entry in ```/bootable/grub.cfg``` then you are good to boot.


# Setup
- git clone <this repo> 
- grub.iso is a bootable image; just create a bootable flash drive using any utility(fedora-media-writer or Rufus or dd utility)
-- ```sudo dd bs=4M if=grub.iso of=/dev/sdX``` (X - your USB device entry)
- Above step will create a bootable USB flash drive which only uses up to 20MB on your device and rest is unallocated space
- Now use any CLI or disk partition utility to format the unallocated space to FAT partition
-- **NOTE**: The FAT partition should be labelled as "PENDRU", this label is internally used by the grub bootloader(grub.iso) to locate grub.cfg and bootable ISO files.
- The last step is to copy the bootable directory into the USB drive

```bash  
├── bootable

│   ├── grub.cfg

│   └── iso
```
##### Now above steps have made your flash drive multi boot usb device, you just have to take care of two things
1. ```/bootable/iso/:``` - copy your bootable Linux ISO files into this directory
2. ```/bootable/grub.cfg:``` - add/update the ISO file entry into this grub config file -- **NOTE**: kernel and initrd service entry might differ for a distro to distro; just locate isolinux.cfg file(isolinux/isolinux.cfg) in your ISO and search for KERNEL and INITRD entries and update accordingly in the grub.cfg


### NOTE:
- This device is now capable of booting any and many OS from single
- No need to reformat the drive to change the OS
- Also, you may use this flash drive for normal usage (transfer file and etc)
- Only make sure that you don't change the ```/bootable``` directory entries unless required


###### Keep Hacking :)
