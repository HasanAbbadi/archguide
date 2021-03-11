# archguide
A GUide to help you install archlinux easily without hurting your brain

# ArchLinux Installation and setting up users guide:


# (use the archwiki installation guide if you don't know how to do a certain step)

0. Download your iso 
1. Boot from the .iso (either in VirtualBox or by making a bootable USB)
2. Partition your disks, "lsblk", "cfdisk /dev/<THENAMEOFDISK>"
3. Format your disks (ext4 for boot and root)
4. Mount your disks, mount the boot partition to /mnt/boot, mkdir /mnt/boot
5. "pacstrap /mnt base base-devel linux linux-firmware vim"
6. Generate your fstab file "genfstab -U /mnt export to /mnt/etc/fstab"
7. Chroot into Arch "arch-chroot /mnt"

8. Install grub and network manager "pacman -S networkmanager grub"
9. Make network manager run at startup "systemctl enable NetworkManager"
10. Configure Grub "grub-install /dev/sda && grub-mkconfig -o /boot/grub/grub.cfg"
11. set password for root user, "passwd"
12. Configure local and timezone
 "ln -sf /usr/share/timezone/<REGION> /etc/localtime"
.................(

Edit  /etc/locale.genand uncomment  en_US.UTF-8 UTF-8and other needed locales. Generate the locales by running: 

 locale-gen

 Create the locale.conf(5) file, and set the LANG variable accordingly: 

 /etc/locale.conf

 LANG=en_US.UTF-8
)........................


13. exit chroot, unmount, and reboot into your arch environment

# Users creation and finalizing:

14. create user, "useradd -mg wheel <USERNAME>"
15. set password for new user, "passwd <USERNAME>"

16. uncoment line "wheel ALL=(ALL) ALL", vim etc/sudoers
>> add line, "Defaults !tty_tickets" (prevents asking for root passwd second time)

17. install a Dekstop Environment or a Window Manager
>> if Window Manager, then install "xorg-server" and "xorg-xinit" using pacman

18. show that you're cool by running neofetch :D

Thx.
