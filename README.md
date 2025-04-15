# ArchPostInstall
Post-Install Arch Linux

# Configuración de archivos del sistema.

## Pacman

`sudo nano /etc/pacman.conf`

```
# Misc options  
 Color  
 ParallelDownloads = 10  
 ILoveCandy  
```

## Pacman

`sudo nano /etc/sudoers`


```
 Defaults env_reset,pwfeedback
 
```

## Gestión de energía (KDE PLASMA)

```
sudo pacman -S powerdevil power-profiles-daemon
```

```
sudo systemctl enable --now power-profiles-daemon.service
```
## Bluetooth

```
sudo systemctl enable --now bluetooth
```
## AUR 

### YAY

```
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

### PAMAC

```
yay -S libpamac-full pamac-all
```

### OCTOPI

```
yay -S octopi
```
## Bash Scripts

```
sudo pacman -S bash-completion
```

## Herramientas de compilación

```
sudo pacman -S linux-headers base-devel
```
## Fuse

```
sudo pacman -S fuse fuse2fs fuseiso
```
## MDNS para carpetas compartidas en red

```
sudo pacman -S avahi nss-mdns
```
---
`sudo nano /etc/nsswitch.conf`

```
hosts: mymachines mdns_minimal [NOTFOUND=return] resolve [!UNAVAIL=return] files myhostname dns
```
---
```
sudo systemctl enable --now avahi-daemon
```

## Firewall

```
sudo pacman -S firewalld python-pyqt6
```

```
sudo systemctl enable --now firewalld
```

```
sudo firewall-cmd --set-default-zone=home
sudo firewall-cmd --permanent --add-service=mdns
```
## Plymouth

```
sudo pacman -S plymouth
```
---
`sudo nano /etc/mkinitcpio.conf`

añadir `plymouth`
```
HOOKS=(base udev plymouth autodetect microcode modconf kms keyboard keymap consolefont block filesystems fsck)
```
---
### Grub
`sudo nano /etc/default/grub`

```
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet splash"
```
### Systemd-boot
`sudo nano  /boot/loader/entries/*.conf `

add `quiet` and `splash`
```
options root=PARTUUID=df4a860f-0cad-4bd0-8c75-e245a41eeab2 zswap.enabled=0 rootflags=subvol=@ rw rootfstype=btrfs quiet splash
```

```
sudo mkinitcpio -P
```
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```






