#!/usr/bin/env bash

# settings
device=${1:-'/dev/zero'}
arch_image="${HOME}/Downloads/linux/rpi/ArchLinuxARM-rpi-2-latest.tar.gz"
arch_image_url='https://archlinuxarm.org/os/ArchLinuxARM-rpi-2-latest.tar.gz'
mountpoint='/mnt/arch'

echo $device

exit

## umask
umask 007

# cleanup
umount ${device}*
dd if=/dev/zero of=${device} bs=1M count=8
partprobe

# bootstrap
mkdir -p $mountpoint/{boot,root}
mkdir -p $arch_image
cd $mountpoint

# partition
## delete partition table
sfdisk --delete -w auto $device
partprobe

## create partitions
sfdisk $device << EOF
, +100M, c
, +27G, 83
,+2G, 82
EOF
partprobe

## create FS
mkfs.vfat ${device}1
mkfs.f2fs ${device}2
mkswap ${device}3

mount ${device}2 root
mount ${device}1 root/boot


# get image
if [[ ! -f $arch_image ]]; then
    wget \
        -c \
        -O $arch_image \
        $arch_image_url
fi

# install
bsdtar -xpf $arch_image -C $mountpoint/root
sync
umount -l root

# cleanup
cd
rm -fr $mountpoint
