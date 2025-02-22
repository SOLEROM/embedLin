# rpi clean conf

## partition boot

* enable ssh
```
touch /boot/ssh
```

* user:user
```
/boot/userconf 
user:$6$JQnutxrsH843i8vi$GWmsceGT8YVXPGqtuJ75YUxX78dTbjC9WWd8iNk6fcXWJX7PhmyAB4ZZZogd4ZDNOm1c522JqAH2ApETSGjGO0
```


*  disable interface name changes
```
/boot/cmdline.txt
net.ifnames=0
```

* add gether

```
config.txt  // append in end of file:
=====================================
dtoverlay=dwc2

cmdline.txt add:
=================
modules-load=dwc2,g_ether

```

* set display size
```
config.txt
========================
hdmi_group=1
hdmi_mode=16
framebuffer_width=1920
framebuffer_height=1080

```

## partition root

* local ip

```
apt-get install ifupdown


/etc/network/interfaces.d/eth0
auto eth0
allow-hotplug eth0
iface eth0 inet static
    address 10.0.0.10
    netmask 255.255.255.0
    gateway 10.0.0.1

/etc/network/interfaces.d/usb0 
auto usb0
allow-hotplug usb0
iface usb0 inet static
    address 10.0.0.11
    netmask 255.255.255.0
    gateway 10.0.0.1


sudo systemctl enable networking

```

* dissable first boot
```
raspi-config nonint do_boot_behaviour B4
```

* tui configs:

```
> raspi-config

	move to x11
	enbale vnc

```

* vnc config to logis as user:

```
> sudo vncpasswd -legacy -service -weakpwd

root/.vnc/config.d/vncserver-x11 
================================
Authentication=VncAuth
Encryption=PreferOn
Password=8c46f601fbba0067


```
