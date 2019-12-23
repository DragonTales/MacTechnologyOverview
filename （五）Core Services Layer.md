# 【Mac Technology Overview】（五）Core Services Layer 核心服务层

[TOC]

***

https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html

***

## 一、概述

The technologies in the Core Services layer are called *core services* because they provide essential services to apps but have no direct bearing on the app’s user interface. In general, these technologies are dependent on frameworks and technologies in the two lowest layers of OS X—that is, the Core OS layer and the Kernel and Device Drivers layer. 

 Core Services 层的技术之所以成为 核心服务，是因为它们提供了 基础的服务，但没有在应用的用户界面上直接显示出来。通常来说，这些技术都依赖于 OSX 最下面两层（Core OS 层 和 Kernel and Device Drivers 层）的框架和技术。



![../art/osx_architecture-core_services_2x.png](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/art/osx_architecture-core_services_2x.png)





***

## 二、High-Level Features  高级别的功能

The following sections describe some of the key technologies available in the Core Services layer. 

以下部分 描述了 核心服务层中可用的一些关键技术：

***
### 1、Social Media Integration  

Two frameworks that make it easy for users to share content with various social networking services from within your app:

以下两个框架 可以使用户便捷地从应用程序中与各种社交网络服务共享内容：

- **Accounts** (`Accounts.framework`). The Accounts framework provides access to supported account types that are stored in the Accounts database. 

  Accounts 框架提供对存储在 Accounts 数据库中的受支持帐户类型的访问。

- **Social** (`Social.framework`). The Social framework provides an API for sending requests to supported social media services that can perform operations on behalf of your users.

  社交框架提供了一个API，用于向支持的社交媒体服务发送请求，这些服务可以代表用户执行操作。

  

