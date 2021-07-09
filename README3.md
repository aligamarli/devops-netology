
####sfdisk -d /dev/sda | sfdisk -f /dev/sdb
####mdadm --create /dev/md127 --level=mirror --raid-devices=2 /dev/sda1 /dev/sdb1
####mdadm --create /dev/md2 --level=stripe --raid-devices=2 /dev/sda2 /dev/sdb2

-------------------before------------------------------
root@ubuntu:~# lsblk
>NAME               MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
> 
>...
>sda                  8:0    0  2.6G  0 disk
> 
>├─sda1               8:1    0    2G  0 part
> 
>│ └─md127            9:127  0    2G  0 raid1
> 
>└─sda2               8:2    0  512M  0 part
> 
>  └─md2              9:2    0 1020M  0 raid0
> 
>    └─myvg-100mvol 253:0    0  100M  0 lvm
> 
>sdb                  8:16   0  2.6G  0 disk
> 
>├─sdb1               8:17   0    2G  0 part
> 
>│ └─md127            9:127  0    2G  0 raid1
> 
>└─sdb2               8:18   0  512M  0 part
> 
>  └─md2              9:2    0 1020M  0 raid0
> 
>    └─myvg-100mvol 253:0    0  100M  0 lvm
> 
>sdc                  8:32   0   60G  0 disk
> 
>├─sdc1               8:33   0  512M  0 part  /boot/efi
> 
>├─sdc2               8:34   0    1K  0 part
> 
>└─sdc5               8:37   0 59.5G  0 part  /
> 


----------------------after-------------------------------

####$ pvmove -n 100mvol /dev/md2 /dev/md127   переносим lvm 
> $lsblk
>sda                  8:0    0  2.6G  0 disk
> 
>├─sda1               8:1    0    2G  0 part
> 
>│ └─md127            9:127  0    2G  0 raid1>
> 
>│   └─myvg-100mvol 253:0    0  100M  0 lvm   /tmp/new
> 
>└─sda2               8:2    0  512M  0 part
> 
>  └─md2              9:2    0 1020M  0 raid0
> 
>sdb                  8:16   0  2.6G  0 disk
> 
>├─sdb1               8:17   0    2G  0 part
> 
>│ └─md127            9:127  0    2G  0 raid1
> 
>│   └─myvg-100mvol 253:0    0  100M  0 lvm   /tmp/new
> 
>└─sdb2               8:18   0  512M  0 part
> 
>  └─md2              9:2    0 1020M  0 raid0
> 
>sdc                  8:32   0   60G  0 disk
> 
>├─sdc1               8:33   0  512M  0 part  /boot/efi
> 
>├─sdc2               8:34   0    1K  0 part
> 
>└─sdc5               8:37   0 59.5G  0 part  /
> 
####$ mdadm /dev/md127 --fail /dev/sdb1
>  root@ubuntu:/tmp/new# gzip -t /tmp/new/test.gz
  root@ubuntu:/tmp/new# echo $?
  0

####$ dmesg
>[ 4309.540653] md: data-check of RAID array md127
> 
> [ 4319.917861] md: md127: data-check done.
> 
> [ 4397.150311] md/raid1:md127: Disk failure on sdb1, disabling device.
> 
>  md/raid1:md127: Operation continuing on 1 devices.

#### mdadm /dev/md127 --re-add /dev/sdb1  добавляем обратно диск 
