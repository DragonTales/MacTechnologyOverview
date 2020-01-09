# 【Mac Technology Overview】（二） Creating Software Products for the Mac Platform 

[toc]

***
原文地址：
[https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF101](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF101)
***

Apps are the most common type of Mac software, but there are many other types of software that you can create, too. The following sections introduce the range of software products you can create for the Mac platform and suggest when you might consider doing so. 

Mac 软件常见的类型为 应用（Apps）, 同时你也可以创建其它类型的软件。下面的部分将向你介绍你可以在 Mac 平台上开发的软件类型范围，和你考虑做这些产品时的建议。



## 一、Apps 应用

Apps are by far the predominant type of software created for Mac, or for any platform. You use Cocoa to build new Mac apps. To learn more about the features and frameworks available in Cocoa, see [Cocoa Application Layer](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CocoaApplicationLayer/CocoaApplicationLayer.html#//apple_ref/doc/uid/TP40001067-CH274-SW1).

Apps 时目前 Mac 上，也可以说是所有平台上的主要软件类型。你可以使用 Cocoa 来创建新的 Mac 应用。去学习更多 Cocoa中的特性和可用框架，可以查看 [Cocoa Application Layer](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CocoaApplicationLayer/CocoaApplicationLayer.html#//apple_ref/doc/uid/TP40001067-CH274-SW1).（译：）



In general, there are three basic styles of Mac apps:

一般而言，有三种基本类型的 Mac 应用：

- **The single-window utility app.** A single-window utility app helps users perform the primary task within one window. Although a single-window utility app might also open an additional window—such as a preferences window—the user remains focused on the main window. Calculator is an example of a single-window utility app.

  单窗口工具应用：一个单窗口工具应用帮助用户在一个窗口内，实现主要的操作。虽然单窗口应用可能会开启一个附加的窗口，比如偏好设置窗口，但用户还是把注意力放在主窗口上。计算器是这种类型应用的一个例子。

  

- **The single-window “shoebox” app.** The defining characteristic of a shoebox app is the way it gives users an app-specific view of their content. For example, iPhoto users don’t find or organize their photos in the Finder; instead, they manage their photo collections entirely within the app.

  单窗口“鞋盒”应用：shoebox 应用程序的定义特诊是，它向用户提供 应用内容的特定试图。比如，iPhone 用户不会再他们的 Finder 应用中查找或整理照片；而是完全通过 iPhoto 应用来管理照片集合。

   

- **The multiwindow document-based app.** A multiwindow document-based app, such as Pages, opens a new window for each document the user creates or views. This style of app does not need a main window (although it might open a preferences or other auxiliary window).

  多窗口的基于文档的应用：一个多窗口基于文档的应用，比如 Pages，会为用户创建或浏览的每一个文稿打开一个新窗口。这种类型的应用不需要一个主窗口（虽然它可能会打开偏好设置，或者其他辅助窗口）。





***

### 1、App Extensions 应用拓展

No matter what type of app you write, you use app extensions to extend the functionality and content of that app to other parts of the system, or even to other apps. Types of extensions include:

无论你编写哪种类型的应用，你可以使用 应用拓展来将 功能 和 内容 拓展到系统的其他部分，甚至其他应用。拓展的类型包含：



- **Today.** Display information from your app, or perform a quick task in the Today view of Notification Center.

  今天：展示你的 App 的内容，或者在 通知中心 的`今天` 试图中展示一个快捷任务。

  

- **Share.** Share information with others by posting information to a website or social service, or sending data out in some other way.

  分享：通过发送内容给网站或社交服务、或其它发送数据的方式来分享信息。

  

- **Action.** Create a context allowing the user to manipulate or view items from your app inside another app.

  创建一个会画， 允许用户在其它应用中操作或查看其你应用中的内容。

  

- **Finder.** Show the sync state information in Finder.

  展示Finder 中的同步状态信息。



### 2、App Store 苹果商店应用

Regardless of the app style you choose, your goal is probably to get your app into the Mac App Store. The development process that helps you achieve this goal includes a mix of coding and administrative tasks.

This document gives you an overview of Mac technologies that you can incorporate into your app. To learn more about the other tasks involved in the development process, read *App Distribution Quick Start*.

无论你选择哪种应用风格，目标都可能是将应用上架 Mac App Store。帮助你实现这一目标的开发过程包含代码和管理任务的混合。

这份文档给你展示可以在应用中采用的 Mac 技术。要了解有关开发过程中涉及的其他任务的更多信息，可以阅读  *App Distribution Quick Start*。



***

## 二、Development Languages 开发语言

The tools for OS X supports many different development languages. In addition to Swift, Objective-C, C++, C, and other such languages, Xcode provides support for many scripting languages. For more information, see [Scripts](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF120) below.

The most common languages used for development for OS X are Swift and Objective-C. The following sections call out key features in some of these environments. 

OSX 的工具支持许多不同的开发语言，在 Swift,  Objective-C, C++, C 之外，Xcode 提供很多脚本语言的支持，更多信息可以看下面的 脚本 部分。



***

### 1、Swift

Swift is a new programming language for Cocoa and Cocoa Touch with a concise and expressive syntax. Swift incorporates research on programming language combined with decades of experience building Apple platforms. Code written in Swift co-exists with existing classes written in Objective-C, allowing for easy adoption.

Swift 是用于  Cocoa 和 Cocoa Touch  的新型编程语言，拥有间接的富于表现力的语法。Swift 对变成语言的研究，结合了 Apple 数十年的平台架构经验。Swift 编写的代码可以和已存在的 OC 语言兼容，从而易于采用。



Some of the key features of Swift are:

Swift 的主要特性如下：



- Closures unified with function pointers

  与函数指针统一的闭包

- First class functions

  一流的功能

- Tuples and multiple return values

  元祖和多数据返回

- Generics

  泛型

- Fast and concise iteration over a range or collection

  在范围或集合上进行 快速和简洁的迭代

- Structs and Enums that support methods, extensions, and protocols

  支持方法，扩展和协议的结构和枚举

- Functional programming patterns

  功能编程模式

- Type safety and type inference with restricted access to direct pointers

  类型安全和类型推断，对直接指针的访问受到限制

  

Swift also supports the use of Playgrounds, an interactive environment for real time evaluation of code. Use playgrounds for designing a new algorithm, creating and verifying new tests, or learning about the language and APIs.

Swift 同样支持 Playgrounds 的使用，Playgrounds 是实时评估代码的交互环境。使用 Playgrounds 来设计一个新的算法，创建和验证新的测试，或者学习语言 APIs。

To learn more about Swift, see *The Swift Programming Language*, or for a quick overview, see *Welcome to Swift*.



***

### 2、Objective-C

Objective-C is a C-based programming language with object-oriented extensions. It is a primary development language for Cocoa apps. Unlike C++ and some other object-oriented languages, Objective-C comes with its own dynamic runtime environment. This runtime environment makes it much easier to extend the behavior of code at runtime without having access to the original source. 

Objective-C 是基于C语言的面向对象扩展的编程语言。它是 Cocoa 应用开发的主要语言。不同于 C++ 和其它对象对象的语言，Objective-C 有独有的动态运行时环境。这个运行时环境，让它更容易去无需访问原始源的情况下，在运行时拓展代码的行为。



Objective-C 2.0 supports the following features, among many others:

Objective-C 比起同类型语言，支持一下特性：

- Blocks (which are described in [Block Objects](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW10))

- Declared properties, which offer a simple way to declare and implement an object’s accessor methods

  申明的属性，可以提供一个简单的方法去申明和实现一个对象的访问器方法

- A `for` operator syntax for performing fast enumerations of collections

  `for` 操作符，支持集合的快速遍历。

- Formal and informal protocols, which allow you to declare methods that are independent of any specific class, but which any class might implement

  正式和非正式的协议，允许你声明独立于任何特定类，但任何类都可以实现的方法。

- Categories and extensions, both of which allow you to add methods to an existing class

  分类和扩展，都支持你对现有类添加方法。

To learn about the Objective-C language, see *[The Objective-C Programming Language](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ObjectiveC/Introduction/introObjectiveC.html#//apple_ref/doc/uid/TP30001163)*. 





## 三、Other Types of Software 其它软件类型

There are many other types of software you can develop for Mac. Most of these software products have no user interface (UI) and instead provide services that extend the capabilities of other software, such as third-party apps or the system itself.

你可以在 Mac 上开发很多其它类型的软件。这些软件产品大多没有用户交互（UI），提供服务来拓展其它软件（比如第三方软件，或系统本身）的功能。



### 1、Frameworks 框架

A framework is a special type of bundle used to distribute shared resources, including library code, resource files, header files, and reference documentation. Frameworks offer a more flexible way to distribute shared code—for example, image files and localized strings—that you might otherwise put into a dynamic shared library. Frameworks also have a version control mechanism that makes it possible to distribute multiple versions of a framework in the same framework bundle.

框架（framework） 是一种特定类型的包（bundle），用来分发共享的资源，包含 库代码、资源文件、头文件 和参考文档。框架提供了一种个灵活而方式来分发共享的代码，比如，图片文件和本地化字符串，你可以放进动态共享库中。框架同时拥有版本控制机制，来让在同一个框架包中 分发多版本框架成为可能。



Apple uses frameworks to distribute the public interfaces of OS X (and iOS), which are packaged in software development kits. A software development kit (SDK) collects the frameworks, header files, tools, and other resources necessary for developing software targeted at a specific version of a platform. You, too, can use frameworks to distribute public code and interfaces that you create, or to develop private shared libraries to embed in your apps.

苹果使用框架来分发 OSX(和 iOS)的公共接口，打包在 SDK 中。一个 SDK集合了框架，头文件，工具还有其他软件在特定版本系统上开发所需要的资源。你也可以使用框架来分发你开发的公共代码和接口，或者开发嵌入到你应用中的私有共享库。



**Note:** Although OS X also supports the concept of an “umbrella” framework, which encapsulates multiple subframeworks in a single package, this mechanism is used primarily for the distribution of Apple software. The creation of umbrella frameworks by third-party developers is not recommended.

备注：虽然 OSX 也支持 伞式框架（封装多个子框架在一个包中），这个机制主要用于 Apple 软件的发布。不建议第三发开发者创建伞式框架。



You can use any programming language to create your own frameworks, but it’s best to choose a language that makes it easy to update the framework later. Apple frameworks generally export programmatic interfaces in ANSI C, Swift, or Objective-C. Both of these languages have a well-defined export structure that makes it easy to maintain compatibility between different revisions of the framework. 

你可以使用任意语言来开发自己的框架，但最好选择一门后续能更方便更新框架的预压。Apple框架通常以ANSI C，Swift或Objective-C 导出编程接口。 这些语言都有一个定义明确的导出结构，可以轻松维护不同版本框架之间的兼容性。



To learn about the structure and composition of frameworks, see *[Framework Programming Guide](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPFrameworks/Frameworks.html#//apple_ref/doc/uid/10000183i)*. That document also describes how to use Xcode to create public and private frameworks.

学习更多框架的结构和组成，可以查看 *[Framework Programming Guide](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPFrameworks/Frameworks.html#//apple_ref/doc/uid/10000183i)*。这份文档同样介绍了如何使用 Xcode 来创建公有和私有框架。



***

### 2、Plug-ins 插件

Plug-ins are the standard way to extend many apps and system behaviors. A plug-in is a bundle whose code is loaded dynamically into the runtime of an app. Because it’s loaded dynamically, a plug-in can be added and removed by the user. 

插件是拓展应用和系统功能的标准方式。一个插件是一个包（bundle）, 这个包的代码会动态装载进 app 的运行时。因为它是动态装载的，插件可以被用户添加或移除。



The app and system plug-ins listed below represent some of the many opportunities for developing plug-ins.

下列应用和系统插件代表了很多开发插件的方式：

***
#### 1）Address Book action plug-ins. 

An Address Book plug-in lets you add custom actions that act on the data in a person’s Address Book card. For example, the existing Large Type action displays the selected phone number in large type. Each action plug-in performs a single action, which can open a simple window within the Address Book app. If an action needs to do anything else, it must launch your app to perform the action. To learn how to create an Address Book action plug-in, see [Creating and Using Address Book Action Plug-ins](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AddressBook/Tasks/Actions.html#//apple_ref/doc/uid/20001681). 

通讯录操作插件：一个通讯录插件可以帮你对用户通讯录数据 添加自定义的操作。比如，现有的“大字体”操作将以大字体显示所选电话号码。每个操作插件都执行一个动作，可以在“通讯簿”应用中打开一个简单的窗口。如果一个操作需要做其他事，必须登陆你的应用去执行操作。学习更多通讯录操作插件，可以查看 [Creating and Using Address Book Action Plug-ins](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AddressBook/Tasks/Actions.html#//apple_ref/doc/uid/20001681)。



***
#### 2）App plug-ins.
An app plug-in can extend the features of any app that supports a plug-in model. In addition to third-party apps, several Apple apps also support plug-ins, such as iTunes, Final Cut Pro, and Aperture. For information about developing plug-ins for Apple apps, visit the [Apple Developer](http://developer.apple.com/) website. 

一个应用查看可以拓展任意支持插件模型的应用的功能。除了第三方应用，一些苹果的应用也支持插件，比如  iTunes, Final Cut Pro, 和 Aperture。更多Apple 应用插件开发信息，可以访问  [Apple Developer](http://developer.apple.com/)  来查看。



***
#### 3）Automator plug-ins. 自动操作插件
Using an Automator plug-in, you can expand the default set of actions available in Automator, a utility app that lets users assemble complex scripts using a palette of predefined actions. Automator plug-ins can be written in AppleScript or Objective-C, so you can write them for your own app’s features or for the features of other scriptable apps. (It’s a good idea to provide Automator plug-ins for your app’s most common tasks because doing so gives users more ways to interact with your app.) To learn how to write an Automator plug-in, see *[Automator Programming Guide](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/AutomatorConcepts/Automator.html#//apple_ref/doc/uid/TP40001450)*. 

使用 Automator 插件，你可以拓展 Automator 的默认操作组，Automator 是一个可以让用户使用 预设值的动作来 组装复杂脚本的工具。Automator 插件可以使用 OC 或 AppleScript 编写，你也可以为自己应用的特性编写，也可以给其它支持脚本的应用编写。（让自己的应用的常用功能提供 Automator 插件是个好想法，因为这样可以给用户更多方式去与你的应用交互）。学习更多 Automator 插件，可以查看  *[Automator Programming Guide](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/AutomatorConcepts/Automator.html#//apple_ref/doc/uid/TP40001450)*。



> 译者注：Automator 是 `自动操作` 这款应用



***
#### 4）Core Audio plug-ins. 核心音频插件
A Core Audio plug-in can support the manipulation of audio streams during most processing stages. For example, you can use plug-ins to generate, process, or receive an audio stream or to interact with new types of audio-related hardware devices. To begin learning about Core Audio, read *[Core Audio Overview](https://developer.apple.com/library/archive/documentation/MusicAudio/Conceptual/CoreAudioOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003577)*.

一个核心音频插件可以在大部分处理阶段支持对音频流的处理。比如，你可以使用插件去产生、处理或者接受音频流，或者去和音频相关硬件设备的交互。学习核心音频，可以阅读： *[Core Audio Overview](https://developer.apple.com/library/archive/documentation/MusicAudio/Conceptual/CoreAudioOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003577)*.



***
#### 5）Image units. 图像单元
An image unit is a type of plug-in that you can use with the Core Image and Core Video technologies. An image unit consists of a collection of filters—each of which implements a specific manipulation for image data—packaged together in a single bundle. For example, you could write a set of filters that perform different kinds of edge detection and package them as one image unit. To learn how to create an image unit, see [Creating Custom Filters](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreImaging/ci_custom_filters/ci_custom_filters.html#//apple_ref/doc/uid/TP30001185-CH6). 

一个图像单元是插件的一种，你可以通过 Core Image 和 Core Video 技术使用。一个图像单元由一组滤镜组成，每一个都为图像数据执行一组特定的操作，打包进一个单独的包。比如，你可以写一组滤镜，执行各种边缘检测并将其打包为一个图像单元。学习更多的图片单元，可以查看  [Creating Custom Filters](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreImaging/ci_custom_filters/ci_custom_filters.html#//apple_ref/doc/uid/TP30001185-CH6). 





***
#### 6）Input methods. 输入法
A common example of an input method is an interface for typing Japanese or Chinese characters using multiple keystrokes. Other examples of input methods include spelling checkers and pen-based gesture recognition systems. You can create input methods using Input Method Kit (`InputMethodKit.framework`). For information on how to use this framework, see *[Input Method Kit Framework Reference](https://developer.apple.com/documentation/inputmethodkit)*. 

一个输入法的常见例子是 使用多种键盘 输入日文或中文字符的接口。其它例子是，输入检查和基于笔触的识别系统。你可以使用 Input Method Kit (`InputMethodKit.framework`) 创建输入法。更多信息可见  *[Input Method Kit Framework Reference](https://developer.apple.com/documentation/inputmethodkit)*。



***
#### 7）Metadata importers. 元数据导入器
Spotlight relies on metadata importers to gather information about the user’s files and to build a systemwide index. Spotlight uses this index to help users find information by searching on attributes that make sense to them, such as the duration of a video or the dimensions of an image. If your app defines a custom file format, you should always provide a metadata importer for that file format. (If your app relies on commonly used file formats, such as JPEG, RTF, or PDF, the system provides a metadata importer for you.) To learn how to create metadata importers, see *[Spotlight Importer Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/MDImporters/MDImporters.html#//apple_ref/doc/uid/TP40001267)*. 

聚焦（Spotlight） 依赖于源输入导入七来采集用户文件信息来创建一个系统级别的缩影。聚焦使用这个缩影来帮助用户通过搜索属性来 查找信息，比如视频的长度或图片的尺寸。如果你的应用定义了一个自定义的文件格式，你需要一直为这个格式提供一个元数据导入器。（如果你的应用依赖于常见的用户文件格式，比如  JPEG, RTF, 或 PDF，使用系统的元数据导入器即可）。



***
#### 8）Quartz Composer plug-ins. 
Quartz Composer supports a plug-in mechanism that allows you to create a custom patch and make it available in the Quartz Composer workspace and to most Quartz Composer clients. (A *patch* is processing unit that performs a specific task, such as processing a string or rendering an OpenGL texture.) To learn how to create a Quartz Composer plug-in, see *[Quartz Composer Custom Patch Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/QuartzComposer_Patch_PlugIn_ProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004787)*.

Quartz Composer 支持一个插件机制，允许你创建自定义的不定，在 Quartz Composer 工作栈中和多数 Quartz Composer  客户端中可用。不定是执行特定任务的处理单元，比如 处理字符串或渲染 OpenGL 纹理。



***
#### 9）Quick Look plug-ins. 快速查看插件
A Quick Look plug-in—also known as a Quick Look generator—converts a document from its native format into a format that Quick Look can display to users. If your app creates documents of a nonstandard or private type, it’s a good idea to provide a Quick Look generator so that users can get previews of these documents in Quick Look. To learn how to create a Quick Look plug-in, see *[Quick Look Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/Quicklook_Programming_Guide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005020)*.

Quick Look 插件，也被熟知为 Quick Look 生成器，将文档从原始格式转化为 Quick Look 可以展示给用户查看的格式。如果你的应用创建 非标准格式或私有类型的文档，最好提供 Quick Look 生成器，这样用户可以从 Quick Look 预览文档。



***
#### 10）Safari plug-ins.    Safari 插件
Safari supports the Netscape-style plug-in model for incorporating additional types of content in the web browser. In Safari in OS X v10.7 and later, these plug-ins run in their own process, which improves the stability and security of Safari. Netscape-style plug-ins include support for onscreen drawing, event handling, and networking and scripting functions.

Safari 支持网景风格的插件模型，赖在浏览器中合并其它类型的内容。在 OSX 10.7 和之后的 Safari 中，这个插件在他们自己的进程中运行，增强了 Safari 的稳定性和安全性。网景风格的插件，包含屏幕绘图、事件处理 和 网络、脚本等功能。



**Note:** Beginning in OS X v10.7, Safari does not support WebKit plug-ins because they are not compatible with the new process architecture. Going forward, you must convert WebKit plug-ins to Netscape-style plug-ins or Safari Extensions.

备注：从  OSX 10.7 之后，Safari 不支持 WebKit 插件，因为他们和新的进程架构不兼容。此后，你需要将 WebKit 插件 转化为 Netscape-style  插件 或 Safari 拓展。



For information about creating Safari plug-ins with the Netscape API, see *[WebKit Plug-In Programming Topics](https://developer.apple.com/library/archive/documentation/InternetWeb/Conceptual/WebKit_PluginProgTopic/WebKitPluginTopics.html#//apple_ref/doc/uid/TP40001521)* and *[WebKit Objective-C Framework Reference](https://developer.apple.com/documentation/webkit)*. 



***
### 3、Safari Extensions. Safari 拓展

Use Safari extensions to add features both to the Safari web browser and to the content that Safari displays. For example, you can add custom buttons to the browser’s toolbar, reformat webpages, block unwanted sites, and create contextual menu items. Extensions let you inject scripts and style sheets into pages of web content. 

A Safari extension is a collection of HTML, JavaScript, and CSS files with support for both HTML5 and CSS3. Safari extensions are supported in both OS X and Windows systems running Safari 5.0 and later.

To learn more about Safari extensions, read *Safari Extensions Development Guide* in the [Safari Developer Library](https://developer.apple.com/library/safari/navigation/index.html). 



使用 Safari 拓展即可以增强 Safari 浏览器特性，也可以增强 Safari 的显示内容特性。比如，你可以给浏览的工具栏添加自定义的按钮，重新设置网页格式，阻止不需要的站点，以及创建上下文菜单项。拓展可以让你在网页内容中注入脚本和样式表。

一个 Safari 拓展是 HTML、 JavaScript 和 CSS文件  的集合，同事支持  HTML5 和 CSS3。OSX 和 Windows 系统中的 Safari 5.0 及后续版本都支持 Safari 拓展。

> 译者注：OSX 10.8及以后，苹果停止开发Windows版Safari。



***
### 4、Agent Applications 代理应用

An agent is a special type of application that typically runs in the background, providing information as needed to the user or to another app. For example, the Dock is an agent application that is run by OS X. 

An agent can be launched by the user but is more likely to be launched by the system or another app. As a result, agents do not show up in the Dock or the window displayed by the Force Quit menu command. Although agents might occasionally come to the foreground and display a user interface, they do not have a menu bar for choosing commands. All user interaction with an agent application is brief and focused on a specific goal, such as setting preferences or requesting information.

To create an agent application, you create a bundled app and include the `LSUIElement` key in its information property list (`Info.plist`) file. For more information on using this key, see *[Information Property List Key Reference](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009247)*. 



代理是一种特殊类型的应用，通常在后台运行，向用户或其他应用程序提供所需的信息。比如，Dock 是 OSX 运行的代理应用。

一个代理应用可以被用户启动，但更多的是被系统或其它应用启动。所以，代理应用不一般不会再 Dock 上展示，也不会出现在强制退出的目录中。虽然代理可能会出现在前台，并展示用户接口，但他们没有用于选择命令 的菜单栏（译者注：左上角的菜单栏）。所有和代理应用的用户交互都是简洁的，而且聚焦在特定的目标上，比如设置偏好或请求信息。

创建一个代理程序，你需要创建一个应用，并在 `Info.plist` 中包含 `LSUIElement` 键。



***
### 5、Screen Savers 屏幕保护

Screen savers are small programs that take over the screen after a certain period of idleness. Screen savers provide entertainment and also prevent the screen image from being burned into the surface of a display. OS X supports both slideshows and programmatically generated screen-saver content.

屏幕保护程序是一些小的程序，它们在电脑闲置了一段时间后会接管屏幕。屏幕保护程序不仅可以娱乐，还可以防止屏幕图像被烧入显示器表面。OSX 提供了幻灯片 和 编程方式生成的屏幕保护程序内容。



A slideshow is a simple type of screen saver that does not require any code to implement. To create a slideshow, you create a bundle with an extension of `.slideSaver`. Inside this bundle, you place a Resources directory that contains the images you want to display in your slideshow. Your bundle should also include an information property list that specifies basic information about the bundle, such as its name, identifier string, and version. 

OS X includes several slideshow screen savers you can use as templates for creating your own. These screen savers are located in `/System/Library/Screen Savers`. You should put your own slideshows in either `/Library/Screen Savers` or in the `~/Library/Screen Savers`directory of a user.



幻灯片类型的屏幕保护程序，不需要使用代码来实现。你可以创建  `.slideSaver` 类型的扩展来创建幻灯片，在包中，替换资源文件夹中的图片为你想展示的图片即可。您的包还应包含一个信息属性列表（info.plist），该列表指定有关捆绑软件的基本信息，例如其名称，标识符字符串和版本。

OSX 包含几个幻灯片类型的屏幕保护，你可以作为模板来创建你自己的。它们在 `/System/Library/Screen Savers` 文件夹中。你需要将你的幻灯片放到用户的  `/Library/Screen Savers` 或 `~/Library/Screen Savers`来给用户使用。



A programmatic screen saver is a screen saver that continuously generates content to appear on the screen. You can use this type of screen saver to create animations or to create a screen saver with user-configurable options. The bundle for a programmatic screen saver ends with the `.saver`extension. 

You create programmatic screen savers using Cocoa with the Swift language or with Objective-C. Specifically, you create a custom subclass of `ScreenSaverView` that provides the interface for displaying the screen saver content and options. The information property list of your bundle provides the system with the name of your custom subclass. For information on creating programmatic screen savers, see *[Screen Saver Framework Reference](https://developer.apple.com/documentation/screensaver)*.

程序式的屏保 需要不断生成内容以展示到屏幕上。你可以通过这种屏保创建动画，或根据用户可配置的选项来创建屏保。

你可以使用 OC 或 Swift 语言来使用 Cocoa 创建程序式屏保。特别注意的是，你创建自定义的类继承自 `ScreenSaverView`，`ScreenSaverView` 提供接口来展示评报内容和选项。包的 info.plist 提供了你自定义类的名字。





***
### 6、Services 服务

Services are not separate programs that you write; instead, they are features exported by your app for the benefit of other apps. Services let you share the resources and capabilities of your app with other apps in the system. Users access services through the Services menu that is available in every app’s application menu. (Services replace the contextual menu plug-in functionality that was available in earlier versions of OS X.)

服务不是您编写的单独程序； 相反，它们是您的应用导出的功能，以供其他应用使用。Services 帮助你和系统中其它应用分享资源和应用的功能。用户可以 通过每个应用程序 的应用程序菜单中的 `服务` 菜单访问服务。（Services 替换了早期版本中可用的上下文菜单插件功能）。



> 译者注：Typora 的服务
>
> ![image-20191219145835281](/Users/shushu/Library/Application Support/typora-user-images/image-20191219145835281.png)





A service typically acts on the currently selected data. When the user initiates a service, the app that holds the selected data places it on the pasteboard. The app whose service was selected then takes the data, processes it, and puts the results (if any) back on the pasteboard for the original app to retrieve. 

For example, a user might select a folder in the Finder and choose a service that compresses the folder contents and replaces them with the compressed version. 

Services can represent one-way actions as well. For example, a service could take the currently selected text in a window and use it to create the content of a new email message. For information on how to provide and use services in your app, see *[Services Implementation Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/SysServices/introduction.html#//apple_ref/doc/uid/10000101i)*.

服务通常会作用于当前选择的数据。当用户初始化一个服务，应用会获取到选中的数据，放到剪贴板中。然后，选择了服务的应用程序将获取数据，对其进行处理，然后将结果（如果有）放回粘贴板上，以供原始应用程序检索。

比如，一个用户肯恩贵选择 Finder 中的一个文件夹，然后选择一个服务去 压缩文件架内容，并将其替换为压缩版本。

服务也可以代表单向操作。比如，一个服务可以获取窗口中当前选中的文字，然后用它来创建一个新的邮件信息。



***
### 7、Preference Panes 偏好设置

Preference panes are used primarily to modify system preferences for the current user. Preference panes are implemented as plug-ins and installed in `/Library/PreferencePanes`. App developers can also take advantage of these plug-ins to manage per-user app preferences; however, most apps provide their own UI to manage preferences.

偏好设置面板主要用来修改 当前用户的系统偏好设置。偏好设置作为插件来执行，安装在  `/Library/PreferencePanes` 文件夹。App 开发者 可以利用这些插件 来管理每个用户的应用程序首选项。 但是，大多数应用程序提供了自己的UI 来管理偏好设置。



You might need to create preference panes if you create:

你可以使用偏好设置面板来创建：

- Hardware devices that are user configurable

  用户可配置的硬件设备

- Systemwide utilities, such as virus protection programs, that require user configuration

  系统工具，比如需要用户配置的病毒防护程序

  

If you're an app developer, you might want to reuse preference panes intended for the System Preferences app or use the same model to implement your app preferences. To learn how to create and manage preference panes, read *[Preference Pane Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/PreferencePanes/PreferencePanes.html#//apple_ref/doc/uid/10000110i)*.

如果你是应用开发这，你可能需要重用用于 “系统偏好设置”应用的偏好设置面板，或使用相同的模型来实现您的应用程序偏好设置。



***
### 8、Dynamic Websites and Web Services 动态网站和网页服务

OS X supports a variety of techniques and technologies for creating web content. In addition to [Identity Services](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW1), dynamic websites and web services offer web developers ways to deliver their content quickly and easily. 

OS X支持多种用于创建Web内容的技术。在 [Identity Services](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW1) 之外，动态网站和网络服务提供网站开发者方式去快速和简便发布他们的内容。



OS X provides support for creating and testing dynamic content in web pages. If you are developing CGI-based web apps, you can create websites using a variety of scripting technologies, including Perl and the PHP Hypertext Preprocessor (a complete list of scripting technologies is provided in [Scripts](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF120)). You can also create and deploy more complex web apps using JBoss, Tomcat, and WebObjects. To deploy your webpages, use the built-in Apache HTTP web server.

OSX 提供创建和测试网络中的动态内容。如果你在开发基于 CGI 的网页app。您可以使用多种脚本技术创建网站，包括 Perl 和 PHP。您还可以使用JBoss，Tomcat和WebObjects创建和部署更复杂的Web应用程序。使用内置的 Apache HTTP web server 来部署你的网页。



Safari provides standards-compliant support for viewing pages that incorporate numerous technologies, including HTML, XML, XHTML, DOM, CSS, Java, and JavaScript. You can also use Safari to test pages that contain multimedia content created for QuickTime, Flash, and Shockwave.

Safari 为查看页面提供了符合标准的支持，这些页面结合了多种技术，包括HTML，XML，XHTML，DOM，CSS，Java和JavaScript。你也可以使用 Safari 来测试包含 为 QuickTime, Flash, and Shockwave 创建的多媒体内容的网页。



The Simple Object Access Protocol (SOAP) is an object-oriented protocol that defines a way for programs to communicate over a network. XML-RPC is a protocol for performing remote procedure calls between programs. In OS X, you can create clients that use these protocols to gather information from web services across the Internet. To create these clients, you use technologies such as PHP, JavaScript, AppleScript, and Cocoa. 

SOAP 是一个面向对象的协议，给程序定义了一个网络沟通方法。XML-RPC是用于在程序之间执行远程过程调用的协议。在 OSX 中，你可以创建客户端，使用这些协议来从 web服务中采集信息。要创建这些客户端，可以使用PHP，JavaScript，AppleScript和Cocoa等技术。



Representational State Transfer (REST) is an alternative method for transferring data using URLs. OS X provides full support for building REST applications through NSURL, NSURLSession, and related classes. For more information, see *URL Loading System Programming Guide*.

REST是使用URL传输数据的另一种方法。 OS X 通过NSURL，NSURLSession 和相关类 来全面支持构建 REST应用程序。 查询更多的信息可见：*URL Loading System Programming Guide*.



If you want to provide your own web services in OS X, use WebObjects or implement the service using the scripting language of your choice. You then post your script code to a web server, give clients a URL, and publish the message format your script supports. 

For information on how to create client programs using AppleScript, see *[XML-RPC and SOAP Programming Guide](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/soapXMLRPC/chapter1/soapXMLRPC_intro.html#//apple_ref/doc/uid/TP30001126)*. For information on how to create web services, see *[WebObjects Web Services Programming Guide](https://developer.apple.com/library/archive/documentation/WebObjects/Web_Services/About/About.html#//apple_ref/doc/uid/TP30001019)*.



如果要在OS X中提供自己的Web服务，请使用 WebObjects 或使用您选择的脚本语言实现该服务。 然后，将脚本代码发布到Web服务器，为客户端提供URL，然后发布脚本支持的消息格式。

更多使用 AppleScript 创建客户端程序的信息，可见  *[XML-RPC and SOAP Programming Guide](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/soapXMLRPC/chapter1/soapXMLRPC_intro.html#//apple_ref/doc/uid/TP30001126)*。 如何创建web 服务，更多信息可见  *[WebObjects Web Services Programming Guide](https://developer.apple.com/library/archive/documentation/WebObjects/Web_Services/About/About.html#//apple_ref/doc/uid/TP30001019)*。



***
### 9、Mail Stationery  

The Mail app provides templates that give users prebuilt email messages that are easily customized. Because templates are HTML based, they can incorporate images and advanced formatting to give the user’s email a much more stylish and sophisticated appearance.

Developers and web designers can create custom template packages for external or internal users. Each template consists of an HTML page, a property list file, and a set of images which are packaged together in a bundle and then stored in the Mail app’s stationery folder. The HTML page and images define the content of the email message and can include drop zones for custom user content. The property list file gives Mail information about the template, such as its name, ID, and the name of its thumbnail image. To learn how to create new stationery templates, see *[Mail Programming Topics](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/MailArticles/Introduction/Introduction.html#//apple_ref/doc/uid/TP40006071)*. 

邮件应用程序提供了模板，这些模板为用户提供了易于定制的 预建电子邮件。 由于模板是基于HTML的，所以它们可以合并图像和高级格式，来为用户的电子邮件 提供更加时尚和精致的外观。

开发人员和Web设计人员 可以为外部或内部用户创建自定义模板包。 每个模板都包含一个HTML页，一个属性列表文件和一组图像，这些图像打包在一起捆绑在一起，然后存储在Mail应用程序的 信纸文件夹中。HTML页面和图像定义了电子邮件的内容，并且可以包含用于自定义用户内容的放置区域。 属性列表文件为Mail提供有关模板的信息，例如其名称，ID和其缩略图的名称。学习更多创建信纸模板的方法，可以参考  *[Mail Programming Topics](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/MailArticles/Introduction/Introduction.html#//apple_ref/doc/uid/TP40006071)*。



***
### 10、Command-Line Tools 命令行工具

Command-line tools are simple programs that manipulate data through a text-based interface. These tools do not use windows, menus, or other user interface elements traditionally associated with apps. Instead, they run from the command-line environment of the Terminal app. Because command-line tools require less explicit knowledge of the system to develop, they are often simpler to write than many other types of software. However, command-line tools are best suited to technically savvy users who are familiar with the conventions and syntax of the command-line interface. 

Xcode supports the creation of command-line tools from several initial code bases. For example, you can create a simple and portable tool using standard C or C++ library calls, or you can create a tool more specific to OS X using frameworks such as Core Foundation, Core Services, or Cocoa Foundation.

命令行工具是通过基于文本的接口操作数据的简单程序。这些工具不会使用 窗口、菜单或其它用户接口元素 传统的连接到应用。作为代替，他们从终端应用中运行命令行环境。因为命令行工具的开发 需要比较少的系统知识，他们一般比其它类型软件更容易编写。然而，命令行工具 最适合 熟悉命令行界面的约定和语法 的技术精通的用户。

Xcode 支持从几个不同的初始化代码基础 创建命令行工具。比如，你可以使用标准 C 或 C++ 库 创建一个简单的编写的工具，或者你可以使用比如 Core Foundation, Core Services, or Cocoa Foundation之类的框架来 创建针对 OSX 的工具。





***
### 11、Launch Items and Daemons 启动项和守护进程

Launch items are special programs that launch other programs or perform one-time operations during startup and login periods. Daemons are programs that run continuously and act as servers for processing client requests. You typically use launch items to launch daemons or perform periodic maintenance tasks, such as checking the hard drive for corrupted information. 

登录项是特殊的程序，用来启动其它程序，或者在启动和登录期间执行一次性操作。守护进程是不断运行，作为一个服务来处理客户端请求的程序。通常，您使用启动项目来启动守护程序 或执行定期维护任务，例如检查硬盘驱动器上是否有损坏的信息。



Launch items should not be confused with the login items found in the Accounts system preferences. Login items are typically agent applications that run within a given user’s session and can be configured by that user. Launch items are not user-configurable. 

启动项 不应该和 用户账户系统偏好设置中的 `登录项` 混淆。`登录项` 是特定的代理应用，在用户会话中运行，可以被用户配置。启动项不能被用户配置。



> 译者注：系统偏好设置中的登录项，和这里的启动项不同。
>
> ![image-20191219163234439](/Users/shushu/Library/Application Support/typora-user-images/image-20191219163234439.png)



Few developers should ever need to create launch items or daemons. These programs are reserved for special situations in which you need to guarantee the availability of a particular service. For example, OS X provides a launch item to run the DNS daemon. Similarly, a virus-detection program might install a launch item to launch a daemon that monitors the system for virus-like activity. In both cases, the launch item would run its daemon in the root session, which provides services to all users of the system. To learn more about launch items and daemons, see *[Daemons and Services Programming Guide](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/Introduction.html#//apple_ref/doc/uid/10000172i)*. 

几乎没有开发人员需要创建启动项或守护程序。这些程序被用于在特定情况下，你需要保证特定服务的功能可用。 OSX 提供一个启动项来运行 DNS 守护进程。相似的，一个病毒检测程序可能会安装一个启动项来启动进程，来监视系统中是否存在类似病毒的活动。在这些情况下，启动项会在根会话中运行它们的守护进程，给系统的所有用户提供服务。学习更多的启动项和守护进程，可以查看  *[Daemons and Services Programming Guide](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/Introduction.html#//apple_ref/doc/uid/10000172i)*。



***
### 12、Scripts 脚本

A script is a set of text commands that are interpreted at runtime and turned into a sequence of actions. Most scripting languages provide high-level features that make it easy to implement complex workflows quickly. Scripting languages are often very flexible, letting you call other programs and manipulate the data they return. Some scripting languages are also portable across platforms, so that you can use your scripts anywhere. 

脚本是一组文本命令，可在运行时进行解释并转换为一系列操作。大多数脚本语言提供高级功能，简单快捷的实现复杂的工作流。脚本语言通常非常灵活，可以让您调用其他程序并处理它们返回的数据。一些脚本语言也是跨平台的，你可以在任意地方使用你的脚本。



Table 1-1 lists many of the scripting languages available in OS X. 

| Language    | Description                                                  |
| :---------- | :----------------------------------------------------------- |
| AppleScript | An English-based language for controlling scriptable apps in OS X. Use it to tie together apps involved in a custom workflow or repetitive job. For more information, see *[AppleScript Overview](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/AppleScriptX/AppleScriptX.html#//apple_ref/doc/uid/10000156i)*. |
| `bash`      | A Bourne-compatible shell script language used to build programs on UNIX-based systems. |
| `csh`       | The C shell script language used to build programs on UNIX-based systems. |
| Perl        | A general-purpose scripting language supported on many platforms. Perl provides an extensive set of features suited for text parsing and pattern matching and also has some object-oriented features. For more information, see [The Perl Programming Language website](http://www.perl.org/). |
| PHP         | A cross-platform, general-purpose scripting language that is especially suited for web development. For more information, see [PHP: Hypertext Preprocessor](http://www.php.net/). |
| Python      | A general-purpose, object-oriented scripting language implemented for many platforms. For more information, see [Python Programming Language](http://www.python.org/). To learn about using Python with the Cocoa scripting bridge, see *[Ruby and Python Programming Topics for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/RubyPythonCocoa/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004936)*. |
| Ruby        | A general-purpose, object-oriented scripting language implemented for many platforms. For more information, see [Ruby Programming Language](http://www.ruby-lang.org/). To learn about using Ruby with the Cocoa scripting bridge, see *[Ruby and Python Programming Topics for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/RubyPythonCocoa/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004936)*. |
| `sh`        | The Bourne shell script language used to build programs on UNIX-based systems. |
| Swift       | Use the command line Swift compiler to create scripts. For information on the Swift command line tool type `man swift` in the terminal. |
| Tcl         | A general-purpose language implemented for many platforms. Tcl (Tool Command Language) is often used to create graphical interfaces for scripts. For more information, see [Tcl Developer Site](http://www.tcl.tk/). |
| `tcsh`      | A variant of the C shell script language used to build programs on UNIX-based systems. |
| `zsh`       | The Z shell script language used to build programs on UNIX-based systems. |



***
### 13、Scripting Additions for AppleScript

A scripting addition delivers additional functionality for AppleScript scripts by adding systemwide support for new commands or data types. Developers who need features not available in the current command set can use scripting additions to implement those features and make them available to all apps. For example, one of the built-in scripting additions extends the basic file-handling commands to support the reading and writing of file contents from an AppleScript script. For information on how to create a scripting addition, see Technical Note TN1164, “[Scripting Additions for OS X](http://developer.apple.com/technotes/tn/tn1164.html).”

通过添加对 新命令或数据类型的 系统范围支持，脚本附加功能为 AppleScript 脚本提供了附加功能。需要使用当前特性（在当前命令组中没有这个特性）的开发者，可以使用脚本附加功能，来实现这些特性，并让他们对所有应用可用。

比如，一个内置脚本添加功能 扩展了基本的文件处理命令，以支持从AppleScript 脚本 读取和写入文件内容。更多创建附加脚本的信息，可以阅读 Technical Note TN1164, “[Scripting Additions for OS X](http://developer.apple.com/technotes/tn/tn1164.html).”





***
### 14、Kernel Extensions  内核扩展

Kernel extensions are code modules that load directly into the kernel process space and therefore bypass the protections offered by the OS X core environment. Most developers have little need to create kernel extensions. The situations in which you might need a kernel extension are the following:

内和扩展是直接加载进内核进程空间的代码模块，因此可以绕过 OSX 核心环节提供的保护。大部分开发者没有创建内核扩展的需求。下列情况你可能需要内核扩展：

- Your code needs to handle a primary hardware interrupt.

  您的代码需要处理主要的硬件中断。

- The client of your code is inside the kernel.

  您的代码客户端在内核内部。

- A large number of apps require a resource your code provides. For example, you might implement a file-system stack using a kernel extension.

  大量的应用需要你的代码提供源。比如，你可能需要使用内核扩展实现一个文件系统堆栈。

- Your code has special requirements or needs to access kernel interfaces that are not available in the user space.

  你的代码有特别的需要，或者需要访问用户空间无法访问的内核接口。

  

Although a device driver is a type of kernel extension, by convention the term *kernel extension* refers to a code module that implements a new network stack or file system. You would not use a kernel extension to communicate with an external device such as a digital camera or a printer. (For information on communicating with external devices, see [Device Drivers](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF123).)

虽然 设备驱动 是 内核拓展的一种类型；按照约定，术语 `内核扩展` 是指实现新的网络堆栈或文件系统的代码模块。你可能不会使用一个内核扩展来和内部设备（如 电子相机，打印机）通信。关于和外设通信，可以阅读 [Device Drivers](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF123) 。



**Note:** Kernel data structures have an access model that makes it possible to write nonfragile kernel extensions—that is, kernel extensions that do not break when the kernel data structures change. Developers are highly encouraged to use the kernel-extension API for accessing kernel data structures.



Developing a kernel extension must be signed by a special type of developer ID certificate. Paid members of the developer program can request a kernel signing ID at `https://developer.apple.com/contact/kext/`.

For information about writing kernel extensions, see *[Kernel Programming Guide](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/About/About.html#//apple_ref/doc/uid/TP30000905)*. 



备注：内核数据结构拥有可访问模型，让编写稳定内核扩展成为可能，意即：档内核数据结构改变时，内核扩展不会中断。开发者被孤立来使用 内核扩展API 来访问内核数据结构。

开发一个内和扩展，必须使用特殊的 developer ID 证书签名。付费开发者会员可以在 `https://developer.apple.com/contact/kext/`. 申请内核签名ID。更多关于编写内核扩展的信息，可以阅读  *[Kernel Programming Guide](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/About/About.html#//apple_ref/doc/uid/TP30000905)*。



***
### 15、Device Drivers  设备驱动

Device drivers are a special type of kernel extension that enable OS X to communicate with many hardware devices, including mice, keyboards, and FireWire drives. Device drivers communicate hardware status to the system and facilitate the transfer of device-specific data to and from the hardware. OS X provides default drivers for many types of devices, but these might not meet the needs of all hardware developers. 

设备驱动是特殊的内核拓展类型，可以允许 OSX 和很多硬件设备通信，包括 鼠标、键盘 和 火线驱动。设备驱动和和系统沟通硬件状态，并促进设备特定数据与硬件之间的传输。OSX 提供默认的驱动给很多类型的设备，但这可能不能满足所有硬件开发者的需求。



Although developers of mice and keyboards might be able to use the standard drivers, many other developers require custom drivers. Developers of hardware such as scanners, printers, AGP cards, and PCI cards typically have to create custom device drivers because these devices require more sophisticated data handling than is usually needed for mice and keyboards. Hardware developers also tend to differentiate their hardware by adding custom features and behavior, which makes it difficult for Apple to provide generic drivers to handle all devices. 

虽然鼠标和键盘的开发者可能不能使用标准驱动，许多其他的开发者需要自定义的驱动。硬件如：扫描仪、打印机、AGP 卡 和 PCI 卡的开发者 通常需要创建自定义的设备驱动，因为这些设备需要 比鼠标和键盘 更复杂的数据处理。硬件开发者同样趋向于添加自定义的功能和表现，来让他们的产品不同，这让 Apple 难以提供驱动去处理所有设备。



Apple provides code you can use as the basis for your custom drivers. The I/O Kit provides an object-oriented framework for developing device drivers using C++. To learn more about the I/O Kit, see *[IOKit Fundamentals](https://developer.apple.com/library/archive/documentation/DeviceDrivers/Conceptual/IOKitFundamentals/Introduction/Introduction.html#//apple_ref/doc/uid/TP0000011)*.

苹果提供了代码，你可以作为你自定义的驱动的基础。 I/O Kit  提供了一个面向对象的框架来使用 C++ 开发设备驱动。关于学习更多 I/O Kit，可以阅读  *[IOKit Fundamentals](https://developer.apple.com/library/archive/documentation/DeviceDrivers/Conceptual/IOKitFundamentals/Introduction/Introduction.html#//apple_ref/doc/uid/TP0000011)*。









