# img to bootable

host deps:

```
	sudo apt install qemu qemu-user-static binfmt-support gparted
```

## add space

```
xz -d  <IMG>-full.img.xz
truncate -s +10G <IMG>-full.img
sudo losetup -P /dev/loop20 <img>-full.img
sudo gparted /dev/loop20	//RESIZE
sudo losetup -d /dev/loop20
```

## mount

```
mkdir ./mnt1 ./mnt2
disk -l  <IMG>-full.img

sudo mount -o loop,offset=$((512 * 8192 )) <img>-full.img ./mnt1/
sudo mount -o loop,offset=$((512 * 1056768)) img-full.img ./mnt2/

sudo cp /usr/bin/qemu-aarch64-static  ./mnt2/usr/bin/
sudo cp /etc/resolv.conf ./mnt2/etc/

sudo mount -o bind /dev ./mnt2/dev
sudo mount -o bind /sys ./mnt2/sys
sudo mount -o bind /proc ./mnt2/proc
sudo mount -o bind /dev/pts ./mnt2/dev/pts

sudo chroot ./mnt2 /bin/bash


sudo umount ./mnt2/dev ./mnt2/sys ./mnt2/proc ./mnt2/dev/pts ./mnt2 

```




