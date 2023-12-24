## Understanding Source Code
> **Understanding Source Code:** The fundamental concept of source code in software development. It distinguishes between open-source and closed-source software, providing an understanding of how software programs are created and modified from their source code.<br>

  - Source code is the code that makes up a computer program and is typically not visible or relevant to end users.

  - There are two main approaches to software development: closed source (proprietary) and open source. Closed source code is not publicly available, while open source code is publicly accessible, modifiable, and shareable.

  - Linux has a strong favor for open source software development, making source code accessible to the community.

  - Compiling source code is the process of transforming it into an executable binary that can be run as a program.

  - In Linux, the process of compiling source code involves installing a compiler (GCC), downloading the source code, handling dependencies, configuring, and running a make script to automate compilation.

  - Makefiles are used to automate compilation tasks and simplify the process.

## Compiling from Source on Ubuntu
> **Compiling from Source on Ubuntu:** The process of compiling software programs directly from their source code on Ubuntu Linux. It outlines the steps and considerations required for compiling programs on this distribution.<br>

  - Source code compilation on Linux allows users to download and build software from its source code, providing flexibility and customization options.

  - Linux distributions often use package managers (e.g., APT for Ubuntu, DNF for Red Hat) to simplify software installation. However, compiling from source can be advantageous for specific needs.

  - Building software from source requires essential development tools, including the GCC compiler, which can be installed using package managers.

 - To demonstrate source code compilation, the ["ncdu"](https://dev.yorhel.nl/ncdu) utility is downloaded, extracted, and built from source. Dependencies are checked using the ["configure"](https://dev.yorhel.nl/download/ncdu-1.19.tar.gz) script.
!!! example "Command to install the build-essential package on Ubuntu"
    To get access to the GCC compiler, amongst a whole bunch of other development tools and libraries.:

    ```bash
    sudo apt install build-essential
    ```
    Install wget to install and download things from the internet.:

    ```bash
    sudo apt install wget
    wget URL from internet example (https://dev.yorhel.nl/download/ncdu-1.19.tar.gz)
    tar -xzf ncdu-1.19.tar.gz
    ls
    cd ncdu-1.19.tar.gz
    ```
  - The "Makefile" is a script used to automate the compilation process, simplifying it for users.

  - Compiling from source includes running "make" and, for system-wide installation, "sudo make install."
!!! example "Command to install the build-essential package on Ubuntu"
    Install wget to install and download things from the internet.:

    ```bash
    sudo apt-get install libncurses5-dev
    ```

  - Adding the binary's directory to the system's PATH makes the compiled program accessible without specifying the full path.

  - The process may vary depending on the software, but downloading, extracting, configuring, making, and installing are common steps.

  - Different Linux distributions may have their own package managers and package formats, but the source code compilation process remains relatively consistent.

## Compiling from Source on Rocky Linux
> **Compiling from Source on Rocky Linux:** Focus on compiling programs from source code, but specifically on the Rocky Linux distribution. While the process shares similarities with Ubuntu, there are key differences that are explained in this section.<br>

## RAID (including RAID 0, RAID 1, and RAID 5)
> **RAID (Redundant Array of Independent Disks):** The concept of RAID and its importance in data storage and redundancy. It provides explanations for different RAID levels, including RAID 0, RAID 1, and RAID 5, highlighting their distinct features and use cases.<br>

## Storage Types (including file, block, and object storage)
> **Storage Types:** The various types of storage systems used in computing, including file storage, block storage, and object storage. It elucidates the characteristics of each storage type and when to choose one over the other based on specific requirements.<br>

## FUSE (Filesystem in Userspace)
> **FUSE (Filesystem in Userspace):** Introducing the concept of FUSE, which stands for Filesystem in Userspace. It explains how FUSE enables users to mount filesystems without requiring superuser privileges and offers insights into its practical applications in Linux.<br>







