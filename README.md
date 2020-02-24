The ramdisk image for Firefly-RK3288 board and other rockchip based platforms.

### How to generate the ramdisk ###

After cloning, cd to the working directory, and run:

    make

a new initrd.img will be created in the parent directory.

### Credit ###

Based on https://github.com/radxa/initrd.git which is
based on https://github.com/Galland/rk30_linux_initramfs which is
based on fkubi's initramfs who in turn
based on Debian's initramfs.cpio.


#################
http://wiki.t-firefly.com/zh_CN/Firefly-RK3128/compile_kernel.html

创建 linux-boot.img
  创建内存盘
    内核启动时会加载内存盘作为初始的根文件系统，再加载实际的根存储设备，最后切换过去。

    git clone -b fireprime https://github.com/TeeFirefly/initrd.git
    make -C initrd
  打包内核和内存盘
    将 kernel 和 initrd 打包成 linux-boot.img：

    truncate -s "%4" initrd.img
    mkbootimg --kernel arch/arm/boot/zImage --ramdisk initrd.img -o linux-boot.img
