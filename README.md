# Kickstart

## Create LVM volume


```
# lvremove /dev/system/test
lvcreate -L 6G -n test system
```

## Install Ubuntu via Kickstart

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

### Static Ip:

```
--extra-args= "ks=http://kickstart.benjamin-borbe.de/ks.cfg ksdevice=eth0 ip=10.10.21.76 netmask=255.255.255.240 dns=10.10.21.1 gateway=10.10.21.100"
```

## Copyright and license

    Copyright (c) 2016, Benjamin Borbe <bborbe@rocketnews.de>
    All rights reserved.
    
    Redistribution and use in source and binary forms, with or without
    modification, are permitted provided that the following conditions are
    met:
    
       * Redistributions of source code must retain the above copyright
         notice, this list of conditions and the following disclaimer.
       * Redistributions in binary form must reproduce the above
         copyright notice, this list of conditions and the following
         disclaimer in the documentation and/or other materials provided
         with the distribution.

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
    "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
    LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
    A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
    OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
    SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
    LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
    DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
    THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
    (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
    OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
