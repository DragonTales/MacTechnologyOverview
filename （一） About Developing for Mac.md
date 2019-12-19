#  【Mac Technology Overview】（一） About Developing for Mac

[toc]

***

原文地址：https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/About/About.html#//apple_ref/doc/uid/TP40001067-CH204-TPXREF101

***

The OS X operating system combines a stable core with advanced technologies to help you deliver world-class products on the Mac platform. Knowing what these technologies are, and how to use them, can help streamline your development process, while giving you access to key OS X features.

OSX 操作系统包一个稳定的内核，有先进的技术来帮助你在 Mac平台上发布世界一流水准的产品。

了解有哪些技术，这些技术如何使用，可以帮助你简化开发流程，帮助你进入 OSX 的主要功能。



![../art/MacBookProDesktop_2x.png](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/art/MacBookProDesktop_2x.png)





***

## 一、At a Glance 

This guide introduces you to the range of possibilities for developing Mac software, describes the many technologies you can use for software development, and points you to sources of information about those technologies. It does not describe user-level system features or features that have no impact on software development.

这个指南向你介绍 Mac 上可以进行应用开发的范围，描述了你可以用于软件开发的技术，也告诉你这些技术的信息源。它不会描述用户级别的系统功能，或者对应用开发没有意义的功能。



### 1、OS X Has a Layered Architecture with Key Technologies in Each Layer （OSX 具有分层架构，每一层都有关键技术）

It’s helpful to view the implementation of OS X as a set of layers. The lower layers of the system provide the fundamental services on which all software relies. Subsequent layers contain more sophisticated services and technologies that build on (or complement) the layers below.

将 OSX 的实现看做一组层次 很有帮助。系统的低层提供软件依赖的基础服务。后续的层，依赖或者补充低层，包含更多复杂的服务和技术。



![Layers of OS X](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/art/osx_architecture-layers_2x.png)
**Figure I-1** Layers of OS X



The lower the layer a technology is in, the more specialized are the services it provides. Generally, technologies in higher layers incorporate lower-level technologies to provide common app behaviors. A good rule of thumb is to use the highest-level programming interface that meets the goals of your app. Here is a brief summary of the layers of OS X.

越是低层次的技术，提供的服务越专业。一般而言，高层次的技术协同低层次的技术来提供常用的app行为。好的经验法则是，使用高层次的编程接口来满足应用的需要。这里是 OS X 层级的简单说明：

- The Cocoa (Application) layer includes technologies for building an app’s user interface, for responding to user events, and for managing app behavior. 

  Cocoa (Application) layer 包含 构建应用用户界面、响应用户时间、管理应用行为的技术。

- The Media layer encompasses specialized technologies for playing, recording, and editing audiovisual media and for rendering and animating 2D and 3D graphics.

   Media 层包含 播放、录制、编辑 试听媒体，渲染和动画 2D和3D图形 的专业技术。

- The Core Services layer contains many fundamental services and technologies that range from Automatic Reference Counting and low-level network communication to string manipulation and data formatting.

  Core Services 层包含很多基础服务和技术，从 ARC 和低层次的 网络通信 到字符串操作 和数据拼接。

- The Core OS layer defines programming interfaces that are related to hardware and networking, including interfaces for running high-performance computation tasks on a computer’s CPU and GPU. 

  Core OS  层定义了硬件和网络相关的编程接口，包含在电脑的 CPU 和 GPD 上运行高性能的计算服务。

- The Kernel and Device Drivers layer consists of the Mach kernel environment, device drivers, BSD library functions (`libSystem`), and other low-level components. The layer includes support for file systems, networking, security, interprocess communication, programming languages, device drivers, and extensions to the kernel. 

  Kernel and Device Drivers 层由 Mach 内核环境，设备驱动，BSD 库功能，低层次组件 组成。这个层包含文件系统、网络、安全、进程通信、编程语言、设备驱动、内核拓展的支持。



