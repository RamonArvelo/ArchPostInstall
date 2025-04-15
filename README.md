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





