Cara install
cd ~/img/openwrt-imagebuilder-25.12.5-armsr-armv8.Linux-x86_64/bin/targets/armsr/armv8
IMG=~/.local/var/pmbootstrap/chroot_native/home/pmos/rootfs/qcom-msm89x7.img
LOOP=$(sudo losetup -fP --show $IMG)
sudo mount ${LOOP}p2 /mnt
sudo rm -rf /mnt/* /mnt/.[!.]* 2>/dev/null
sudo tar -xzpf openwrt-25.12.5-armsr-armv8-generic-rootfs.tar.gz -C /mnt
ls -l /mnt/sbin/init
sync; sudo umount /mnt; sudo losetup -d $LOOP
pmbootstrap flasher flash_rootfs
