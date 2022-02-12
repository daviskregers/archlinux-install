# Archlinux install

My flimsy scripts for installing archlinux https://github.com/daviskregers/old-dotfiles/tree/v4/install/archlinux
This version has cut off the dotfiles installation part though.

- The `./install-arch.sh` script is for running into the archlinux installation boot
- The `./configure-arch.sh` script is for running after the installation, while in `arch-chroot /mnt`.

If you decide to use it - use carefully. It might be broken at times - so no guarantees that it will work or that it doesn't mess anything up.

If you mess something up and things start breaking - it's probably due to mounts. Usually at that stage it's easier to
restart the machine and start all over.

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

```console
$ pacman -Sy git
$ git clone https://github.com/daviskregers/archlinux-install.git
$ cfdisk (partition drive - GPT, 512M EFI partition, rest for system)
$ export ARCHLINUX_PROXY_HOST=... (optional)
$ ./install-arch.sh 
$ arch-chroot /mnt
$ cd /root
$ ./configure-archlinux.sh 
$ exit
$ reboot
```
