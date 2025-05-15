# Install Arch Linux

* Download Arch Linux ISO
* Download Rufus on Windows
* Make USB bootable with rufus and iso
* Boot image
* Run `loadkeys dk`
* Run `iwctl`
* Run `station wlan0 connect <wifi name>`
* When connected to internet run `archinstall`
  * Choose desktop environment
  * Let the computer select the partitioning?
  * Perhaps install `iwd` and  (`NetworkManager` or `networkmanager` or `network-manager`)
  * Say yes to chroot into arch. Sudo root yes
  * run `pacman -S gnome` then `exit` then `reboot`



# Arch Linux Setup

first, run `sudo pacman -Syu git ansible`

clone the arch setup with ansible repository

```bash```

df