1. make and build the HelloOS.bin

2. A few changes to /etc/default/grub. 
1) comment out GRUB_TIMEOUT_STYLE=hidden
2) set GRUB_CMDLINE_LINUX_DEFAULT="text"
3) set GRUB_TIMEOUT=30

3. sudo update-grub

4. add the following piece to /boot/grub/grub.cfg

menuentry 'HelloOS' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        multiboot2 /boot/HelloOS.bin
        boot
}

5. reboot the VM and will see HelloOS selection from grub
