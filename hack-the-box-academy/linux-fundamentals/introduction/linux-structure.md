---
description: https://academy.hackthebox.com/module/18/section/94
---

# Linux Structure

### History

Many events led up to creating the first Linux kernel and, ultimately, the Linux operating system (OS), starting with the Unix operating system's release by Ken Thompson and Dennis Ritchie (whom both worked for AT\&T at the time) in 1970. The Berkeley Software Distribution (BSD) was released in 1977, but since it contained the Unix code owned by AT\&T, a resulting lawsuit limited the development of BSD. Richard Stallman started the GNU project in 1983. His goal was to create a free Unix-like operating system, and part of his work resulted in the GNU General Public License (GPL) being created. Projects by others over the years failed to result in a working, free kernel that would become widely adopted until the creation of the Linux kernel.

许多事件促成了第一个Linux 内核的诞生并最终产生了Linux 操作系统。Linux 操作系统起源于 Ken Thompson 和 Dennis Ritchie 于 1970 年发行的 Unix 操作系统。伯克利软件发行版 BSD 于 1977 年发布，但是因为其包含了由 AT\&T 所有的 Unix 代码，所以 BSD 的发展受到了法律的限制。Richard Stallman 于 1983 年启动了 GNU 项目，他的目标是创建一个免费的类 Unix 的操作系统。他的部分工作成果促成了 GNU 通用公开协议 （GPL）的创建。然而多年以来，他们都未能创建一个广泛采用的免费的、自由的内核，直至 Linux 内核的创建。

At first, Linux was a personal project started in 1991 by a Finnish student named Linus Torvalds. His goal was to create a new, free operating system kernel. Over the years, the Linux kernel has gone from a small number of files written in C under licensing that prohibited commercial distribution to the latest version with over 23 million source code lines (comments excluded), licensed under the GNU General Public License v2.

起初，Linux 是一个名为 Linux Torvalds 的芬兰学生于 1991 年启动的私人项目。他的目标是创建一个全新的、免费的操作系统内核。多年来，Linux 内核已经从少量用 C 编写的文件，在禁止商业发行的许可下，发展到拥有超过 2300 万行源代码(不包括注释)的最新版本，在 GNU 通用公共许可证 v2 下获得许可。

Linux is available in over 600 distributions (or an operating system based on the Linux kernel and supporting software and libraries). Some of the most popular and well-known being Ubuntu, Debian, Fedora, OpenSUSE, elementary, Manjaro, Gentoo Linux, RedHat, and Linux Mint.

Linux 有超过 600 个发行版（一个基于 Linux 内核并提供软件和库支持的操作系统）。最受欢迎也是最知名的发行版有 Ubuntu、Debian、Fedora、OpenSUSE、

Linux is generally considered more secure than other operating systems, and while it has had many kernel vulnerabilities in the past, it is becoming less and less frequent. It is less susceptible to malware than Windows operating systems and is very frequently updated. Linux is also very stable and generally affords very high performance to the end-user. However, it can be more difficult for beginners and does not have as many hardware drivers as Windows.

通常来说，人们认为 Linux 比其他的操作系统要更加安全。尽管 Linux 在过去有许多的内核漏洞，但是如今已变得越来越少。比起 Windows 操作系统，Linux 更不容易受到恶意软件的影响，同时其更新也非常频繁。Linux 也非常的稳定，并且一般能够给终端用户提供非常高的性能。然而，比起 Windows 操作系统，Linux 对初学者更加的不友好并且没有 Windows 那么多的硬件驱动。

Since Linux is free and open-source, the source code can be modified and distributed commercially or non-commercially by anyone. Linux-based operating systems run on servers, mainframes, desktops, embedded systems such as routers, televisions, video game consoles, and more. The overall Android operating system that runs on smartphones and tablets is based on the Linux kernel, and because of this, Linux is the most widely installed operating system.

因为 Linux 是免费且开源的，所以任何人都可以修改商业的或非商业的发行版的源代码。基于 Linux 的操作系统可以运行在服务器上、大型主机上、桌面上以及嵌入式系统上，比如路由器、电视机、游戏主机等。运行在智能手机和平板电脑上的所有安卓操作系统都是基于 Linux 内核的，所以 Linux 是世界上使用最广泛的操作系统。

