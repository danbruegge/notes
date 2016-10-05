Systemwide A4
-------------
```
echo a4 >> etc/papersize
```

Require: **libpaper**


German keyboard layout X11 
---------------------------
```
localectl set-x11-keymap de nodeadkeys
```


Pacman update mirrorlist
------------------------
```
# reflector --verbose -l 200 -p http --sort rate --save /etc/pacman.d/mirrorlist
```

Require: **reflector**


xfce4 clipman popup
-------------------
Add to key shortcuts

```
xfce4-popup-clipman
<super>-c
```


bash better autocompletion
--------------------------
```
pacman -S bash-completion
```


win7 > usb
----------
1. install [MBR](http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/)
    + create primary NTFS-partition
    + set bootflag
2. now copy all files from the iso
3. install syslinux on the stick
    + `dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb`
