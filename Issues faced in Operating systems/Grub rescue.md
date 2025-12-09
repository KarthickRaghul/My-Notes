![[1000058129.jpg]]

```Bash
set prefix=(hd0,gpt3)/grub
insmod normal
normal
```

  

After Logging into the system :

```Bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
grub-install /dev/nvme0n1
```