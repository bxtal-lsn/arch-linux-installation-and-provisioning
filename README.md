# Arch Linux

## Install Arch Linux

* Download Arch Linux ISO
* Download Rufus on Windows
* Make USB bootable with rufus and iso
* Boot image
* Run `loadkeys dk`
* Run `iwctl`
* Run `device list`
* Run `station wlan0 scan` and nothing will show until running `station wlan0 get-networks`
* Run `station wlan0 connect <wifi name>`
* press `CTRL + D` to exit `iwctl`
* check if the internet connection is available with `ping google.com`
* When connected to internet run `archinstall`
  * Choose desktop environment
  * Let the computer select the partitioning?
  * Perhaps install `iwd` and  (`NetworkManager` or `networkmanager` or `network-manager`)
  * 
  * 

## Arch Linux Setup in chroot

Say yes to chroot into arch. Sudo root yes

first, run `sudo pacman -Syu git ansible sudo xorg networkmanager`

Then create a user with sudo permissions, add him to wheel and make not have to insert password all the goddamn time

``````shell
username -m bxtal
passwd bxtal
``````

``````shell
usermod -aG wheel bxtal	
``````

uncomment these lines in visudo `wheel ALL=(ALL:ALL) ALL` and `wheel ALL=(ALL:ALL) NOPASSWD: ALL`

enter visudo with `visudo`

Then, enable display manager and networkmanager services

``````shell
sudo systemctl enable gdm.service
sudo systemctl enable NetworkManager.service
``````

run `exit` then `reboot`

## Further Arch Linux Installation

### Install LTS Kernel

After the reboot it is recommended to install an LTS kernel for stability

check linux version with `uname r`

Install LTS kernel and LTS headers

``````shell
sudo pacman -Syu linux-lts
sudo pacman -Syu linux-lts-headers
``````

### Install  Yaourt

Yet AnOther User Repository Tool. Can install packages from official repository as well as AUR. open /etc/pacman.conf and add these lines at the bottom

``````shell
[archlinuxfr]
SigLevel = Never
Server = "http://repo.archlinux.fr/$arch"
``````

install yaourt wirh `sudo pacman -Syu yaourt`

sync yaourt with `yaourt -Syy`

### Installing Codecs and Plugins



clone the arch setup with ansible repository

``````shell
git clone git@github.com:bxtal-lsn/arch-linux-installation-and-provisioning.git
``````

cd into `ansible`

* `pacman.yml` contains all packages to be installed
* `arch-setup.yml` executes pacman for each package defined in `pacman.yml`
* `fish-setup` installs fish plugins via `fisher` which should be installed with `arch-setup.yml`

First, run `ansible-playbook arch-setup.yml` 
Then run `ansible-playbook fish-setup.yml`