Linux is an operating system like Windows, iOS, Android, or macOS. An OS is software that manages all of the hardware resources associated with our computer. That means that an OS manages the whole communication between software and hardware. Also, there exist many different distributions (distro). It is like a version of Windows operating systems.

Linux 是一个类似于 Windows、iOS、安卓或 macOS 的操作系统。操作系统是一个软件，其管理着与计算机相关的所有硬件资源，这意味着 OS 管理者软件和硬件之间的所有通信。就像 Windows 操作系统有很多版本一样，Linux 也存在许多不同的发行版（distro）。

With the interactive instances, we get access to the Pwnbox, a customized version of Parrot OS. This will be the primary OS we will work with through the modules. Parrot OS is a Debian-based Linux distribution that focuses on security, privacy, and development.

***

***

### Philosophy

Linux follows five core principles:

Linux 遵循以下 5 个核心原则：

<table data-header-hidden><thead><tr><th width="294.5"></th><th></th></tr></thead><tbody><tr><td><strong>Principle</strong></td><td><strong>Description</strong></td></tr><tr><td><code>Everything is a file</code></td><td>All configuration files for the various services running on the Linux operating system are stored in one or more text files.</td></tr><tr><td>一切皆文件</td><td>运行在 Linux 操作系统上的各种服务的配置文件都被存储在一个或多个文本文件中。</td></tr><tr><td><code>Small, single-purpose programs</code></td><td>Linux offers many different tools that we will work with, which can be combined to work together.</td></tr><tr><td>小的，单一用途的程序</td><td>Linux 提供了许多不同的工具，我们可以串联地使用他们。</td></tr><tr><td><code>Ability to chain programs together to perform complex tasks</code></td><td>The integration and combination of different tools enable us to carry out many large and complex tasks, such as processing or filtering specific data results.</td></tr><tr><td>将应用程序链接在一起以执行复杂任务的能力</td><td>不同工具的集成和组合允许我们进行许多巨大的、复杂的任务。比如处理或过滤特定数据集。</td></tr><tr><td><code>Avoid captive user interfaces</code></td><td>Linux is designed to work mainly with the shell (or terminal), which gives the user greater control over the operating system.</td></tr><tr><td>避免强制用户界面</td><td>Linux 旨在使用 shell 进行工作，这使得用户对操作系统有更大的控制权。</td></tr><tr><td><code>Configuration data stored in a text file</code></td><td>An example of such a file is the <code>/etc/passwd</code> file, which stores all users registered on the system.</td></tr><tr><td>将配置数据存储在文本文件中</td><td>这样的文件的一个例子就是 /etc/passwd ，该文件存储了系统中所有已注册的用户</td></tr></tbody></table>

***

### Components

