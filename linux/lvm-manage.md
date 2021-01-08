# LVM manage

```text
pvs pvdisplay
lvs lvdisplay
lvextend -L 160G -r /dev/vg0/root
lvreduce -L 792.62G -r /dev/vg0/data
e2fsck -f /dev/mapper/vg0-data （可选-y选项，跳过确认）
```

