Load the bootable usb

```Bash
lsblk -f

fdisk -l
```

use fdisk -l to check for the efi partition and general partition

![[1000058168.jpg]]

  

mount the general partion first using :

  

```Bash
mount /dev/nvme0n1p6 /mnt

mount /dev/nvme0n1p3 /mnt/boot

arch-chroot /mnt

grub-install —target=x86_64-efi —efi-directory=/boot

grub-mkconfig -o /boot/grub/grub.cfg
```

  

  

check the boot diectory whether all these files are there

![[1000058169.jpg]]

now exit and reboot

  

  

reference :

[https://youtu.be/dF5qzXQGCR8?si=TG0BTUEhuewiSmcq](https://youtu.be/dF5qzXQGCR8?si=TG0BTUEhuewiSmcq)