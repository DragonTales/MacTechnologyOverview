# 【Mac Technology Overview】（六）Core OS Layer

[TOC]

***

原文地址：[https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html)

***

## 一、概述

The technologies and frameworks in the Core OS layer provide low-level services related to hardware and networks. These services are based on facilities in the Kernel and Device Drivers layer.

Core OS 层的技术和框架提供与硬件和网络相关的底层服务。这些服务基于  Kernel and Device Drivers 的功能。 



![../art/osx_architecture-core_os_2x.png](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/art/osx_architecture-core_os_2x.png)





***

## 二、High-Level Features 高级特性

The Core OS layer implements features related to app security.

Core OS  层 实现与应用程序安全性相关的功能。



***
### 1、Gatekeeper 门禁

Gatekeeper, allows users to block the installation of software that does not come from the Mac App Store and identified developers. If your app is not signed with a Developer ID certificate issued by Apple, it will not launch on systems that have this security option selected. If you plan to distribute your app outside of the Mac App Store, be sure to test the installation of your app on a Gatekeeper enabled system so that you can provide a good user experience.

Xcode supports most of the tasks that you need to perform to get a Developer ID certificate and code sign your app. To learn how to submit your app to the Mac App Store—or test app installation on a Gatekeeper enabled system—read *Tools Workflow Guide for Mac*.



Gatekeeper 允许用户阻止安装 非  Mac App Store  和认证开发者的软件。如果选中了这个安全选项，不是使用 Apple 发行的  Developer ID 证书签名的应用，不会再系统中启动。如果你想在 Mac App Store   之外发型应用，需要测试你的应用在一个启用了 Gatekeeper 的系统上的安装，来保证一个良好的用户体验。

Xcode 支持大多数需要执行的任务，以便获得 开发人员ID证书（Developer ID certificate ） 并对应用程序进行代码签名。关于更多提交你的应用到  Mac App Store，或者测试应用在 启用 Gatekeeper 的系统上的安装，可以阅读 Tools Workflow Guide for Mac 。

***
### 2、App Sandbox 沙盒

App Sandbox provides a last line of defense against stolen, corrupted, or deleted user data if malicious code exploits your app. App Sandbox also minimizes the damage from coding errors. Its strategy is twofold:

如果恶意代码利用你的应用，App Sandbox 提供了防止被盗、损坏或删除用户数据的最后一道防线。App Sandbox还可以将编码错误造成的损害降到最低。其战略有两个方面：



- App Sandbox enables you to describe how your app interacts with the system. The system then grants your app only the access it needs to get its job done, and no more.

  应用程序沙盒使您能够描述 应用程序如何与系统交互。然后，系统只授予你的应用程序 完成任务所需的访问权限，而不再授予。

- App Sandbox allows the user to transparently grant your app additional access by using Open and Save dialogs, drag and drop, and other familiar user interactions.

  App Sandbox 允许用户通过使用 Open 和 Save 对话框、拖放和其他熟悉的用户交互 透明地授予应用程序额外的访问权限。

  

