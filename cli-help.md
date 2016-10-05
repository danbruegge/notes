A collection of useful CLI commands.

Bash
====
+ restart bash
    ```
    source ~/.bashrc
    OR
    . .bashrc
    ```


Hard drive
==========
+ Mirror hard drive
    + `dd if=/dev/sda of /dev/sdb`
+ Progress of dd
    + `pkill -USR1 dd`
+ View devices, such as: sda, sdc ...
    + `fdisk -l`
+ Disk assignment
    + `df -h`
+ View filesystem label
    + `blkid`
+ View folder size
    + `du -h /path/to/dir`
+ TRIM
    ```
    fstrim -v /
    fstrim -v /home
    ```
+ Clear /var/tmp/
    + `find /var/tmp/ -ctime +0 -delete`


Files
=====
+ View file permissions
    + `ls -l`
    + `ls -hal`
+ chown for different files
    + `chown [[USER]] foo.md bar.md`
+ chmod for folder and files
    + `find -type d -print0 | xargs -0 chmod 755`
    + `find -type f -print0 | xargs -0 chmod 644` 
+ Show filesize
    + `du -ks FILE`
    + `ls -l | grep FILE `
+ Find file
    + `find / -type f -name +.foobar`


Pacman
======
+ Save manually installed packages into a file
    ```
    pacman -Qqe | grep -vx "`pacman -Sqg base base-devel xorg kde gstreamer0.10-plugins`" > datei.txt
    ```
+ [Locating .pac* files](https://wiki.archlinux.org/index.php/Pacman/Pacnew_and_Pacsave#Locating_.pac.2A_files)
+ Get installed packages despite a broken pacman db
    ```
    lostfiles | while read file; do pkgfile -q "$file"; done | awk '!x[$0]++'
    lostfiles | while read file; do pkgfile -q "$file"; done | awk '!x[$0]++' | pacman -S --force -
    pacman -S --force `lostfiles | while read file; do pkgfile -q "$file"; done | awk '!x[$0]++'`
    ```


System
======
+ Show certain system informations
    + `uname --help`
+ Show kernel version
    + `uname -a`
+ Shutdown ... now
    + `shutdown -h now`
+ Show loaded modules
    + `cat /proc/modules`
+ Show memory
    + `free -m -t`
    + `cat /proc/meminfo`


Network
=======
+ Show programs that generate traffic
    + `lsof -i`


Images
======
+ JPG -> PDF - require: _imagemagick_
    + `convert foo.jpg bar.pdf`
+ Adjust image size of multiple images - require: _imagemagick_
    + `mogrify -resize 1024x768 +.jpg`
        + with `-quality [VALUE]` you can specify the quality
    + Better solution
        ```
        for i in $( ls +.jpg); do convert -resize 50% $i re`$i; done
        ```
+ Rotate image
    + `convert -rotate 90 image.jpg image.png`
+ PNGOUT to all images in the folder
    + `for f in +.png; do pngout $f; done`


Documents
=========
+ PDF -> TXT
    + `pdftotext -layout foobar.pdf`


Multimedia
==========
+ mount .iso
    + `mount -o loop image.iso /mnt/<mountpoint>`
+ .bin2iso (mount)
    + `bchunk name.bin name.cue name.iso`
+ .flv -> .mp3
    + `ffmpeg -i "video.flv" -f mp3 -ab 160000 -acodec libmp3lame "video.mp3"`


Internet
========
+ rsync only one file type
    + `rsync -avz --include "*.jpg" --exclude "*" SRC DEST`
