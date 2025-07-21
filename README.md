# 🔐 Reset Forgotten Root Password in RHEL-9/CentOS-10/Fedora Linux

This guide helps you reset a forgotten **root password** on **RHEL**, **CentOS**, or **Fedora** Linux systems.

*** rd.break does not work in RHEL 9.0. or centos stream 10.

> ⚠️ Use this method responsibly. Physical or console access to the machine is required.

---

### 1. Reboot and Access GRUB Menu
- Reboot the system.
- At the GRUB menu, press `e` to edit the default boot entry.

- Otherwise Reboot the system. When the grub bootloader screen appears, use the UpArrow and DownArrow keys or Click on the highlighted option with your mouse to initiate the boot process. to stop the countdown timer. Be very quick, as the timer can be set anything from 1 to 5 seconds.


### 2. Modify Boot Parameters
- Find the line starting with `linux16` or `linux` and append the following at the end:
  ```
  replace "ro" with "rw" and Add "init=/bin/bash" at the end of that line.
  ```
- Press `Ctrl + X` or `F10` to boot with these parameters.

### 3. Remount Root Filesystem (if needed)
```bash
mount -o remount,rw /
```

### 4. Reset the Root Password
```bash
passwd  
```
- Enter the new root password twice when prompted.

### 5. Re-label SELinux Context (only for SELinux-enabled systems)
```bash
touch /.autorelabel
```

### 6. Reboot the System
```bash
exec /sbin/init
```
OR
```bash
reboot -f
```

## 📂 Author
- Created by **Mairazul Khan**


## 🔐 Notes
- Ensure physical access to the system or console access via virtualization.
- This method works for most RHEL, CentOS, and Fedora versions using GRUB2.
