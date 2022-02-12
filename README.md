# Archlinux install

My flimsy scripts for installing archlinux https://github.com/daviskregers/old-dotfiles/tree/v4/install/archlinux
This version has cut off the dotfiles installation part though.

- The `./install-arch.sh` script is for running into the archlinux installation boot
- The `./configure-arch.sh` script is for running after the installation, while in `arch-chroot /mnt`.

### Using pacman proxy

The script will automatically set up pacman mirrors, if you wish to use your own proxy, set an environment variable.

```
export ARCHLINUX_PROXY_HOST=http://192.168.1.X:8099
```

### Dualbooting systemd-boot

If you want to dualboot into windows using systemd-boot, you can use these steps:

```
lsblk -- find the windows EFI partition (should be 100MB size)
sudo mount /dev/sdc2 /mnt
cd /mnt/EFI
sudo cp -ax Microsoft /boot/EFI
```

https://github.com/spxak1/weywot/blob/main/Pop_OS_Dual_Boot.md#22-how-to-add-an-option-for-windows-in-pop_os-boot-menu

### Installation process

1. Boot into archlinux iso
2. pacman -Sy git
3. git clone https://github.com/daviskregers/archlinux-install.git
4. partition drive (GPT, 512M EFI partition, rest for system)
5. Optionally setup proxy
6. cd archlinux-install
6. ./install-arch.sh 
