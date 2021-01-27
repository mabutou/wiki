# LVM manage

```text
pvs && pvdisplay
lvs && lvdisplay
验证，（可选-y选项，跳过确认）
e2fsck -f /dev/mapper/vg0-data
e2fsck -f /dev/mapper/vg0-root
先缩容
lvreduce -L 792.62G -r /dev/vg0/data
pvs 查看free空间
再扩容
lvextend -L 160G -r /dev/vg0/root
再次验证
e2fsck -f /dev/mapper/vg0-data
e2fsck -f /dev/mapper/vg0-root
```

删除 LVM

```text
mount –l
umount xxx
lvdisplay 获取需要删除 LV 的 LV name
lvremove /dev/vg0/lv0
删除 VG
vgremove /dev/vg0
```