| **Component**     | **Description**                                                                                                                                                                                                                                                                                                                                 |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Bootloader`      | A piece of code that runs to guide the booting process to start the operating system. Parrot Linux uses the GRUB Bootloader.                                                                                                                                                                                                                    |
| `OS Kernel`       | The kernel is the main component of an operating system. It manages the resources for system's I/O devices at the hardware level.                                                                                                                                                                                                               |
| `Daemons`         | Background services are called "daemons" in Linux. Their purpose is to ensure that key functions such as scheduling, printing, and multimedia are working correctly. These small programs load after we booted or log into the computer.                                                                                                        |
| `OS Shell`        | The operating system shell or the command language interpreter (also known as the command line) is the interface between the OS and the user. This interface allows the user to tell the OS what to do. The most commonly used shells are Bash, Tcsh/Csh, Ksh, Zsh, and Fish.                                                                   |
| `Graphics server` | This provides a graphical sub-system (server) called "X" or "X-server" that allows graphical programs to run locally or remotely on the X-windowing system.                                                                                                                                                                                     |
| `Window Manager`  | Also known as a graphical user interface (GUI). There are many options, including GNOME, KDE, MATE, Unity, and Cinnamon. A desktop environment usually has several applications, including file and web browsers. These allow the user to access and manage the essential and frequently accessed features and services of an operating system. |
| `Utilities`       | Applications or utilities are programs that perform particular functions for the user or another program.                                                                                                                                                                                                                                       |

***

### Linux Architecture

The Linux operating system can be broken down into layers:

Linux 操作系统可以分成如下几层：

<table data-header-hidden><thead><tr><th width="330.5"></th><th></th></tr></thead><tbody><tr><td><strong>Layer</strong></td><td><strong>Description</strong></td></tr><tr><td><code>Hardware-硬件层</code></td><td>Peripheral devices such as the system's RAM, hard drive, CPU, and others.-外围设备，如系统的RAM、硬盘驱动器、CPU等</td></tr><tr><td><code>Kernel-内核</code></td><td>The core of the Linux operating system whose function is to virtualize and control common computer hardware resources like CPU, allocated memory, accessed data, and others. The kernel gives each process its own virtual resources and prevents/mitigates conflicts between different processes.-Linux操作系统的核心，其功能是虚拟化和控制常见的计算机硬件资源，如CPU、分配的内存、访问的数据等。内核为每个进程提供自己的虚拟资源，并防止/减轻不同进程之间的冲突。</td></tr><tr><td><code>Shell</code></td><td>A command-line interface (<strong>CLI</strong>), also known as a shell that a user can enter commands into to execute the kernel's functions.-命令行界面(CLI)，也称为shell，用户可以在其中输入命令来执行内核的功能。</td></tr><tr><td><code>System Utility-系统实用程序</code></td><td>Makes available to the user all of the operating system's functionality.-为用户提供操作系统的所有功能。</td></tr></tbody></table>

***

### File System Hierarchy

The Linux operating system is structured in a tree-like hierarchy and is documented in the [Filesystem Hierarchy](http://www.pathname.com/fhs/) Standard (FHS). Linux is structured with the following standard top-level directories:

Linux操作系统以树状层次结构构成，并在文件系统层次结构标准(FHS)中进行了记录。Linux由以下标准顶级目录构成:

![iamge](https://academy.hackthebox.com/storage/modules/18/NEW\_filesystem.png)



<table data-header-hidden><thead><tr><th width="179.5"></th><th></th></tr></thead><tbody><tr><td><strong>Path</strong></td><td><strong>Description</strong></td></tr><tr><td><code>/</code></td><td>The top-level directory is the root filesystem and contains all of the files required to boot the operating system before other filesystems are mounted as well as the files required to boot the other filesystems. After boot, all of the other filesystems are mounted at standard mount points as subdirectories of the root.-顶级目录是根文件系统，包含了在挂载其他文件系统之前引导操作系统所需的所有文件，以及引导其他文件系统所需的文件。引导之后，所有其他文件系统都作为根目录的子目录挂载到标准挂载点。</td></tr><tr><td><code>/bin</code></td><td>Contains essential command binaries.-包含必要的命令二进制文件。</td></tr><tr><td><code>/boot</code></td><td>Consists of the static bootloader, kernel executable, and files required to boot the Linux OS.</td></tr><tr><td><code>/dev</code></td><td>Contains device files to facilitate access to every hardware device attached to the system.</td></tr><tr><td><code>/etc</code></td><td>Local system configuration files. Configuration files for installed applications may be saved here as well.</td></tr><tr><td><code>/home</code></td><td>Each user on the system has a subdirectory here for storage.</td></tr><tr><td><code>/lib</code></td><td>Shared library files that are required for system boot.</td></tr><tr><td><code>/media</code></td><td>External removable media devices such as USB drives are mounted here.</td></tr><tr><td><code>/mnt</code></td><td>Temporary mount point for regular filesystems.</td></tr><tr><td><code>/opt</code></td><td>Optional files such as third-party tools can be saved here.</td></tr><tr><td><code>/root</code></td><td>The home directory for the root user.-root用户的主目录。</td></tr><tr><td><code>/sbin</code></td><td>This directory contains executables used for system administration (binary system files).</td></tr><tr><td><code>/tmp</code></td><td>The operating system and many programs use this directory to store temporary files. This directory is generally cleared upon system boot and may be deleted at other times without any warning.</td></tr><tr><td><code>/usr</code></td><td>Contains executables, libraries, man files, etc.</td></tr><tr><td><code>/var</code></td><td>This directory contains variable data files such as log files, email in-boxes, web application related files, cron files, and more.-该目录包含可变数据文件，如日志文件、电子邮件收件箱、web应用程序相关文件、cron文件等。</td></tr></tbody></table>
