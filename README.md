# ArchGuide
A Guide to help you install archlinux easily without hurting your brain

## ArchLinux Installation and setting up users guide:


#### (use the archwiki installation guide if you don't know how to do a certain step)

- Download your iso 
- Boot from the .iso (either in VirtualBox or by making a bootable USB)
-  Partition your disks, "lsblk", "cfdisk /dev/<THENAMEOFDISK>"
-  Format your disks (ext4 for boot and root)
-  Mount your disks, mount the boot partition to /mnt/boot, mkdir /mnt/boot
-  "pacstrap /mnt base base-devel linux linux-firmware vim"
-  Generate your fstab file "genfstab -U /mnt export to /mnt/etc/fstab"
-  Chroot into Arch "arch-chroot /mnt"

-  Install grub and network manager "pacman -S networkmanager grub"
-  Make network manager run at startup "systemctl enable NetworkManager"
-   Configure Grub "grub-install /dev/sda && grub-mkconfig -o /boot/grub/grub.cfg"
-   set password for root user, "passwd"
-   Configure local and timezone
 "ln -sf /usr/share/timezone/<REGION> /etc/localtime"

> Edit (vim) /etc/locale.gen
>> uncomment en_US.UTF-8 UTF-8 and other needed locales.

> Generate the locales by running: 
>> "locale-gen"

> Create the locale.conf file, and set the LANG variable accordingly: 

>> "vim /etc/locale.conf"

>>> LANG=en_US.UTF-8


-  exit chroot, unmount, and reboot into your arch environment

## Users creation and finalizing:

-  create user, "useradd -mg wheel <USERNAME>"
-   set password for new user, "passwd <USERNAME>"

- uncoment line "wheel ALL=(ALL) ALL", vim etc/sudoers
>> add line, "Defaults !tty_tickets" (prevents asking for root passwd second time)

- install a Dekstop Environment or a Window Manager
>> if Window Manager, then install "xorg-server" and "xorg-xinit" using pacman

- show that you're cool by running neofetch :D

Thx.
