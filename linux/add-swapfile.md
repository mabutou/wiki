# add swapfile



```text
sudo swapon --show
sudo fallocate -l 1G /swapfile
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576
sudo dd if=/dev/zero of=/swapfile bs=1024 count=524
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo vi /etc/fstab
/swapfile swap swap defaults 0 0
sudo swapon --show
Adjusting the Swappiness Value
cat /proc/sys/vm/swappiness
sudo sysctl vm.swappiness=10
```

### **Adjusting the Swappiness Value**

Swappiness is a Linux kernel property that defines how often the system will use the swap space. Swappiness can have a value between 0 and 100. A low value will make the kernel to try to avoid swapping whenever possible while a higher value will make the kernel to use the swap space more aggressively.

The default swappiness value is 60. You can check the current swappiness value by typing the following command:

```text
cat /proc/sys/vm/swappiness
```

While the swappiness value of 60 is OK for most Linux systems, for production servers you may need to set a lower value.

For example, to set the swappiness value to 10, type:

```text
sudo sysctl vm.swappiness=10
```

To make this parameter persistent across reboots append the following line to the `/etc/sysctl.conf` file:

/etc/sysctl.conf

`vm.swappiness=10` Copy

The optimal swappiness value depends on your system workload and how the memory is being used. You should adjust this parameter in small increments to find an optimal value.

### **Removing a Swap File**

### **Removing a Swap File**

To deactivate and remove the swap file, perform the steps below:

1. First deactivate the swap space by typing:

   ```text
   sudo swapoff -v /swapfile
   ```

2. Next, remove the swap file entry `/swapfile swap swap defaults 0 0` from the `/etc/fstab` file.
3. Finally, delete the actual swapfile file:

   ```text
   sudo rm /swapfile
   ```

