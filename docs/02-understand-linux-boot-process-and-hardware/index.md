
# understand Linux boot process and hardware

> **The focus on the Linux boot process. Emphasis on the Linux kernel and associated hardware. BIOS and UEFI** Explanation of the BIOS (Basic Input/Output System) as firmware. Introduction to UEFI (Unified Extensible Firmware Interface) as a modern replacement for BIOS.<br>


> **Identifying PCI Devices** Explanation of identifying PCI (Peripheral Component Interconnect) devices. Noting that PCI is a legacy technology, unlike USB.<br>

## Partition Tables and Firmware

**Differences Between MBR and GPT**

The differences between MBR (Master Boot Record) and GPT (GUID Partition Table) in the context of disk partitioning.

When you have a disk and you want to store data on it, you can't just put data on it without any preparation. Instead, the disk needs to be formatted.

But before formatting, it needs something called a **partition table**. 

## Partition Table Styles
> **Partition Tables** Two different partition tables, specifically MBR (Master Boot Record) and GPT (GUID Partition Table).<br>
There are two main styles of partition tables: MBR and GPT. These two styles are quite different.

**MBR (Master Boot Record)**

**MBR** is the older of the two and has been widely used. Its biggest advantage is its compatibility with various systems and boot processes. However, it has limitations compared to GPT.

**GPT (GUID Partition Table)**

**GPT** is more modern and advanced. It offers more features and flexibility compared to MBR. GPT is suitable for larger disks, supports a higher number of partitions, and provides better support for UEFI booting and data integrity.

**Choosing Between MBR and GPT**

The choice between MBR and GPT depends on your specific needs and hardware. If you have a legacy system or require maximum compatibility, MBR might be the better choice. However, if you have a modern system with larger disks and need advanced features, GPT is usually the preferred option. Your decision should be based on your specific requirements.

## External Hardware
> **Peripherals** Focus on working with peripherals, particularly USB devices. Mention of commands to identify connected USB devices.<br>
- External Hardware in Linux:
  - Mnaging external hardware components in Linux.

- **USB devices** are common external hardware used for storing data and possibly even as a boot source.

- **PCI Devices** Older Peripheral Component Interconnect (PCI) interface used to connect devices like SCSI, modems, and network cards.

- **Importance of Hardware Management**: Understanding and managing external hardware components is crucial, especially for Linux+ examination.

- **lspci Command**: The `lspci` command for listing PCI devices in Linux.

- **Using man Command**: Using the `man` command to access manual pages for Linux utilities.

- **Options for lspci**: The use of various options like `-v`, `-vv`, `-vvv`, `-b`, `-k`, and `-D` with `lspci` for detailed information.

- **lsusb Command**: The `lsusb` command for listing USB devices in Linux.

- **Accessing lsusb Manual Pages**: How to access manual pages for the `lsusb` command using `man`.

- **Using lsusb**: The use of `lsusb` to list connected USB devices and obtain verbose information with `-v`.

- **dmidecode Command**: The `dmidecode` command for inspecting hardware information, including BIOS, motherboard, processor, and memory details.

- **Accessing dmidecode Manual Pages**: How to access manual pages for the `dmidecode` command using `man`.

- **Using dmidecode**: The use of `dmidecode` with `-t` to inspect various hardware details, requiring superuser privileges with `sudo`.

## Understanding the Boot Process
> **Linux Boot Process Overview** High-level overview of the Linux boot process. Mention of components like BIOS/UEFI and the bootloader Grub2.<br>
- **BIOS/UEFI:** The boot process starts with the BIOS (or UEFI) firmware, which initiates the boot sequence. BIOS and UEFI are often used interchangeably, even though modern systems usually use UEFI.

- **POST (Power-On Self Test):** After the BIOS/UEFI is invoked, the system performs a POST, which is a set of hardware self-tests to ensure everything is functioning correctly.

- **Bootloader:** The bootloader, such as GRUB2 (the most common one), is loaded by BIOS/UEFI. The bootloader's job is to load the Linux kernel.

- **Kernel (vmlinuz):** The Linux kernel (vmlinuz) is a compressed image that is hardware-agnostic and generic. It forms the core of the operating system.

- **initrd (Initial RAM Disk):** The initrd is a RAM disk loaded in memory. It contains kernel modules necessary to identify hardware and allow the full kernel to be loaded.

- **Kernel Modules:** Initrd loads necessary kernel modules, enabling the kernel to mount the hard drive and access other modules stored on it.

- **System Initialization:** Once the kernel is fully loaded, control is handed over to the system initialization process, which varies (e.g., SysVinit, Upstart, or systemd). In modern systems, systemd is often used to manage system services and initialize the system.

- **Operational System:** After system initialization, the Linux system becomes fully operational, and users can log in, run services, and perform regular tasks.

## The Bootloader
> **Grub2** A closer look at the Grub2 bootloader and its role in the boot process.<br>

- **Bootloader Evolution:** The evolution of Linux bootloaders, starting with LILO, followed by GRUB (GRUB Legacy), and finally, GRUB2 (often referred to as just GRUB in casual terms).

- **GRUB2 Features:** GRUB2 is a significant improvement over its predecessors as it can handle UEFI firmware and GPT partition style, making it more compatible with modern systems.

