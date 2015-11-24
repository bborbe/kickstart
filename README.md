# kickstart

## create lvm volume


```
# lvremove /dev/system/test
lvcreate -L 6G -n test system
```

## install ubuntu via kickstart

```
LC_CTYPE=C virt-install \
--debug \
--autostart \
--accelerate \
--name=test \
--ram=1024 \
--vcpus=2 \
--os-type=linux \
--os-variant=ubuntutrusty \
--network=bridge:br0 \
--disk=/dev/mapper/system-test \
--location='http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-amd64/' \
--console pty,target_type=serial \
--graphics none \
--extra-args='ks=http://kickstart.benjamin-borbe.de/ks.cfg text console=tty0 utf8 console=ttyS0,115200n8 serial'
```

Static Ip:
```
--extra-args= "ks=http://kickstart.benjamin-borbe.de/ks.cfg  ksdevice=eth0 ip=10.10.21.76 netmask=255.255.255.240 dns=10.10.21.1 gateway=10.10.21.100"
```