kickstart
=========


create lvm volume
-----------------

    lvcreate -L 6G -n test system

install ubuntu via kickstart
----------------------------

    LC_CTYPE=C virt-install \
    --debug \
    --autostart \
    --serial pty \
    --accelerate \
    --name=test \
    --ram=1024 \
    --vcpus=2 \
    --os-type=linux \
    --os-variant=ubuntuprecise \
    --network=bridge:br0 \
    --disk=/dev/mapper/system-test \
    --noautoconsole \
    --location='http://de.archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/' \
    --nographics \
    --extra-args='ks=http://kickstart.benjamin-borbe.de/ks.cfg text console=tty0 utf8 console=ttyS0,115200'