You describe your app’s interaction with the system by setting entitlements in Xcode. For details on all the entitlements available in OS X, see *[Entitlement Key Reference](https://developer.apple.com/library/archive/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html#//apple_ref/doc/uid/TP40011195)*.

您可以通过在 Xcode 中设置 权限（entitlements） 来描述应用程序与系统的交互。有关 OS X中所有可用权利的详细信息，请参阅 *[Entitlement Key Reference](https://developer.apple.com/library/archive/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html#//apple_ref/doc/uid/TP40011195)*.



When you adopt App Sandbox, you must code sign your app (for more information, see [Code Signing](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html#//apple_ref/doc/uid/TP40001067-CH9-SW4)). This is because entitlements, including the special entitlement that enables App Sandbox, are built into an app’s code signature.

For a complete explanation of App Sandbox and how to use it, read *[App Sandbox Design Guide](https://developer.apple.com/library/archive/documentation/Security/Conceptual/AppSandboxDesignGuide/AboutAppSandbox/AboutAppSandbox.html#//apple_ref/doc/uid/TP40011183)*.

采用应用程序沙盒时，必须对应用程序进行代码签名（有关详细信息可参阅 [Code Signing](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html#//apple_ref/doc/uid/TP40001067-CH9-SW4) ）。这是因为授权，包括 启用应用程序沙盒的特殊授权，都内置到应用程序的代码签名中。

对于应用程序沙盒以及如何使用它的完整解释，可以阅读  *[App Sandbox Design Guide](https://developer.apple.com/library/archive/documentation/Security/Conceptual/AppSandboxDesignGuide/AboutAppSandbox/AboutAppSandbox.html#//apple_ref/doc/uid/TP40011183)*。

***
### 3、Code Signing 代码签名

OS X employs the security technology known as *code signing* to allow you to certify that your app was indeed created by you. After an app is code signed, the system can detect any change to the app—whether the change is introduced accidentally or by malicious code. Various security technologies, including App Sandbox and parental controls, depend on code signing.

In most cases, you can rely on Xcode automatic code signing, which requires only that you specify a code signing identity in the build settings for your project. The steps to take are described in Code Signing Your App in *Tools Workflow Guide for Mac*. If you need to incorporate code signing into an automated build system or if you link your app against third-party frameworks, refer to the procedures described in *[Code Signing Guide](https://developer.apple.com/library/archive/documentation/Security/Conceptual/CodeSigningGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005929)*.

For a complete explanation of code signing in the context of App Sandbox, read [App Sandbox in Depth](https://developer.apple.com/library/archive/documentation/Security/Conceptual/AppSandboxDesignGuide/AppSandboxInDepth/AppSandboxInDepth.html#//apple_ref/doc/uid/TP40011183-CH3) in *[App Sandbox Design Guide](https://developer.apple.com/library/archive/documentation/Security/Conceptual/AppSandboxDesignGuide/AboutAppSandbox/AboutAppSandbox.html#//apple_ref/doc/uid/TP40011183)*.



OS X使用了安全技术: `代码签名（code signing）`，允许您确认您的应用程序确实是由您创建的。当一个应用程序的代码被签名后，系统就可以检测到应用程序的任何变化——不管变化是偶然引起的还是恶意代码引起的。各种安全技术，包括应用沙箱和家长控制，都依赖于代码签名。

在大多数情况下，您可以依赖Xcode自动代码签名，这只需要您 在项目的构建设置中 指定一个代码签名标识。使用代码签名 您的应用程序 的步骤描述 在 `Tools Workflow Guide for Mac`。如果您需要将代码签名合并到自动构建系统中，或者将应用程序链接到第三方框架，请参考  *[Code Signing Guide](https://developer.apple.com/library/archive/documentation/Security/Conceptual/CodeSigningGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005929)* 中描述的过程。

有关在App Sandbox上下文中进行代码签名的完整说明，请阅读 *[App Sandbox Design Guide](https://developer.apple.com/library/archive/documentation/Security/Conceptual/AppSandboxDesignGuide/AboutAppSandbox/AboutAppSandbox.html#//apple_ref/doc/uid/TP40011183)* 中的  [App Sandbox in Depth](https://developer.apple.com/library/archive/documentation/Security/Conceptual/AppSandboxDesignGuide/AppSandboxInDepth/AppSandboxInDepth.html#//apple_ref/doc/uid/TP40011183-CH3) 。



***
## 三、Core OS Frameworks

The following technologies and frameworks are in the Core OS layer of OS X:

下面是 OSX 的 Core OS 层的技术和框架：

***
### 1、Accelerate 加速器

The Accelerate framework (`Accelerate.framework`) contains APIs that help you accelerate complex operations—and potentially improve performance—by using the available vector unit. Hardware-based vector units boost the performance of any app that exploits data parallelism, such as those that perform 3D graphic imaging, image processing, video processing, audio compression, and software-based cell telephony. (Because Quartz and QuickTime Kit incorporate vector capabilities, any app that uses these APIs can tap into this hardware acceleration without making any changes.)

The Accelerate framework is an umbrella framework that wraps the vecLib and vImage frameworks into a single package. The vecLib framework contains vector-optimized routines for doing digital signal processing, linear algebra, and other computationally expensive mathematical operations. The vImage framework supports the visual realm, adding routines for morphing, alpha-channel processing, and other image-buffer manipulations. 

For information on how to use the components of the Accelerate framework, see *[vImage Programming Guide](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/vImage/Introduction/Introduction.html#//apple_ref/doc/uid/TP30001001)*, *vImage Reference Collection*, and *[vecLib Reference](https://developer.apple.com/documentation/accelerate/veclib)*. For general performance-related information, see *[Performance Overview](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/PerformanceOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40001410)*.



Accelerate 框架（`Accelerate.framework`） 包含一些api，可以通过使用可用的向量单元，帮助您加速复杂的操作，并可能提高性能。基于硬件的向量单元 可以提高任何利用数据并行性的 应用程序的性能，比如那些执行3D图形成像、图像处理、视频处理、音频压缩 和 基于软件的移动电话 的应用程序。(因为 Quartz 和 QuickTime 工具包 结合了矢量功能，任何使用这些api 的应用程序 都可以在不做任何更改的情况下利用这种硬件加速。)



加速框架是一个伞形框架，它将 `vecLib` 和 `vImage` 框架打包到一个包中。

vecLib 框架包含向量优化的例程，用于进行数字信号处理、线性代数 和 其他高消耗计算的数学操作。

vImage 框架支持可视化领域，为变形、alpha通道处理 和 其他图像缓冲区操作 添加例程。



***
### 2、Disk Arbitration

The Disk Arbitration framework (`DiskArbitration.framework`) notifies your app when local and remote volumes are mounted and unmounted. It also furnishes other updates on the status of remote and local mounts and returns information about mounted volumes. For example, if you provide the framework with the BSD disk identifier of a volume, you can get the volume’s mount-point path.

For more information on Disk Arbitration, see *[Disk Arbitration Framework Reference](https://developer.apple.com/documentation/diskarbitration)*.



Disk Arbitration 框架 (`DiskArbitration.framework`)  在 本地卷和远程卷 被 挂载 和 卸载时，通知应用程序。它还提供关于 远程和本地挂载状态 的其他更新，并返回关于挂载卷的信息。例如，如果为框架提供 卷的BSD 磁盘标识符，则可以获得卷的挂载点路径。

有关 Disk Arbitration 的更多信息，请参见 *[Disk Arbitration Framework Reference](https://developer.apple.com/documentation/diskarbitration)*。



***
### 3、OpenCL

The Open Computing Language (OpenCL) makes the high-performance parallel processing power of GPUs available for general-purpose computing. The OpenCL language is a general purpose computer language, not specifically a graphics language, that abstracts out the lower-level details needed to perform parallel data computation tasks on GPUs and CPUs. Using OpenCL, you create compute kernels that are then offloaded to a graphics card or CPU for processing. Multiple instances of a compute kernel can be run in parallel on one or more GPU or CPU cores, and you can link to your compute kernels from Cocoa, C, or C++ apps.

For tasks that involve data-parallel processing on large data sets, OpenCL can yield significant performance gains. There are many apps that are ideal for acceleration using OpenCL, such as signal processing, image manipulation, and finite element modeling. The OpenCL language has a rich vocabulary of vector and scalar operators and the ability to operate on multidimensional arrays in parallel.

For information about OpenCL and how to write compute kernels, see *[OpenCL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/OpenCL_MacProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008312)*.



开放运算语言 (OpenCL：Open Computing Language) 使高性能并行处理能力的 gpu 可用于通用计算。OpenCL语言 是一种通用的计算机语言，而不只是图形语言；它抽象出在 GPUs 和 CPU 上执行并行数据计算任务所需的底层细节。使用OpenCL，您可以创建计算内核，然后将其卸载到 显卡或CPU上进行处理。一个计算内核的多个实例可以在一个或多个 GPU 或 CPU 内核上并行运行；您可以从 Cocoa、C 或 c++ 应用程序链接到您的计算内核。

对于涉及大型数据集上的数据并行处理的任务，OpenCL 可以产生显著的性能提升。有许多应用程序是使用OpenCL 进行加速的理想选择，比如信号处理、图像处理 和 有限元建模。OpenCL 语言拥有丰富的向量和标量运算符词汇表，并且能够并行地操作多维数组。

有关OpenCL和如何编写计算内核的信息，请参阅 *[OpenCL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/OpenCL_MacProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008312)* 。



***
### 4、Open Directory (Directory Services) 开放目录服务

Open Directory is a directory services architecture that provides a centralized way to retrieve information stored in local or network databases. Directory services typically provide access to collected information about users, groups, computers, printers, and other information that exists in a networked environment (although they can also store information about the local system). You use Open Directory to retrieve information from these local or network databases. For example, if you’re writing an email app, you can use Open Directory to connect to a corporate LDAP server and retrieve the list of individual and group email addresses for the company. 

Open Directory uses a plug-in architecture to support a variety of retrieval protocols. OS X provides plug-ins to support LDAPv2, LDAPv3, NetInfo, AppleTalk, SLP, SMB, DNS, Microsoft Active Directory, and Bonjour protocols, among others. You can also write your own plug-ins to support additional protocols. 

The Open Directory framework (`OpenDirectory.framework`) publishes a programmatic interface for accessing Open Directory services.

For more information on this technology, see *[Open Directory Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/Open_Directory/Introduction/Introduction.html#//apple_ref/doc/uid/TP40000917)*. For information on how to write Open Directory plug-ins, see *[Open Directory Plug-in Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/Open_Dir_Plugin/Introduction/Introduction.html#//apple_ref/doc/uid/TP40000918)*. 



Open Directory 是一种 目录服务体系结构，提供了一种集中的方式 来检索 存储在本地或网络数据库中的信息。目录服务 通常提供对收集到的关于用户、组、计算机、打印机和 存在于网络环境中的其他信息的访问(尽管它们也可以存储关于本地系统的信息)。使用Open Directory 从这些本地 或网络数据库检索信息。例如，如果正在编写电子邮件应用程序，可以使用 Open Directory 连接到 公司LDAP服务器，并检索公司的个人和组电子邮件地址列表。

Open Directory 使用插件架构来支持各种检索协议。OS X 提供了支持 LDAPv2、LDAPv3、NetInfo、AppleTalk、SLP、SMB、DNS、Microsoft Active Directory 和 Bonjour 协议等的插件。您还可以编写自己的插件来支持其他协议。

Open Directory 框架（`OpenDirectory.framework`）发布了变成接口来访问  Open Directory  服务。

更多关于这个技术的信息，可访问  *[Open Directory Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/Open_Directory/Introduction/Introduction.html#//apple_ref/doc/uid/TP40000917)*。更多关于编写 Open Directory  插件的信息，可访问  *[Open Directory Plug-in Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/Open_Dir_Plugin/Introduction/Introduction.html#//apple_ref/doc/uid/TP40000918)*。



***
### 5、System Configuration 系统配置

System Configuration (`SystemConfiguration.framework`) is a framework that helps apps configure networks and determine if networks can be reached prior to connecting with them. The framework includes calls for a user experience when interacting with a captive network. (A captive network, such as a public Wi-Fi hotspot, requires user interaction before providing Internet access.)

Use System Configuration APIs to determine and set configuration settings and respond dynamically to changes in that information. You can also use these APIs to help you determine whether a remote host is reachable and, if it is, to request a network connection so it can provide content to its users. To assist in this, System Configuration does the following:

- It provides access to current network configuration information.
- It allows apps to determine the reachability of remote hosts and start PPP-based connections.
- It notifies apps when there are changes in network status and network configuration.
- It provides a flexible schema for defining and accessing stored preferences and the current network configuration.

To learn more about System Configuration, see *[System Configuration Programming Guidelines](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/SystemConfigFrameworks/SC_Intro/SC_Intro.html#//apple_ref/doc/uid/TP40001065)*.





System Configuration (`SystemConfiguration.framework`) 是一个 帮助应用程序配置网络，并确定网络是否可以在连接之前到达 的框架。该框架包括在与 `captive network` 交互时，对用户体验的调用。(`captive network`，例如：公共Wi-Fi热点，在提供互联网接入之前，需要用户进行交互。)

使用  System Configuration APIs 来确定和设置配置设置，并对信息中的更改 做出动态响应。您还可以使用这些api 来帮助确定 是否可以访问远程主机，如果可以，还可以请求网络连接，以便向用户提供内容。为了在这方面提供帮助，系统配置做了以下工作:

- 它提供对当前网络配置信息的访问。
- 它允许应用程序确定远程主机的可达性，并启动基于ppp的连接。
- 当网络状态和网络配置发生变化时，它会通知应用程序。
- 它为 定义和访问存储的首选项 和 当前网络配置，提供了一个灵活的模式。

关于更多 System Configuration 的信息，可参阅  *[System Configuration Programming Guidelines](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/SystemConfigFrameworks/SC_Intro/SC_Intro.html#//apple_ref/doc/uid/TP40001065)* 。

***
伊织 2019-12-24（二）平安夜