**Relevant Chapters（相关章节）:** [Cocoa Application Layer](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CocoaApplicationLayer/CocoaApplicationLayer.html#//apple_ref/doc/uid/TP40001067-CH274-SW1), [Media Layer](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW1), [Core Services Layer](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-BCICAIFJ), [Core OS Layer](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html#//apple_ref/doc/uid/TP40001067-CH9-SW1), [Kernel and Device Drivers Layer](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemTechnology/SystemTechnology.html#//apple_ref/doc/uid/TP40001067-CH207-BCICAIFJ)





### 2、You Can Create Many Different Kinds of Software for Mac （你可以在 Mac 上创建不同类型的软件）

Using the developer tools and system frameworks, you can develop a wide variety of software for Mac, including the following:

使用开发工具和系统框架，你可以开发很多种类型的软件，包含如下类型：



- **Apps.** Apps help users accomplish tasks that range from creating content and managing data to connecting with others and having fun. OS X provides a wealth of system technologies such as app extensions and handoff, that you use to extend the capabilities of your apps and enhance the experience of your users.

  Apps 帮助用户实现功能，从创建内容，到管理数据，到和他人联系、娱乐。OSX 提供了一系列的系统技术，比如 应用拓展和传送，你可以用来拓展你的应用功能，增强用户体验。

  

- **Frameworks and libraries.** Frameworks and libraries enable code sharing among apps.

  Frameworks and libraries 可以在应用之间共享代码。

  

- **Command-line tools and daemons.** Command-line tools allow sophisticated users to manipulate data in the command-line environment of the Terminal app. Daemons typically run continuously and act as servers for processing client requests.

  命令行工具（ Command-line tools）允许熟练的用户在终端的命令行环境下操作数据。守护进程（Daemons）通常连续运行，作为服务器来处理客户端请求。

  

- **App plug-ins and loadable bundles.** Plug-ins extend the capabilities of other apps; bundles contain code and resources that apps can dynamically load at runtime.

  插件拓展了其它应用的功能; bundles 包含应用在运行时可以动态加载的代码和资源。

  

- **System plug-ins.** System plug-ins, such as audio units, kernel extensions, I/O Kit device drivers, preference panes, Spotlight importers, and screen savers, extend the capabilities of the system.

  系统插件，比如音频单元、内核拓展、I/O Kit设备驱动程序、偏好设置面板、聚焦导入、屏幕保护，拓展了系统的功能。



**Relevant Chapter:** [Creating Software Products for the Mac Platform](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF101)



***

### 3、When Porting a Cocoa Touch App, Be Aware of API Similarities and Differences （当移植 Cocoa Touch App 应用时，注意API 的相似之处和区别）

The technology stacks on which Cocoa and Cocoa Touch apps are based have many similarities. Some system frameworks are identical (or nearly identical) in each platform, including Foundation, Core Data, and AV Foundation. This commonality of API makes some migration tasks—for example, porting the data model of your Cocoa Touch app—easy. 

Cocoa 和 Cocoa Touch 应用的所基于的技术栈有很多相似之处。一些系统框架在不同平台上几乎是相似的，比如 Foundation, Core Data, and AV Foundation。API 的这种通用性 使一些迁移任务成为可能，比如，从你的  Cocoa Touch  应用中导入数据模型。



Other migration tasks are more challenging because they depend on frameworks that reflect the differences between the platforms. For example, porting controller objects and revising the user interface are more demanding tasks because they depend on AppKit and UIKit, which are the primary app frameworks in the Cocoa and CocoaTouch layers, respectively. 

其它迁移任务可能会有些挑战，因为他们所给予的框架在不同平台上表现不同。比如，移植 控制器对象和修改用户界面是更艰巨的任务，因为他们基于 AppKit 和 UIKit，他们分别是 Cocoa and CocoaTouch 层的主要应用框架。



**Relevant Chapter:** [Migrating from Cocoa Touch](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW1)



## 二、See Also

Apple provides developer tools and additional information that support your development efforts.

Apple 提供支持你开发 的 开发工具和附加信息。



Xcode, Apple’s integrated development environment, helps you design, create, debug, and optimize your software. You can download Xcode from the Mac App Store.

Xcode, Apple 的 IDE， 帮助你设计、开发、调试和优化你的应用。你可以在 MAS 下载 Xcode。



For an overview of the developer tools for OS X, see the [Xcode Apple Developer webpage](https://developer.apple.com/xcode/). For an overview Xcode functionality, read *[Xcode Overview](https://developer.apple.com/library/archive/documentation/ToolsLanguages/Conceptual/Xcode_Overview/index.html#//apple_ref/doc/uid/TP40010215)*.

有关OS X 开发工具的概述，可以查看  [Xcode Apple Developer webpage](https://developer.apple.com/xcode/). 想了解 Xcode 的功能，可以阅读 *[Xcode Overview](https://developer.apple.com/library/archive/documentation/ToolsLanguages/Conceptual/Xcode_Overview/index.html#//apple_ref/doc/uid/TP40010215)*.



The OS X Developer Library contains the documentation, sample code, tutorials, and other information you need to write OS X apps. You can access the OS X Developer Library from the [Apple Developer website](https://developer.apple.com/library/mac/navigation/) or from Xcode. In Xcode, choose Help > Documentation and API Reference to view documents and other resources in the Organizer window.

OSX 开发库包含文件、样例代码和教程，还有你所需要的其它信息。你可以从  [Apple Developer website](https://developer.apple.com/library/mac/navigation/)  获取 OSX 开发库，也可以从 Xcode 的 Help > Documentation，还有 API 参考来查看文档和其它资源。



In addition to the OS X Developer Library, there are other sources of information on developing different types of software for Mac:

在OSX 开发库之外，开发不同类型的 Mac 软件 有很多信息资源：

- **Apple Open Source**. Apple makes major components of OS X—including the UNIX core—available to the developer community. To learn about Apple’s commitment to Open Source development, visit [Open Source Development Resources](http://developer.apple.com/opensource/). To learn more about some specific Open Source projects, such as Bonjour and WebKit, visit [Mac OS Forge](http://www.macosforge.org/).

  Apple 将 OSX 的核心组件，包含 UNIX 内核，开源给开发者社区使用。



- **BSD**. Berkeley Software Distribution (BSD) is an essential UNIX-based part of the OS X kernel environment. Several excellent books on BSD and UNIX are available in bookstores. But you can also find additional information on any of the websites that cover BSD variants—for example, [The FreeBSD Project](http://www.freebsd.org/).

  BSD 是 OSX 内核环境中重要的基于 Unix 的部分。一些优秀的关于 BSD 和 Unix 的书很有必要。不过你也可以从关于 BSD 的网站上查找其它信息，比如  [The FreeBSD Project](http://www.freebsd.org/)。



- **Third-party books**. Several excellent books on Mac app development can be found online and in the technical sections of bookstores.

  第三方数据，一些关于 Mac app 开发的书籍和技术章节，可以在书店中找到。




