- **GRUB Configuration File:** The configuration file for GRUB2 is typically located in `/etc/default/grub` on Debian-based systems and `/boot/grub2/grub.cfg` on Red Hat-based systems (like Rocky Linux).

- **Modifying Configuration:** Users should not modify `grub.cfg` directly but should instead make changes in `/etc/default/grub`. After making changes, the `update-grub` command (on Debian-based systems) or `grub2-mkconfig` (on Red Hat-based systems) is used to apply the modifications to `grub.cfg`.
One big distinction about GRUB2, now, we could handle UEFI firmware, which means we could handle the GPT partition style.

!!! warning "Warning Message"
    This is where the grub.cfg file is located.

    !!! example "root location of grub2 configuration file"
    You're not meant to modify this configuration file directly.

    ```bash
    root@systemn: cd /boot/grub ls
    ```
    !!! example "Location of grub2 configuration file for modification indirectly"
    This is the location to modify the configuration file indirectly.

    ```bash
    root@systemn: cd /etc
    root@systemn:/etc$ cd default
    root@systemn:/etc/default$ cat grub
    ```

    !!! example "To update changes run command below"
    if you change this file, run 'update-grub' afterwards to update.

    ```bash
    root@systemn:/etc/default$ update-grub

    ```

- **Distribution Differences:** Red Hat-based systems explicitly use the directory name `GRUB2`, while Debian-based systems often refer to GRUB2 as just GRUB. The command for generating the configuration file also differs between distributions.

- **Understanding Differences:** It's important to understand these distribution-specific differences and commands when working with Linux bootloaders.

## Boot Sources
> **Different Boot Sources** Explanation of various boot sources beyond just hard drives. The ability to boot kernel images from a network.<br>
- Bootloader Evolution: The text discusses the historical evolution of Linux bootloaders, starting with LILO and its limitations with MBR-based systems.

- **GRUB Legacy**: The original GRUB, referred to as "GRUB Legacy," allowed users to choose the operating system during boot through a menu. Its configuration was stored in `/boot/grub/menu.lst`.

- **Transition to GRUB2**: GRUB Legacy was replaced by GRUB2, a completely rewritten and more versatile bootloader. It's often referred to as just "GRUB" in casual terms.

- **GRUB2 Features**: GRUB2 has the capability to handle UEFI firmware and GPT partition style, making it suitable for modern systems.

- **GRUB Configuration File**: The configuration file for GRUB2 is typically located in `/etc/default/grub` on Debian-based systems and 
`/boot/grub2/grub.cfg` on Red Hat-based systems (e.g., Rocky Linux).

- **Modifying Configuration**: Users should make changes to `/etc/default/grub` rather than directly modifying grub.cfg. The changes are applied using the `update-grub` command on Debian-based systems or grub2-mkconfig on Red Hat-based systems.

- **Distribution Differences**: Red Hat-based systems explicitly use the directory name GRUB2, while Debian-based systems often refer to GRUB2 as just "GRUB." The command for generating the configuration file differs between distributions.

- **Understanding Differences**: It's important to be aware of these distribution-specific differences and commands when working with Linux bootloaders.

- **Boot Sources in Linux**: The text discusses various boot sources in Linux, including PXE (preboot execution environment), network booting, CD/DVD, USB drives, and live operating systems for forensics and analysis.

## Kernel Panic
> **Kernel Panic** Introduction to kernel panic, what it is, and how to identify its potential causes. Real-world applications of solving kernel panics using backups.<br>

- **Kernel Panic**: Kernel panic occurs when the Linux kernel stops running in memory, causing the entire system to crash.

- **Causes of Kernel Panic**: Kernel panic can happen due to various reasons, including driver issues, hardware problems (e.g., memory or CPU issues), malware infections, or problems during a kernel update.

- **Backup Kernel**: It's essential to have a working backup of the kernel before performing updates to allow for a rollback in case of issues.

- **Diagnosing Kernel Panic**: To diagnose kernel panic issues, check log files such as kern.log, syslog, and dmesg for kernel-related messages, although detailed diagnosis often requires kernel expertise.

- **Utilizing Alternative Kernel Images**: Linux systems often keep backup kernel images, allowing users to boot from a previous working configuration in case of kernel issues. Access to these images is typically available through the GRUB menu during system boot.

- **GRUB Menu**: The GRUB menu allows users to choose different kernel images during system boot, providing a way to recover from kernel panic situations.

- **Troubleshooting**: Understanding how to access the GRUB menu and selecting alternative kernel images is a practical solution to recover from kernel panic issues.

!!! example "Log files location"
    These are some location you could findthe reasons for the error!.

    ```bash
    root@systemn: cd /var
    root@systemn:/var$ ls
    root@systemn:/var$ cd log
    root@systemn:/var/log$ ls
    root@systemn:/var/log$ cat kern.log
    root@systemn:/var/log$ clear
    root@systemn:/var/log$ cat syslog
    root@systemn:/var/log$ clear
    root@systemn:/var/log$ cat dmesg
    ```
        
    This is where you will find old kernal images to rolback too.

    ```bash
    root@systemn: cd /boot
    root@systemn:/boot$ ls
    ```

!!! tip
    To restart the system manually.
    ```bash
    root@systemn: shutdown -r now
    ```
    Hold down the shift button, what happens is you will be presented with the grub menu and you can choose different images such as a resuce image.


