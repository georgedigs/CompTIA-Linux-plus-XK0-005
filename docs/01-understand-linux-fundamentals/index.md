## FHS Basics

**Definition and Purpose of FHS**: The Filesystem Hierarchy Standard organizes the file system in a standardized hierarchical manner. It's not mandatory, but widely adopted as good practice in Linux systems. The FHS helps users understand where to find specific files and directories, aiding in effective system management.

**Comparison with Windows File System**: The transcript contrasts the Linux FHS with the Windows file system. In Windows, the file system is directly tied to physical drives (like C: or D: drives). However, in Linux, the physical hardware is abstracted away. The user may access different directories like 'Downloads' or 'Documents' without knowing which physical disk they reside on. This abstraction provides a seamless experience, with the actual physical storage details being irrelevant to the user's navigation.

**Navigating Linux Filesystem**: The concept of the 'root' of the filesystem is highlighted. The root (/) is different from the 'root directory' (/root). The root (/) is the base of the entire filesystem hierarchy. Understanding this is crucial for navigating Linux systems effectively.

!!! example "Command Example"
    To display the current working directory:

    ```bash
    pwd
    ```
    To display the contents of directories like `/boot`, `/etc`, or any other directory:

    ```bash
    ls /etc
    ls /boot
    ```

**System Files and Directories**: The importance of understanding the specific roles and purposes of various directories in the FHS is emphasized. This knowledge is vital for tasks like mounting devices or identifying connected hardware.

### Various System Files and Directories

**Boot Directory (/boot)**: This directory contains essential files required for booting the system, such as the kernel image, bootloader files, initial RAM disk image, and kernel configuration files. It includes specific files like config (indicating the kernel version) and vmlinuz (the compressed Linux kernel executable).

**Etc Directory (/etc)**: This is where system configuration files are stored. The directory includes numerous .conf files and subdirectories for configuring different aspects of the system, such as network settings through netplan.

**Lib Directory (/lib)**: This directory houses crucial libraries needed for system operation. Examples include libraries for package management (apt), handling printers (cups), Python programming language support, and applications like rhythm box and libreoffice.

**Var Directory (/var)**: Home to variable data, which includes information that changes in size or content over time, like logs and emails. An example is the /var/log subdirectory, containing various logs, including kernel messages.

## The Dev Directory

The "dev" directory is an essential part of the Linux file system, containing device files that allow the system to communicate with hardware devices.

**The "dev" Directory**: The "dev" directory houses device files that enable communication between the operating system and hardware devices like keyboards, USB drives, and more.

**Device File Naming Conventions**: Device files in the "dev" directory follow a naming convention. For example, "sda" typically represents a hard drive, and "a" indicates it's the first hard drive. Additional drives are named "sdb," "sdc," and so on. If there are partitions, they are numbered, like "sda1" or "sdb3," indicating the first partition of the first drive or the third partition of the second drive.

**"tty" Entries**: The "dev" directory may contain "tty" entries, representing terminals or consoles. When you log in via a terminal, it will create a corresponding "tty" entry.

**Special Device Files**: There are special device files in the "dev" directory. For example, "/dev/null" is used to discard information put into it. This can be helpful when dealing with commands that produce both valid output and error messages.

**"/dev/random"**: This special file is used to generate random data, which can be useful for applications that require random data, such as encryption or password generation.

**System Administration**: Device files in the "dev" directory play a vital role in system administration, and understanding how to use them can be valuable for managing a Linux system effectively.

## The Proc Directory - /proc

The /proc directory in Linux serves as a valuable resource for gaining insights into the system's current state, including processes, memory usage, and other system-related information.

**Virtual File System**: The /proc directory is a virtual file system that exists in memory. It's dynamically created when the system boots up, and it holds various types of system-related information.

**Process Information**: One of the primary purposes of the /proc directory is to provide information about running processes. Each running process has a corresponding directory within /proc, identified by its process ID (PID). These directories contain information about the process, including memory usage and associated files.

**Process ID (PID)**: The PID is a numerical value associated with each process and is used to identify and manage processes on the system. The /proc directory contains directories named after these PIDs, allowing easy access to process-related information.

!!! example "Command Example"
    To view the running processes and their PIDs, use the following command:

    ```bash
    ps -e
    ```

**Dynamic Updates**: The /proc directory is dynamically updated in real-time. When a process starts or stops, its corresponding directory is created or removed in /proc. This dynamic nature reflects the current state of processes on the system.

**Other Information**: In addition to process-related data, the /proc directory provides access to various system information files. Examples include information about interrupts, supported file systems, memory usage, networking, and more. These files can be useful for troubleshooting and monitoring system performance.