When you use the Accounts framework, your app does not need to be responsible for storing account login information because an `ACAccount` object stores the users login credentials for services such as Twitter and Facebook. Users can grant your app permission to use their account login credentials, bypassing the need to enter their user name and password. If no account for a particular service exists in the user’s Accounts database, you can help them create and save an account from within your app. To learn more about the Accounts framework, see *[Accounts Framework Reference](https://developer.apple.com/documentation/accounts)*. 

使用 Accounts 框架时，应用程序不需要负责存储帐户登录信息，因为 `ACAccount` 对象会存储用户登录Twitter 和 Facebook 等服务的凭据。用户可以授予应用程序使用其帐户登录凭据的权限，而无需输入其用户名和密码。如果在 用户帐户数据库中 不存在特定服务的帐户，则可以帮助他们从应用程序中创建和保存帐户。要了解有关 Accounts 框架的更多信息，请参阅  *[Accounts Framework Reference](https://developer.apple.com/documentation/accounts)*。



The Social framework provides a simple interface for accessing the user’s social media accounts, including Facebook and Sina Weibo, a Chinese microblogging website. Apps can use this framework to post status updates and images to a user’s account. The Social framework works with the Accounts framework to provide a single sign-on model for the user and to ensure that access to the user’s account is approved. For more information about the Social API, see *[Social Framework Reference](https://developer.apple.com/documentation/social)*.

该社交框架提供了 访问用户社交媒体账户的简单界面，包括Facebook 和 新浪微博。应用程序可以使用此框架将状态更新和图片 发布到用户帐户。Social框架与Accounts框架协同工作，为用户提供单点登录模型，并确保对用户帐户的访问得到批准。有关社交API的更多信息，请参见 *[Social Framework Reference](https://developer.apple.com/documentation/social)*。



***
### 2、iCloud Storage

From a user’s perspective, iCloud is a simple feature that automatically makes their personal content available on all of their devices. When you adopt iCloud, OS X initiates and manages uploading and downloading of data for the devices associated with an iCloud account.

从用户的角度来看，iCloud是一个简单的功能，它可以自动让他们的个人内容在所有设备上都可用。当您采用iCloud时，OS X 会启动并管理与iCloud帐户关联的设备的数据上载和下载。



There are three types of iCloud storage that your app can take advantage of:

您的应用程序可以利用三种类型的iCloud存储：

- **Document storage**. Document storage is for user-visible file-based content, such as presentations or documents, or for other substantial file-based content, such as the state of a complex game.

  文档存储：文档存储用于用户可见的基于文件的内容，如演示文稿或文档，或用于其他实质性的基于文件的内容，如复杂游戏的状态。

- **Key-value storage**. Key-value storage is for sharing small amounts of data—such as preferences or bookmarks—among instances of your app.

  键值对存储：键值存储用于在 你的应用程序实例之间 共享少量数据，如偏好设置或书签。

- **Core Data storage**. Core Data storage supports server-based, multidevice database solutions for structured content. (Core Data storage is built on document storage.)

  核心数据存储：核心数据存储支持 结构化内容的 基于服务器的 多设备数据库解决方案。（核心数据存储建立在文档存储之上。）

  

Many apps can benefit from using more than one type of storage. For example, a complex strategy game could employ document storage for its game state, and key-value storage for scores and achievements.

许多应用程序可以从使用多种类型的存储中获益。例如，一个复杂的策略游戏可以使用文档存储作为其游戏状态，使用关键值存储作为分数和成绩。



**Important:** To use iCloud storage in your app, you need to get an appropriate provisioning profile for your development device and request the appropriate entitlements in your Xcode project. To learn more about these tasks, see Provisioning Your System and Configuring Entitlements in *Tools Workflow Guide for Mac*.

To learn more about adding iCloud storage to your app, read *[iCloud Design Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/iCloudDesignGuide/Chapters/Introduction.html#//apple_ref/doc/uid/TP40012094)*.

重要： 要在应用程序中使用iCloud存储，您需要为开发设备获取适当的 配置文件，并在Xcode项目中请求适当的权限（entitlements）。若要了解有关这些任务的详细信息，请参阅 `Tools Workflow Guide for Mac`中的 `设置系统和配置权利`。

要了解有关在应用程序中添加iCloud存储的更多信息，请阅读  *[iCloud Design Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/iCloudDesignGuide/Chapters/Introduction.html#//apple_ref/doc/uid/TP40012094)*。

***
### 3、CloudKit

CloudKit provides apps with more control over when and how data is stored in iCloud. Unlike iCloud Storage, CloudKit is a complimentary service that works with your apps existing data structures. CloudKit records include support for:

CloudKit 为应用程序提供了 对数据何时 以及 如何存储在 iCloud 中 的更多控制。与iCloud存储不同，CloudKit 是一个免费的服务，与你的应用程序现有的数据结构一起工作。CloudKit 记录包括对以下各项的支持：

- Saving, searching, and fetching data for specific to an individual user

  保存、搜索和获取特定于单个用户的数据

- Saving, searching, and fetching data in a public area shared by all users

  在所有用户共享的公共区域中保存、搜索和获取数据

CloudKit has minimal caching and relies on a network connection. To learn more about using CloudKit, see the *[CloudKit Framework Reference](https://developer.apple.com/documentation/cloudkit)*

CloudKit具有最小的缓存，并且依赖于网络连接。要了解有关使用CloudKit的更多信息，请参见 *[CloudKit Framework Reference](https://developer.apple.com/documentation/cloudkit)*。



***
### 4、File Coordination 文件协作

File coordination eliminates file-system inconsistencies due to overlapping read and write operations from competing processes. When you use the `NSDocument` class from the AppKit framework, you get file coordination with very little effort. To use file coordination explicitly, you employ the `NSFileCoordinator` class and the `NSFilePresenter` protocol, both from the Foundation framework.

文件协调 消除了由于 竞争进程 的 重叠读写操作而导致的文件系统不一致。当使用AppKit框架中的`NSDocument` 类时，只需很少的工作就可以获得文件协调。要显式地使用文件协调，可以从 Foundation 框架中使用 `NSFileCoordinator` 类和 `NSFilePresenter` 协议。



The file coordination APIs let you assert your app’s ownership of files and directories. When another process attempts access, you have a chance to respond. For example, if another app attempts to read a document that your app is editing, you have a chance to write unsaved changes to disk before the other app is allowed to do its reading.

File Coordination API 允许您断言应用程序对文件和目录的所有权。当另一个进程尝试访问时，您有机会做出响应。例如，如果另一个应用程序试图读取您的应用程序正在编辑的文档，则在允许另一个应用进行读取之前，您有机会将未保存的更改写入磁盘。



You use file coordination only with files that users conceivably might share with other users, not (for example) with files written to a cache or other temporary locations. File coordination is an enabling technology for automatic document saving, App Sandbox, and other features introduced in OS X v10.7. For more information on file coordination, see [Coordinating File Access With Other Processes](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/AppRuntime/AppRuntime.html#//apple_ref/doc/uid/TP40010543-CH2-SW16) in *[Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)*.

仅对用户可能与其他用户共享的文件使用文件协调，而不是（例如）对写入缓存或其他临时位置的文件使用文件协调。文件协调是 OSX 10.7 中引入的自动文档保存、应用程序沙盒和其他功能的一种启用技术。有关文件协调的详细信息，请参见  [Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)  中的 [Coordinating File Access With Other Processes](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/AppRuntime/AppRuntime.html#//apple_ref/doc/uid/TP40010543-CH2-SW16) 部分。



***
### 5、Bundles and Packages 

A feature integral to OS X software distribution is the bundle mechanism. Bundles encapsulate related resources in a hierarchical file structure but present those resources to the user as a single entity. Programmatic interfaces make it easy to find resources inside a bundle. These same interfaces form a significant part of the OS X internationalization strategy. 

OSX 软件分发集成的一个功能是 包（bundle） 机制。Bundle 将相关资源封装在分层文件结构中，但将这些资源作为单个实体 呈现给用户。编程接口使系统在包中查找资源变得容易。这些相同的接口构成了OSX 国际化策略的重要组成部分。



Apps and frameworks are only two examples of bundles in OS X. Plug-ins, screen savers, and preference panes are also implemented using the bundle mechanism. Developers can also use bundles for their document types to make it easier to store complex data. 

应用程序和框架 只是 OSX中包的两个示例。插件、屏幕保护程序和首选项窗格也使用包机制实现。开发人员还可以对其文档类型使用bundle，以便更容易地存储复杂的数据。



Packages are another technology, like bundles, that make distributing software easier. A package—also referred to as an *installation package*—is a directory that contains files and directories in well-defined locations. The Finder displays packages as files. Double-clicking a package launches the Installer app, which then installs the contents of the package on the user’s system. 

For an overview of bundles and to learn how they are constructed, see *[Bundle Programming Guide](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/Introduction/Introduction.html#//apple_ref/doc/uid/10000123i)*.

Packages 是另一种技术，跟 bundles 一样，它使软件的分发更加容易。package 也称为安装包（`installation package`），是一个目录，其中包含 定位良好的文件和目录。Finder 将包显示为文件。双击一个 Package 启动安装程序应用程序，然后在用户的系统上安装包的内容。
有关 bundles 的概述以及如何的信息，请参见  *[Bundle Programming Guide](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/Introduction/Introduction.html#//apple_ref/doc/uid/10000123i)*。



***
### 6、Internationalization and Localization 国际化与本土化

Localization (which is the process of adapting your app for use in another region) is necessary for success in many foreign markets. Users in other countries are much more likely to buy your software if the text and graphics reflect their own language and culture. Before you can localize an app, though, you must design it in a way that supports localization, a process called internationalization. Properly internationalizing an app makes it possible for your code to load localized content and display it correctly. 

Internationalizing an app involves the following steps:

- Use Unicode strings for storing user-visible text.
- Extract user-visible text into “strings” resource files.
- Use nib files to store window and control layouts whenever possible.
- Use international or culture-neutral icons and graphics whenever possible.
- Use Cocoa or Core Text to handle text layout.
- Support localized file-system names (also known as *display names*).
- Use formatter objects in Core Foundation and Cocoa to format numbers, currencies, dates, and times based on the current locale.

For details on how to support localized versions of your software, see *[Internationalization and Localization Guide](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPInternational/Introduction/Introduction.html#//apple_ref/doc/uid/10000171i)*. For information on Core Foundation formatters, see *[Data Formatting Guide for Core Foundation](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFDataFormatting/Articles/CFDataFormatting.html#//apple_ref/doc/uid/10000176i)*. 



***
### 7、Block Objects

Block objects, or *blocks*, are a C-level mechanism that you can use to create an ad hoc function body as an inline expression in your code. In other languages and environments, a block is sometimes called a *closure* or a *lambda*. You use blocks when you need to create a reusable segment of code but defining a function or method might be a heavyweight (and perhaps inflexible) solution. For example, blocks are a good way to implement callbacks with custom data or to perform an operation on all the items in a collection. Many OS X technologies—for example Game Kit, Core Animation, and many Cocoa classes—use blocks to implement callbacks.

The compiler provides support for blocks using the C, C++, and Objective-C languages. For more information about how to create and use blocks, see *[Blocks Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Blocks/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40007502)*.



***
### 8、Grand Central Dispatch 大中枢派发

Grand Central Dispatch (GCD) provides a simple and efficient API for achieving the concurrent execution of code in your app. Instead of providing threads, GCD provides the infrastructure for executing any task in your app asynchronously using a dispatch queue. Dispatch queues collect your tasks and work with the kernel to facilitate their execution on an underlying thread. A single dispatch queue can execute tasks serially or concurrently, and apps can have multiple dispatch queues executing tasks in parallel.



Grand Central Dispatch (GCD) 为实现应用中 代码的并发执行 提供了一个简单高效的API。GCD不提供线程，而是提供了 使用调度队列异步执行应用程序 中任何任务的基础结构。调度队列收集您的任务，并与内核一起工作，以促进它们在底层线程上的执行。单个调度队列 可以串行或并发执行任务，应用程序可以有多个调度队列并行执行任务。



There are several advantages to using dispatch queues over traditional threads. One of the most important is performance. Dispatch queues work more closely with the kernel to eliminate the normal overhead associated with creating threads. Serial dispatch queues also provide built-in synchronization for queued tasks, eliminating many of the problems normally associated with synchronization and memory contention normally encountered when using threads. 

与传统线程相比，使用调度队列有几个优点。其中最重要的是 性能（performance）。调度队列与内核更紧密地协作，以消除与创建线程相关的常用开销。串行调度队列还为队列任务提供内置同步，消除了许多通常与使用线程时遇到的同步和内存争用相关的问题。



In addition to providing dispatch queues, GCD provides three other dispatch interfaces to support the asynchronous design approach offered by dispatch queues: 

除了提供调度队列外，GCD还提供了三个其他调度接口，以支持调度队列提供的异步设计方法：



Dispatch sources provide a way to handle the following types of kernel-level events that is more efficient than BSD alternatives:

调度源提供了一种处理以下类型内核级事件的，比BSD替代方法更有效的方法：

- Timer notifications

  计时器通知

- Signal handling 

  信号处理

- Events associated with file and socket operations

  与文件和套接字操作关联的事件

- Significant process-related events

  重大过程相关事件

- Mach-related events

  Mach 相关事件

- Custom events that you define and trigger

  定义并触发的自定义事件

- Asynchronous I/O through dispatch data and dispatch I/O

  通过 调度数据和 调度I/O 实现 异步I/O

Dispatch groups allow one thread (or *task*) to block while it waits for one or more other tasks to finish executing.

调度组 允许一个线程（或任务）在 等待一个或多个其他任务完成执行时阻塞。

Dispatch semaphores provide a more efficient alternative to the traditional semaphore mechanism. 

调度信号量 为传统的信号量机制 提供了更有效的替代方案。

For more information about how to use GCD in your apps, see *[Concurrency Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/ConcurrencyProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008091)*.

关于更多在你的应用中使用 GCD 的信息，可参阅 *[Concurrency Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/ConcurrencyProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008091)*。

***
### 9、Bonjour

Bonjour is Apple’s implementation of the zero-configuration networking architecture, a powerful system for publishing and discovering services over an IP network. It is relevant to both software and hardware developers. 

Incorporating Bonjour support into your software improves the overall user experience. Rather than prompt the user for the exact name and address of a network device, you can use Bonjour to obtain a list of available devices and let the user choose from that list. For example, you could use it to look for available printing services, which would include any printers or software-based print services, such as a service to create PDF files from print jobs. 

Developers of network-based hardware devices are strongly encouraged to support Bonjour. Bonjour alleviates the need for complicated setup instructions for network-based devices such as printers, scanners, RAID servers, and wireless routers. When plugged in, these devices automatically publish the services they offer to clients on the network.

For information on how to incorporate Bonjour services into a Cocoa app, see *[Bonjour Overview](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/NetServices/Introduction.html#//apple_ref/doc/uid/10000119i)*. To incorporate Bonjour into a non-Cocoa app, see *[DNS Service Discovery Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/dns_discovery_api/Introduction.html#//apple_ref/doc/uid/TP30000964)*.



Bonjour 是零配置网络架构的 Apple 实现，一个 通过 IP 网络 发布和发现服务的 强大的系统，它与软件和硬件都相关。

将 Bonjour 支持集成到您的软件中，可以改善总体用户体验。您可以使用 Bonjour 获得可用设备的列表，并让用户从该列表中进行选择，而不是提示用户输入网络设备的确切名称和地址。例如，您可以使用它来查找可用的打印服务，其中包括任何打印机或基于软件的打印服务，例如从打印作业创建PDF文件的服务。

强烈建议 基于网络的硬件设备的开发人员支持 Bonjour。Bonjour 减轻了对基于网络的设备（如打印机、扫描仪、RAID 服务器 和 无线路由器）的复杂设置指令的需求。插入后，这些设备会自动向网络上的客户端发布它们提供的服务。

有关如何将Bonjour 服务并入 Cocoa应用程序的信息，请参见 *[Bonjour Overview](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/NetServices/Introduction.html#//apple_ref/doc/uid/10000119i)*. 要将Bonjour并入非Cocoa应用程序，请参见  *[DNS Service Discovery Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/dns_discovery_api/Introduction.html#//apple_ref/doc/uid/TP30000964)*。



***
### 10、Security Services 安全服务

OS X security is built upon several open source technologies—including BSD and Kerberos—adds its own features to those technologies. The Security framework (`Security.framework`) implements a layer of high-level services to simplify your security solutions. These high-level services provide a convenient abstraction and make it possible for Apple and third parties to implement new security features without breaking your code. They also make it possible for Apple to combine security technologies in unique ways. 

OSX 的安全 建立在几个开源技术之上，包括 BSD 和 Kerberos，它们为这些技术添加了自己的特性。Security 框架  实现一层高级服务以简化安全解决方案。这些高级服务提供了方便的抽象，使苹果和第三方能够在不破坏代码的情况下，实现新的安全功能。它们还使苹果能够以独特的方式将安全技术结合起来。



OS X provides high-level interfaces for the following features:

OSX为以下功能提供了高级接口：

- User authentication

  用户身份验证

- Certificate, Key, and Trust Services

  证书、秘钥 和 信任服务

- Authorization Services

  授权服务

- Secure Transport

  加密传输

- Keychain Services

  钥匙串服务

- Smart cards with the CryptoTokenKit framework

  CryptoTokenKit 框架的 Smart cards 

  

Security Transforms, provide a universal context for all cryptographic work. A cryptographic unit in Security Transforms, also known as a *transform*, can be used to perform tasks such as encryption, decryption, signing, verifying, digesting, and encoding. You can also create custom transforms. Transforms are built upon GCD and define a data-flow model for processing data that allows high throughput on multicore machines. 

OS X supports many network-based security standards; for a complete list of network protocols, see [Standard Network Protocols](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemTechnology/SystemTechnology.html#//apple_ref/doc/uid/TP40001067-CH207-TPXREF117). For more information about the security architecture and security-related technologies of OS X, see *[Security Overview](https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP30000976)*.

安全转换，为所有加密工作提供通用上下文。安全转换中的加密单元（也称为转换）可用于执行加密、解密、签名、验证、摘要和编码等任务。您还可以创建自定义转换。转换是建立在GCD的基础上的，定义了一个数据流模型，用于处理多核机器上允许高吞吐量的数据。





***
### 11、Maps 地图

MapKit provides a way for embedding maps into your windows and views. There is support for annotation, overlays, and reverse-geocoding lookup using coordinates. For more information, see *[Map Kit Framework Reference](https://developer.apple.com/documentation/mapkit)*

MapKit提供了一种将地图嵌入到窗口和视图中的方法。支持使用坐标进行注释、覆盖和反向地理编码查找。有关详细信息，请参见 *[Map Kit Framework Reference](https://developer.apple.com/documentation/mapkit)*

***
### 12、Address Book 通讯录

Address Book is technology that encompasses a centralized database for contact and group information, an app for viewing that information, and a programmatic interface for accessing that information in your app. The database contains information such as user names, street addresses, email addresses, phone numbers, and distribution lists. Apps that support the Address Book framework can use this data as is or extend it to include app-specific information. They can also share user records with system apps, such as Contacts and Mail. For more information about the Address Book framework, see [Address Book](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-TPXREF130).

Address Book gives users control over their contacts data by requiring your app to get permission before it can access the Address Book database. When users have enabled iCloud, Address Book keeps their data synchronized across all their devices by using the CardDAV protocol. To learn how to integrate Address Book into your app, see *[Address Book Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AddressBook/AddressBook.html#//apple_ref/doc/uid/10000117i)*.



***
### 13、Speech Technologies 语音技术

OS X contains speech technologies that recognize and speak U.S. English. 

Speech recognition is the ability for the computer to recognize and respond to a person’s speech. Using speech recognition, users can accomplish tasks comprising multiple steps with one spoken command. Because users control the computer by voice, speech-recognition technology is very important for people with special needs. You can take advantage of the speech engine and API included with OS X to incorporate speech recognition into your apps.

Speech synthesis, also called text-to-speech (TTS), converts text into audible speech. TTS provides a way to deliver information to users without forcing them to shift attention from their current task. For example, the computer could deliver messages such as “Your download is complete” and “You have email from your boss; would you like to read it now?” in the background while you work. TTS is crucial for users with vision or attention disabilities. As with speech recognition, TTS provides an API and several user interface features to help you incorporate speech synthesis into your apps. You can also use speech synthesis to replace digital audio files of spoken text. Eliminating these files can reduce the overall size of your software bundle.

For more information, see *[Speech Synthesis Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/SpeechSynthesisProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004365)* and *[NSSpeechRecognizer Class Reference](https://developer.apple.com/documentation/appkit/nsspeechrecognizer)*. 



***
### 14、Identity Services 认证服务

Identity Services encompasses features located in the Collaboration and Core Services frameworks. Identity Services provides a way to manage groups of users on a local system. In addition to standard login accounts, administrative users can now create sharing accounts, which use access control lists (ACLs) to restrict access to designated system or app resources. An access control list (ACL) gives fine-grained access to file-system objects. Sharing accounts do not have an associated home directory on the system and have much more limited privileges than traditional login accounts.

For more information about the features of Identity Services and how you use those features in your apps, see *[Identity Services Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/IdentityServices_ProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004490)* and *Identity Services Reference Collection*.



***
### 15、Time Machine Support  时间机器支持

Time Machine protects user data from accidental loss by automatically backing up data to a different hard drive. Included with this feature is a set of programmer-level functions that you can use to exclude unimportant files from the backup set. For example, you might use these functions to exclude your app’s cache files or any files that can be recreated easily. Excluding these types of files improves backup performance and reduces the amount of space required to back up the user’s system. 

For information about using the Backup Core API, see *[Backup Core Reference](https://developer.apple.com/documentation/coreservices/backup_core)*.

Time Machine 通过 自动将数据备份到不同的硬盘驱动器 来保护用户数据，以免意外丢失。此功能包括一组编程级函数，可用于从备份集中排除不重要的文件。例如，您可以使用这些函数排除应用程序的缓存文件 或 任何可以轻松重新创建的文件。排除这些类型的文件可以提高备份性能，并减少备份用户系统所需的空间。

更多关于 Backup Core API 的信息，可参阅  *[Backup Core Reference](https://developer.apple.com/documentation/coreservices/backup_core)*。

***
### 16、Keychain Services  钥匙串服务

Keychain Services provides a secure way to store passwords, keys, certificates, and other sensitive information associated with a user. Users often have to manage multiple user IDs and passwords to access various login accounts, servers, secure websites, instant messaging services, and so on. A keychain is an encrypted container that holds passwords for multiple apps and secure services. Access to the keychain is provided through a single master password. Once the keychain is unlocked, Keychain Services–aware apps can access authorized information without bothering the user.

If your app handles passwords or sensitive information, you should support Keychain Services in your app. For more information on this technology, see *Keychain Services Programming Guide*.



***
### 17、XML Parsing XML解析

OS X includes several XML parsing technologies. Most apps should use these Foundation classes: `NSXMLParser` for parsing XML streams, and the NSXML classes (for example, `NSXMLNode`) for representing XML documents internally as tree structures. Core Foundation also provides a set of functions for parsing XML content.

OSX包括几种 XML 解析技术。大多数应用程序应该使用这些基础类：`NSXMLParser` 用于解析XML流，`NSXML` 类（例如，`NSXMLNode`）用于在内部将XML文档表示为树结构。Core Foundation还提供了一组用于解析 XML 内容的函数。



The open source `libXML2` library allows your app to parse or write arbitrary XML data quickly. The headers for this library are located in the `/usr/include/libxml2` directory.

For information on parsing XML from a Cocoa app, see *[Event-Driven XML Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/XMLParsing/XMLParsing.html#//apple_ref/doc/uid/10000186i)* and *[Tree-Based XML Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/NSXML_Concepts/NSXML.html#//apple_ref/doc/uid/TP40001269)*.

开源 `libXML2` 库允许应用程序快速解析或写入任意XML数据。这个库的头位于 `/usr/include/libxml2` 目录中。

更多在 Cocoa 应用中解析 XML 的信息，可参阅 *[Event-Driven XML Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/XMLParsing/XMLParsing.html#//apple_ref/doc/uid/10000186i)* 和 *[Tree-Based XML Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/NSXML_Concepts/NSXML.html#//apple_ref/doc/uid/TP40001269)*。



***
### 18、SQLite Database 数据库

The SQLite library lets you embed a SQL database engine into your apps. Programs that link with the SQLite library can access SQL databases without running a separate RDBMS process. You can create local database files and manage the tables and records in those files. The library is designed for general purpose use but is still optimized to provide fast access to database records. 

The SQLite library is located at `/usr/lib/libsqlite3.dylib`, and the `sqlite3.h` header file is in `/usr/include`. A command-line interface (`sqlite3`) is also available for communicating with SQLite databases using scripts. For details on how to use this command-line interface, see the `sqlite3` man page. 

For more information about using SQLite, go to [SQLite Home Page](http://www.sqlite.org/). 



***
### 19、Notification Center 通知中心 

Apps can create and manage extensions in the Today view of the Notification Center. Extensions are used to give the user a summary of important pieces of information and can perform simple actions or launch the app. For more information, see *[Notification Center Framework Reference](https://developer.apple.com/documentation/notificationcenter)*

应用程序可以在通知中心的“今日”视图中创建和管理扩展。扩展用于向用户提供重要信息的摘要，并可以执行简单操作或启动应用程序。有关详细信息，请参见 *[Notification Center Framework Reference](https://developer.apple.com/documentation/notificationcenter)*。

***
### 20、Distributed Notifications 通知分发

A distributed notification is a message posted by any process to a per-computer notification center, which in turn broadcasts the message to any processes interested in receiving it. Included with the notification is the ID of the sender and an optional dictionary containing additional information. The distributed notification mechanism is implemented by the Core Foundation `CFNotificationCenter` object and by the Cocoa `NSDistributedNotificationCenter` class.

Distributed notifications are ideal for simple notification-type events. For example, a notification might communicate the status of a certain piece of hardware, such as the network interface. Notifications should not be used to communicate critical information to a specific process because delivery of a notification to every registered received is not guaranteed. 

Distributed notifications are true notifications because there is no opportunity for the receiver to reply to them. There is also no way to restrict the set of processes that receive a distributed notification. Any process that registers for a given notification may receive it. Because distributed notifications use a string for the unique registration key, there is a potential for namespace conflicts.

For information on Core Foundation support for distributed notifications, see *[CFNotificationCenter Reference](https://developer.apple.com/documentation/corefoundation/cfnotificationcenter)*. For information about Cocoa support for distributed notifications, see *[Notification Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Notifications/Introduction/introNotifications.html#//apple_ref/doc/uid/10000043i)*.



***
## 三、Core Service Frameworks

OS X includes several core services that make developing apps easier. These technologies range from utilities for managing your internal data structures to high-level frameworks for speech recognition and accessing calendar data. This section summarizes the technologies in the Core Services layer that are relevant to developers—that is, that have programmatic interfaces or have an impact on how you write software. 



***
### 1、Core Services Umbrella Framework

The Core Services umbrella framework (`CoreServices.framework`) includes the following frameworks:

- **Launch Services** (`LaunchServices.framework`). Launch Services gives you a programmatic way to open apps, documents, URLs, or files with a given MIME type in a way similar to the Finder or the Dock. The Launch Services framework also provides interfaces for programmatically registering the document types your app supports. Launch Services is in the Core Services umbrella framework. For information on how to use Launch Services, see *[Launch Services Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/LaunchServicesConcepts/LSCIntro/LSCIntro.html#//apple_ref/doc/uid/TP30000999)*. 
- **Metadata** (`Metadata.framework`). The Metadata framework helps you to create Spotlight importer plug-ins. It also provides a query API that you can use in your app to search for files based on metadata values and then sort the results based on certain criteria. (The Foundation framework offers an Objective-C interface to the query API.) For more information on Spotlight importers, querying Spotlight, and the Metadata framework, see *[Spotlight Importer Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/MDImporters/MDImporters.html#//apple_ref/doc/uid/TP40001267)* and *[File Metadata Search Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/SpotlightQuery/Concepts/Introduction.html#//apple_ref/doc/uid/TP40001841)*.
- **Search Kit** (`SearchKit.framework`). Search Kit lets you search, summarize, and retrieve documents written in most human languages. You can incorporate these capabilities into your app to support fast searching of content managed by your app. This framework is part of the Core Services umbrella framework. For detailed information about the available features, see *[Search Kit Reference](https://developer.apple.com/documentation/coreservices/search_kit)*. 
- **Web Services Core** (`WebServicesCore.framework`). Web Services Core provides support for the invocation of web services using CFNetwork. The available services cover a wide range of information and include things such as financial data and movie listings. Web Services Core is part of the Core Services umbrella framework. For a description of web services and information on how to use the Web Services Core framework, see *[Web Services Core Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/UsingWebservices/Introduction/Introduction.html#//apple_ref/doc/uid/TP30000985)*. 
- **Dictionary Services** (`DictionaryServices.framework`). Dictionary Services lets you create custom dictionaries that users can access through the Dictionary app. Through these services, your app can also access dictionaries programmatically and can support user access to dictionary look-up through a contextual menu. For more information, see *[Dictionary Services Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/DictionaryServicesProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40006152)*.

You should not link directly to any of these subframeworks; instead link to (and import) `CoreServices.framework`.



***
### 2、Accounts

The Accounts framework (`Accounts.framework`) provides a single sign-on model for supported account types such as Twitter and Facebook. Single sign-on improves the user experience because it prevents your app from having to prompt a user separately for login information related to an account. It also simplifies the development model for you by managing the account authorization process for your app. 

Accounts框架（Accounts.framework）为受支持的帐户类型（如Twitter和Facebook）提供了单点登录模型。单点登录提高了用户体验，因为它可以防止应用程序必须单独提示用户有关帐户的登录信息。它还通过管理应用程序的帐户授权过程，为您简化了开发模型。



***
### 3、Address Book 通讯录

The Address Book framework (`AddressBook.framework`) uses a centralized database to store the user’s contacts and other personal information. With the user’s permission, your app can use the Address Book to access Exchange and CardDAV contacts and allow users to display and edit contacts in a standardized user interface. 

地址簿框架（Address Book.framework）使用一个集中的数据库来 存储用户的联系人和其他个人信息。如果用户允许，您的应用程序可以使用通讯簿访问 Exchange 和 CardDAV 联系人，并允许用户在标准用户界面中显示和编辑联系人。



**Note:** Apps that target OS X 10.11 and later should use the Contacts framework instead of the Address Book framework.

注意：针对OSX10.11 及更高版本的应用程序应该使用联系人框架（`Contacts`），而不是地址簿框架。



The Address Book framework supports yearless dates and several instant-messaging services, in addition to the creation of custom plug-ins. For more information about using the Address Book APIs, see either *[Address Book Objective-C Framework Reference for Mac](https://developer.apple.com/documentation/addressbook)* or *Address Book C Framework Reference for Mac*.

除了创建自定义插件外，通讯录框架还支持 无年份日期和多个即时消息服务。有关使用通讯簿API的更多信息，请参见  [Address Book Objective-C Framework Reference for Mac](https://developer.apple.com/documentation/addressbook)* 或 *Address Book C Framework Reference for Mac*。



***

### 4、Automator

The Automator framework (`Automator.framework`) enables your app to run workflows. Workflows string together the actions defined by various apps to perform complex tasks automatically. Unlike AppleScript, which uses a scripting language to implement the same behavior, workflows are constructed visually, requiring no coding or scripting skills to create.

For information about incorporating workflows into your own apps, see *[Automator Framework Reference](https://developer.apple.com/documentation/automator)*. 

Automator 框架（Automator.framework）使您的应用程序能够运行工作流。工作流将各种应用程序定义的操作 串在一起，以自动执行复杂的任务。与 AppleScript 不同，AppleScript 使用脚本语言实现相同的行为，工作流是可视化构建的，不需要编写代码或脚本来创建。
有关将工作流合并到您自己的应用程序中的信息，请参见  *[Automator Framework Reference](https://developer.apple.com/documentation/automator)*. 



***
### 5、Core Data

The Core Data framework (`CoreData.framework`) manages the data model of an app in terms of the Model-View-Controller design pattern. Instead of defining data structures programmatically, you use the graphical tools in Xcode to build a schema representing your data model. At runtime, entities are created, managed, and made available through the Core Data framework with little or no coding on your part.

Core Data provides the following features:

- Storage of object data in mediums ranging from an XML file to a SQLite database
- Management of undo/redo operations beyond basic text editing
- Support for validation of property values
- Support for propagating changes and ensuring that the relationships between objects remain consistent
- Grouping, filtering, and organizing data in memory and transferring those changes to the user interface through Cocoa bindings

Core Data also includes incremental storage, a work concurrency model, and nested managed object contexts.

- Using the incremental store classes (`NSIncrementalStore` and `NSIncrementalStoreNode`), you can create Core Data stores that connect to any possible data source.
- The work concurrency model API enables your app to share unsaved changes between threads across the object graph efficiently.
- You can create nested managed object contexts, in which fetch and save operations are mediated by the parent context instead of a coordinator. This pattern has a number of usage scenarios, including performing background operations on a second thread or queue and managing discardable edits, such as in an inspector window or view.

For more information, see *[Core Data Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CoreData/index.html#//apple_ref/doc/uid/TP40001075)*. 



***

### 6、Event Kit

Event Kit (`EventKit.framework`) provides an interface for accessing a user’s calendar events and reminder items. You can use the APIs in this framework to get existing events and to add new events to the user’s calendar. Events that are created using Event Kit are automatically propagated to the CalDAV or Exchange calendars on other devices, which allows your app to display up-to-date calendar information without requiring users to open the Calendar app. (Calendar events can include configurable alarms with rules for when they should be delivered.)

You can also use Event Kit APIs to access reminder lists, create new reminders, add an alarm to a reminder, set the due date and start date of a reminder, and mark a reminder as complete. To learn more about the Event Kit APIs, see *[Event Kit Framework Reference](https://developer.apple.com/documentation/eventkit)*.



***
### 7、Foundation and Core Foundation

The Foundation and Core Foundation frameworks are essential to most types of software developed for OS X. The basic goals of both frameworks are the same: 

- Define basic object behavior and introduce consistent conventions for object mutability, object archiving, notifications, and similar behaviors.
- Define basic object types representing strings, numbers, dates, data, collections, and so on.
- Support internationalization with bundle technology and Unicode strings.
- Support object persistence.
- Provide utility classes that access and abstract system entities and services at lower layers of the system, including ports, threads, processes, run loops, file systems, and pipes. 

The difference between Foundation (`Foundation.framework`) and Core Foundation (`CoreFoundation.framework`) is the language environment in which they are used. Foundation is an Objective-C framework and is intended to be used with all other Objective-C frameworks that declare methods taking Foundation class types as parameters or with return values that are Foundation class types. Along with the AppKit and Core Data frameworks, Foundation is considered to be a core framework for app development (see [Cocoa Umbrella Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CocoaApplicationLayer/CocoaApplicationLayer.html#//apple_ref/doc/uid/TP40001067-CH274-SW2)). Core Foundation, on the other hand, declares C-based programmatic interfaces; it is intended to be used with other C-based frameworks, such as Core Graphics. 



**Note:** Although you can use Core Foundation objects and call Core Foundation functions in Swift or Objective-C projects, there is rarely a reason for doing so.



In its implementation, Foundation is based on Core Foundation. And, although it is C based, the design of the Core Foundation interfaces are more object-oriented than C. As a result, the opaque types (often referred to as *objects*) you create with Core Foundation interfaces operate seamlessly with the Foundation interfaces. Specifically, most equivalent Foundation classes and Core Foundation opaque types are toll-free bridged; this means that you can convert between object types through simple typecasting.

Foundation and Core Foundation provide basic data types and data management features, including the following:

- Collections
- Bundles and plug-ins
- Strings
- Raw data blocks
- Dates and times
- Preferences
- Streams
- URLs
- XML data
- Locale information
- Run loops
- Ports and sockets
- Notification Center interaction
- Interprocess communication between apps using XPC



For an overview of Foundation, read the introduction to *[Foundation Framework Reference](https://developer.apple.com/documentation/foundation)*. For an overview of Core Foundation, read *[Core Foundation Design Concepts](https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFDesignConcepts/CFDesignConcepts.html#//apple_ref/doc/uid/10000122i)*.



***
### 8、Quick Look 快速预览

Quick Look enables apps such as Spotlight and the Finder to display thumbnail images and full-size previews of documents. If your app defines custom document formats that are different from the system-supported content types, you should provide a Quick Look generator for those formats. (Generators are plug-ins that convert documents of the appropriate type from their native format to a format that Quick Look can display as thumbnails and previews to users.) Quick Look also allows users of your app to preview the contents of a document that’s embedded as a text attachment without requiring them to leave the app. 

For information about supporting Quick Look for your custom document types, see *[Quick Look Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/Quicklook_Programming_Guide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005020)* and *Quick Look Framework Reference for Mac*. The related Quick Look UI framework is briefly described in [Quick Look UI](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW31).



QuickLook 使 Spotlight 和 Finder 等应用程序能够显示缩略图和文档的全尺寸预览。如果应用程序定义的自定义文档格式 不同于 系统支持的内容类型，则应为这些格式提供快速查找生成器（Quick Look generator）。（生成器是将适当类型的文档从其原来的格式 转换为 Quick Look 可以显示为缩略图并向用户预览的格式的插件。）Quick Look还允许应用程序的用户 预览嵌入为文本附件的文档的内容，而无需离开应用程序。

有关支持 自定义文档类型 Quick Look 的信息，可参见 [Quick Look Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/Quicklook_Programming_Guide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005020) 和 *Quick Look Framework Reference for Mac*.  Quick Look UI 框架的相关描述在 文章下面部分 有简要说明。



***
### 9、Social Framework

The Social framework (`Social.framework`) helps you integrate supported social networking services into your app by providing a template for creating HTTP requests and a generalized interface for posting requests on the user’s behalf. You can also use the Social framework to retrieve information for integrating a user’s social networking accounts into your app. 

To learn more about the Social API, see *[Social Framework Reference](https://developer.apple.com/documentation/social)*.

社交框架（Social.framework）通过提供 用于创建HTTP请求的模板 和 用于代表用户发布请求的通用接口，帮助您将受支持的社交网络服务集成到应用程序中。您还可以使用社交框架检索信息，以便将用户的社交网络帐户集成到您的应用程序中。
要了解有关社交API的更多信息，请参见 *[Social Framework Reference](https://developer.apple.com/documentation/social)*。

***
### 10、Store Kit 

Store Kit (`StoreKit.framework`) enables you to request payment from a user to purchase additional app functionality or content from the Mac App Store. 

Store Kit (`StoreKit.framework`) 允许你向用户请求付款，以从 Mac应用商店购买其他应用程序功能或内容。

Store Kit handles the financial aspects of a transaction, processing the payment request through the user’s iTunes Store account. Store Kit then provides your app with information about the purchase. Your app handles the other aspects of the transaction, including the presentation of a purchasing interface and the downloading (or unlocking) of the appropriate content. This division of labor gives you control over the user experience. You also decide on the delivery mechanism that works best for your app.

For more information about Store Kit, read *[In-App Purchase Programming Guide](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/StoreKitGuide/Introduction.html#//apple_ref/doc/uid/TP40008267)* and *[Store Kit Framework Reference](https://developer.apple.com/documentation/storekit)*.

Store Kit 处理交易的财务方面，通过用户的iTunes商店帐户处理付款请求。然后， Store Kit  将为你的应用程序提供有关购买的信息。你的应用程序处理交易的其他方面，包括展示购买界面和下载（或解锁）适当的内容。这种分工让您可以控制用户体验。您还可以决定最适合您的应用程序的传递机制。



***
### 11、WebKit

The WebKit framework (`WebKit.framework`) enables your app to display HTML content. It has two subframeworks: Web Core and JavaScript Core. Web Core is for parsing and displaying HTML content; JavaScript Core is for parsing and executing JavaScript code. 

WebKit 框架可以让你的应用展示 HTML 内容，它有两个子框架：Web Core 和 JavaScript Core。Web Core 用来解析和显示 HTML 内容； JavaScript Core 用来解析和执行 JavaScript 代码。

WebKit also lets you create text views containing editable HTML. With this basic editing support, users can replace text and manipulate the document text and attributes, including CSS properties. WebKit also supports creating and editing content at the DOM level of an HTML document. For example, you could extract the list of links on a page, modify them, and replace them prior to displaying the document in a web view.

For information on how to use WebKit, see *[WebKit Objective-C Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DisplayWebContent/DisplayWebContent.html#//apple_ref/doc/uid/10000164i)*.

WebKit还允许你创建 包含 可编辑 HTML的 文本视图。有了这个基本的编辑支持，用户可以 替换文本 并操作文档文本和属性，包括CSS属性。WebKit 还支持在 HTML文档的 DOM 级别 创建 和编辑内容。例如，在web 视图中显示文档之前，可以提取页面上的链接列表，对其进行修改和替换。

有关如何使用 WebKit的信息，请参见 *[WebKit Objective-C Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DisplayWebContent/DisplayWebContent.html#//apple_ref/doc/uid/10000164i)*。



***
### 12、Other Frameworks in the Core Services Layer 其它框架

The Core Services layer of OS X also includes the following frameworks:

- **Collaboration** (`Collaboration.framework`). The Collaboration framework provides a set of Objective-C classes for displaying sharing account information and other identity-related user interfaces. With this API, apps can display information about users and groups and display a panel for selecting users and groups during the editing of access control lists. For related information, see [Identity Services](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW1).

  协作框架 (`Collaboration.framework`) 提供了一组Objective-C类，用于显示共享帐户信息 和 其他与身份相关的用户界面。使用此API，应用程序可以显示有关用户和组的信息，并显示一个面板，用于在 编辑访问控制列表期间 选择用户和组。有关信息，请参见 [Identity Services](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW1)。



- **Input Method Kit** (`InputMethodKit.framework`). Input Method Kit helps you build input methods for Chinese, Japanese, and other languages. The framework handles tasks such as connecting to clients and running candidate windows. To learn more, see *[Input Method Kit Framework Reference](https://developer.apple.com/documentation/inputmethodkit)*.

  输入法工具包 帮助你为中文、日语和其他语言构建输入方法。该框架处理连接到客户端和运行候选窗口等任务。要了解更多信息，请参见  *[Input Method Kit Framework Reference](https://developer.apple.com/documentation/inputmethodkit)*。

  

- **Latent Semantic Mapping** (`LatentSemanticMapping.framework`). Latent Semantic Mapping supports the classification of text and other token-based content into developer-defined categories, based on semantic information latent in the text. Products of this technology are maps, which you can use to analyze and classify arbitrary text—for example, to determine, if an email message is consistent with the user’s interests. For information about the Latent Semantic Mapping framework, see *[Latent Semantic Mapping Reference](https://developer.apple.com/documentation/latentsemanticmapping)*.

  潜在语义映射框架 (`LatentSemanticMapping.framework`)  支持根据文本中潜在的语义信息，将文本 和 其他基于令牌的内容分类 为开发人员定义的类别。这项技术的产品是映射，你可以用它来分析和分类任意文本；例如，确定一封电子邮件是否符合用户的兴趣。有关潜在语义映射框架的信息，请参见  *[Latent Semantic Mapping Reference](https://developer.apple.com/documentation/latentsemanticmapping)*。 







