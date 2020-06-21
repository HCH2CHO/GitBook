### 无法安装grub到dev/sda

```
efi系统分区
/
```

- 问题可能是因为之前装Ubuntu的引导器没有删除掉，以致于无法正常安装。解决办法，使用boot-repair修复

- 感觉自己真是要把能踩的坑都踩一遍一样，经过md5验证发现我下的两个镜像都tm有问题，我也是醉了。差不多一周时间都耗在了上面。人生苦短，用什么ubuntu

- 转了一圈，还是/+/boot+/home+swap的分区方法，引导器放在默认磁盘下，真TM挥霍光阴。

- 在被迫了解了BIOS/UEFI/legacy——MBR/GPT——FAT32/NTFS之后，还学了点grub的东西，然后又扯出动态磁盘这一说。

- 还有人说要关电源里的快速启动。。。

- 去TM的efi分区，挂载到这里。系统完全识别不了。放弃18.04.4，回去装18.04

- 在第20+次重装之前，我在windows里对未分配的磁盘新建了一下，终于可以在GUN Grub里识别出我装Linux的磁盘了。然而引导文件还是点进去是空的，只能手动引导！但至少能开机了。。。

- 我TM又得跟Acer提bug了。哦，又被敷衍了，竟然说Linux自行测试，我TM买的是电脑不是windows

- 每次开关安全模式好像还得重启一次才生效

- ```
  cd /boot/efi/EFI
  cp -R ubuntu/* BOOT/
  cd BOOT
  cp grubx64.efi bootx64.efi
  ```

- ```
  >ls
  (hd0),(hd0,gt1),(hd1,gt2),(hd1,gt3) and so on
  >ls (hdN,msdosX)/boot/grub #顺序查找，直到找到
  以(hd0,gt1)
  
  set root=(hd0,gt1)
  set prefix=(hd0,gt1)/boot/grub
  insmod normal
  normal
  ```

- 这里面似乎还有腾傲在搅和。

- 结果最后是腾傲的锅，md，偌大一个中国互联网，竟然没有人用腾傲+ubuntu么