**/proc/meminfo**: The /proc/meminfo file contains information about system memory usage, including total memory, free memory, and caching/buffering statistics.
!!! example "Command Example"
    To view the memory usage of the system, use the following command:

    ```bash
    /proc$ cat meminfo
    ```

**/proc/net**: The /proc/net directory contains network-related information, such as routing tables and protocol-specific details.

**/proc/sys**: The segment mentions that the next topic of discussion will be the /sys directory. This directory is also essential and used for various system configuration and control settings.

## The Sys Directory
This is another important virtual file system in Linux: the `/sys` file system.

### Understanding the Sys File System

The `/sys` file system, also known as `sysfs`, provides a wealth of information about kernel modules, hardware, and driver information. It's crucial to note that `sysfs` is mounted and accessible from the `/sys` directory.

#### Key Features of the Sys File System

- **Real-Time Updates**: Just like the `/proc` file system, `/sys` is updated on the fly in real time.
- **Kernel and Hardware Information**: Contains data related to kernel modules and hardware devices.
- **Accessible Information**: Offers insight into various system components.

##### Navigating the Sys Directory
!!! example "Command Example"
    Take a look at navigating the `/sys` directory:

    ```bash
    cd /sys
    ls
    ```
    This will display the hrives on the system (examples = sda, sdb):

    ```bash
    cd block/
    ls
    ```

## FHS User Files and Directories

Directories and files relating to users in the Filesystem Hierarchy Standard (FHS). Exploring directories like the home directory, media directory, mount directory, root directory, and the TMP directory.

### The Home Directory

The home directory is a personal space for users. Each user has a directory named after their username where personal files like documents, pictures, and videos are stored. It's represented by a tilde (`~`) in the command prompt.

##### Exploring the Home Directory
!!! example "Command Example"
    Navigating the `/home` directory:

    ```bash
    cd ~
    ls
    ```

## The Media Directory

The media directory is used for mounting and accessing removable media such as DVDs or USB drives. It's typically empty unless a removable media is connected.

##### Accessing the Media Directory
!!! example "Command Example"
    Navigating the `/media` directory:

    ```bash
    cd /media
    ls
    ```

## The Mount Directory

Similar to the media directory, the mount directory is used for temporary mounting of file systems, especially those mounted over the network or external drives used as file systems.

##### Using the Mount Directory
!!! example "Command Example"
    Navigating the `/mnt` directory:

    ```bash
    cd /mnt
    ls
    ```

# The Root Directory

The root directory (`/root`) is the home directory for the root user, similar to the regular user's home directory. It's accessible only by the root user.

##### Accessing the Root Directory as Root User
!!! example "Command Example"
    To access the Root Directory as the root user, you can use the following commands in your terminal:

    ```bash
    sudo -i
    cd /root
    ```

# The TMP Directory

The TMP directory is used for temporary files. It has relaxed permissions, allowing the execution of files, which can be a security concern. Files in this directory are often cleared upon system reboot.

##### Viewing the TMP Directory
!!! example "Command Example"
    To view the contents of the TMP Directory, you can use the following command in your terminal:

    ```bash
    ls /tmp
    ```

## FHS System Binaries and Programs

Focus on system binaries and programs within the File System Hierarchy Standard (FHS). Explore several key directories, including the `bin` directory, the `opt` directory, the `sbin` directory, and user directories.

##### The `bin` Directory
!!! example "Command Example"
    The `bin` directory. You can find it at the root level:

    ```bash
    cd /
    ls
    cd bin
    ls
    ```

Inside the bin directory, you'll find essential binary executables needed for the system to operate. These executables are responsible for various system functions and are often denoted by their green text color, indicating that they are executable files.

##### The `opt` Directory
!!! example "Command Example"
    The `opt` directory. You can find it at the root level:

    ```bash
    cd /
    ls
    cd opt
    ls
    ```

The opt directory is typically empty initially. It serves as a location for optional software packages that are not required for the system but can be installed from third-party sources. This separation allows for easy removal of these programs and isolates them from the rest of the system.

##### The `sbin` Directory
!!! example "Command Example"
    The `sbin` directory. You can find it at the root level:

    ```bash
    cd /
    ls
    cd sbin
    ls
    ```

The sbin directory contains system-level binary executables required for system operation. These executables often require administrator privileges (root access) to run. They are crucial for system maintenance and control.

#####The User Directory
!!! example "Command Example"
    The `user/bin` directory. You can find it at the root level:

    ```bash
    cd /user
    ls
    cd bin
    ls
    ```
Within the `user` directory, you'll find various subdirectories containing executables, libraries, and documentation. Of particular interest is the `user/bin` directory, which is used for local user programs.

The `user/bin` directory holds executables for local user programs. These programs are accessible to individual users and can be run without administrative privileges. You can use these executables in your user account without specifying their full paths, thanks to the PATH environment variable, which includes the directory location.