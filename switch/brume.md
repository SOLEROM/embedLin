# brume gl switch

* https://www.gl-inet.com/products/gl-mv1000/

## SW-OS

* openwrt https://github.com/gl-inet/openwrt
* ubuntu  https://github.com/gl-inet/mv1000-ubuntu-image

## user space tools
* https://openwrt.org/docs/guide-user/network/vlan/switch_configuration
* 

```
jeff@garage:~$ swconfig list
Found: switch0 - mdio-bus.0

jeff@garage:~$ swconfig dev switch0 help
switch0: mdio-bus.0(Atheros AR8327), ports: 7 (cpu @ 0), vlans: 128
     --switch
	Attribute 1 (int): enable_vlan (Enable VLAN mode)
	Attribute 2 (none): reset_mibs (Reset all MIB counters)
[...]

```


