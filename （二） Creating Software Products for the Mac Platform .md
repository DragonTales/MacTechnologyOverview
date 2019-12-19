# 【Mac Technology Overview】（二） Creating Software Products for the Mac Platform 

[toc]

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

- **Finder.** Show the sync state information in Finder.



### 2、App Store 苹果商店应用

Regardless of the app style you choose, your goal is probably to get your app into the Mac App Store. The development process that helps you achieve this goal includes a mix of coding and administrative tasks.

This document gives you an overview of Mac technologies that you can incorporate into your app. To learn more about the other tasks involved in the development process, read *App Distribution Quick Start*.



## 二、Development Languages 开发语言

The tools for OS X supports many different development languages. In addition to Swift, Objective-C, C++, C, and other such languages, Xcode provides support for many scripting languages. For more information, see [Scripts](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF120) below.

The most common languages used for development for OS X are Swift and Objective-C. The following sections call out key features in some of these environments. 



### 1、Swift

Swift is a new programming language for Cocoa and Cocoa Touch with a concise and expressive syntax. Swift incorporates research on programming language combined with decades of experience building Apple platforms. Code written in Swift co-exists with existing classes written in Objective-C, allowing for easy adoption.

Some of the key features of Swift are:

- Closures unified with function pointers
- First class functions
- Tuples and multiple return values
- Generics
- Fast and concise iteration over a range or collection
- Structs and Enums that support methods, extensions, and protocols
- Functional programming patterns
- Type safety and type inference with restricted access to direct pointers

Swift also supports the use of Playgrounds, an interactive environment for real time evaluation of code. Use playgrounds for designing a new algorithm, creating and verifying new tests, or learning about the language and APIs.

To learn more about Swift, see *The Swift Programming Language*, or for a quick overview, see *Welcome to Swift*.



### 2、Objective-C

Objective-C is a C-based programming language with object-oriented extensions. It is a primary development language for Cocoa apps. Unlike C++ and some other object-oriented languages, Objective-C comes with its own dynamic runtime environment. This runtime environment makes it much easier to extend the behavior of code at runtime without having access to the original source. 

Objective-C 2.0 supports the following features, among many others:

- Blocks (which are described in [Block Objects](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW10))
- Declared properties, which offer a simple way to declare and implement an object’s accessor methods
- A `for` operator syntax for performing fast enumerations of collections
- Formal and informal protocols, which allow you to declare methods that are independent of any specific class, but which any class might implement
- Categories and extensions, both of which allow you to add methods to an existing class

To learn about the Objective-C language, see *[The Objective-C Programming Language](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ObjectiveC/Introduction/introObjectiveC.html#//apple_ref/doc/uid/TP30001163)*. 



## 三、Other Types of Software

There are many other types of software you can develop for Mac. Most of these software products have no user interface (UI) and instead provide services that extend the capabilities of other software, such as third-party apps or the system itself.



### 1、Frameworks

A framework is a special type of bundle used to distribute shared resources, including library code, resource files, header files, and reference documentation. Frameworks offer a more flexible way to distribute shared code—for example, image files and localized strings—that you might otherwise put into a dynamic shared library. Frameworks also have a version control mechanism that makes it possible to distribute multiple versions of a framework in the same framework bundle.

Apple uses frameworks to distribute the public interfaces of OS X (and iOS), which are packaged in software development kits. A software development kit (SDK) collects the frameworks, header files, tools, and other resources necessary for developing software targeted at a specific version of a platform. You, too, can use frameworks to distribute public code and interfaces that you create, or to develop private shared libraries to embed in your apps.



**Note:** Although OS X also supports the concept of an “umbrella” framework, which encapsulates multiple subframeworks in a single package, this mechanism is used primarily for the distribution of Apple software. The creation of umbrella frameworks by third-party developers is not recommended.



You can use any programming language to create your own frameworks, but it’s best to choose a language that makes it easy to update the framework later. Apple frameworks generally export programmatic interfaces in ANSI C, Swift, or Objective-C. Both of these languages have a well-defined export structure that makes it easy to maintain compatibility between different revisions of the framework. 

To learn about the structure and composition of frameworks, see *[Framework Programming Guide](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPFrameworks/Frameworks.html#//apple_ref/doc/uid/10000183i)*. That document also describes how to use Xcode to create public and private frameworks.



### 2、Plug-ins

Plug-ins are the standard way to extend many apps and system behaviors. A plug-in is a bundle whose code is loaded dynamically into the runtime of an app. Because it’s loaded dynamically, a plug-in can be added and removed by the user. 

The app and system plug-ins listed below represent some of the many opportunities for developing plug-ins.

**Address Book action plug-ins.** An Address Book plug-in lets you add custom actions that act on the data in a person’s Address Book card. For example, the existing Large Type action displays the selected phone number in large type. Each action plug-in performs a single action, which can open a simple window within the Address Book app. If an action needs to do anything else, it must launch your app to perform the action. To learn how to create an Address Book action plug-in, see [Creating and Using Address Book Action Plug-ins](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AddressBook/Tasks/Actions.html#//apple_ref/doc/uid/20001681). 



**App plug-ins.** An app plug-in can extend the features of any app that supports a plug-in model. In addition to third-party apps, several Apple apps also support plug-ins, such as iTunes, Final Cut Pro, and Aperture. For information about developing plug-ins for Apple apps, visit the [Apple Developer](http://developer.apple.com/) website. 

**Automator plug-ins.** Using an Automator plug-in, you can expand the default set of actions available in Automator, a utility app that lets users assemble complex scripts using a palette of predefined actions. Automator plug-ins can be written in AppleScript or Objective-C, so you can write them for your own app’s features or for the features of other scriptable apps. (It’s a good idea to provide Automator plug-ins for your app’s most common tasks because doing so gives users more ways to interact with your app.) To learn how to write an Automator plug-in, see *[Automator Programming Guide](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/AutomatorConcepts/Automator.html#//apple_ref/doc/uid/TP40001450)*. 





**Core Audio plug-ins.** A Core Audio plug-in can support the manipulation of audio streams during most processing stages. For example, you can use plug-ins to generate, process, or receive an audio stream or to interact with new types of audio-related hardware devices. To begin learning about Core Audio, read *[Core Audio Overview](https://developer.apple.com/library/archive/documentation/MusicAudio/Conceptual/CoreAudioOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003577)*.



**Image units.** An image unit is a type of plug-in that you can use with the Core Image and Core Video technologies. An image unit consists of a collection of filters—each of which implements a specific manipulation for image data—packaged together in a single bundle. For example, you could write a set of filters that perform different kinds of edge detection and package them as one image unit. To learn how to create an image unit, see [Creating Custom Filters](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreImaging/ci_custom_filters/ci_custom_filters.html#//apple_ref/doc/uid/TP30001185-CH6). 





**Input methods.** A common example of an input method is an interface for typing Japanese or Chinese characters using multiple keystrokes. Other examples of input methods include spelling checkers and pen-based gesture recognition systems. You can create input methods using Input Method Kit (`InputMethodKit.framework`). For information on how to use this framework, see *[Input Method Kit Framework Reference](https://developer.apple.com/documentation/inputmethodkit)*. 

**Metadata importers.** Spotlight relies on metadata importers to gather information about the user’s files and to build a systemwide index. Spotlight uses this index to help users find information by searching on attributes that make sense to them, such as the duration of a video or the dimensions of an image. If your app defines a custom file format, you should always provide a metadata importer for that file format. (If your app relies on commonly used file formats, such as JPEG, RTF, or PDF, the system provides a metadata importer for you.) To learn how to create metadata importers, see *[Spotlight Importer Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/MDImporters/MDImporters.html#//apple_ref/doc/uid/TP40001267)*. 

**Quartz Composer plug-ins.** Quartz Composer supports a plug-in mechanism that allows you to create a custom patch and make it available in the Quartz Composer workspace and to most Quartz Composer clients. (A *patch* is processing unit that performs a specific task, such as processing a string or rendering an OpenGL texture.) To learn how to create a Quartz Composer plug-in, see *[Quartz Composer Custom Patch Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/QuartzComposer_Patch_PlugIn_ProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004787)*.

**Quick Look plug-ins.** A Quick Look plug-in—also known as a Quick Look generator—converts a document from its native format into a format that Quick Look can display to users. If your app creates documents of a nonstandard or private type, it’s a good idea to provide a Quick Look generator so that users can get previews of these documents in Quick Look. To learn how to create a Quick Look plug-in, see *[Quick Look Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/Quicklook_Programming_Guide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005020)*.

**Safari plug-ins.** Safari supports the Netscape-style plug-in model for incorporating additional types of content in the web browser. In Safari in OS X v10.7 and later, these plug-ins run in their own process, which improves the stability and security of Safari. Netscape-style plug-ins include support for onscreen drawing, event handling, and networking and scripting functions.



**Note:** Beginning in OS X v10.7, Safari does not support WebKit plug-ins because they are not compatible with the new process architecture. Going forward, you must convert WebKit plug-ins to Netscape-style plug-ins or Safari Extensions.



For information about creating Safari plug-ins with the Netscape API, see *[WebKit Plug-In Programming Topics](https://developer.apple.com/library/archive/documentation/InternetWeb/Conceptual/WebKit_PluginProgTopic/WebKitPluginTopics.html#//apple_ref/doc/uid/TP40001521)* and *[WebKit Objective-C Framework Reference](https://developer.apple.com/documentation/webkit)*. 



### 3、Safari Extensions

Use Safari extensions to add features both to the Safari web browser and to the content that Safari displays. For example, you can add custom buttons to the browser’s toolbar, reformat webpages, block unwanted sites, and create contextual menu items. Extensions let you inject scripts and style sheets into pages of web content. 

A Safari extension is a collection of HTML, JavaScript, and CSS files with support for both HTML5 and CSS3. Safari extensions are supported in both OS X and Windows systems running Safari 5.0 and later.

To learn more about Safari extensions, read *Safari Extensions Development Guide* in the [Safari Developer Library](https://developer.apple.com/library/safari/navigation/index.html). 



### 4、Agent Applications

An agent is a special type of application that typically runs in the background, providing information as needed to the user or to another app. For example, the Dock is an agent application that is run by OS X. 

An agent can be launched by the user but is more likely to be launched by the system or another app. As a result, agents do not show up in the Dock or the window displayed by the Force Quit menu command. Although agents might occasionally come to the foreground and display a user interface, they do not have a menu bar for choosing commands. All user interaction with an agent application is brief and focused on a specific goal, such as setting preferences or requesting information.

To create an agent application, you create a bundled app and include the `LSUIElement` key in its information property list (`Info.plist`) file. For more information on using this key, see *[Information Property List Key Reference](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009247)*. 



### 5、Screen Savers

Screen savers are small programs that take over the screen after a certain period of idleness. Screen savers provide entertainment and also prevent the screen image from being burned into the surface of a display. OS X supports both slideshows and programmatically generated screen-saver content.

A slideshow is a simple type of screen saver that does not require any code to implement. To create a slideshow, you create a bundle with an extension of `.slideSaver`. Inside this bundle, you place a Resources directory that contains the images you want to display in your slideshow. Your bundle should also include an information property list that specifies basic information about the bundle, such as its name, identifier string, and version. 

OS X includes several slideshow screen savers you can use as templates for creating your own. These screen savers are located in `/System/Library/Screen Savers`. You should put your own slideshows in either `/Library/Screen Savers` or in the `~/Library/Screen Savers`directory of a user.

A programmatic screen saver is a screen saver that continuously generates content to appear on the screen. You can use this type of screen saver to create animations or to create a screen saver with user-configurable options. The bundle for a programmatic screen saver ends with the `.saver`extension. 

You create programmatic screen savers using Cocoa with the Swift language or with Objective-C. Specifically, you create a custom subclass of `ScreenSaverView` that provides the interface for displaying the screen saver content and options. The information property list of your bundle provides the system with the name of your custom subclass. For information on creating programmatic screen savers, see *[Screen Saver Framework Reference](https://developer.apple.com/documentation/screensaver)*.



### 6、Services

Services are not separate programs that you write; instead, they are features exported by your app for the benefit of other apps. Services let you share the resources and capabilities of your app with other apps in the system. Users access services through the Services menu that is available in every app’s application menu. (Services replace the contextual menu plug-in functionality that was available in earlier versions of OS X.)

A service typically acts on the currently selected data. When the user initiates a service, the app that holds the selected data places it on the pasteboard. The app whose service was selected then takes the data, processes it, and puts the results (if any) back on the pasteboard for the original app to retrieve. For example, a user might select a folder in the Finder and choose a service that compresses the folder contents and replaces them with the compressed version. Services can represent one-way actions as well. For example, a service could take the currently selected text in a window and use it to create the content of a new email message. For information on how to provide and use services in your app, see *[Services Implementation Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/SysServices/introduction.html#//apple_ref/doc/uid/10000101i)*.



### 7、Preference Panes

Preference panes are used primarily to modify system preferences for the current user. Preference panes are implemented as plug-ins and installed in `/Library/PreferencePanes`. App developers can also take advantage of these plug-ins to manage per-user app preferences; however, most apps provide their own UI to manage preferences.

You might need to create preference panes if you create:

- Hardware devices that are user configurable
- Systemwide utilities, such as virus protection programs, that require user configuration

If you're an app developer, you might want to reuse preference panes intended for the System Preferences app or use the same model to implement your app preferences. To learn how to create and manage preference panes, read *[Preference Pane Programming Guide](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/PreferencePanes/PreferencePanes.html#//apple_ref/doc/uid/10000110i)*.



### 8、Dynamic Websites and Web Services

OS X supports a variety of techniques and technologies for creating web content. In addition to [Identity Services](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW1), dynamic websites and web services offer web developers ways to deliver their content quickly and easily. 

OS X provides support for creating and testing dynamic content in web pages. If you are developing CGI-based web apps, you can create websites using a variety of scripting technologies, including Perl and the PHP Hypertext Preprocessor (a complete list of scripting technologies is provided in [Scripts](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF120)). You can also create and deploy more complex web apps using JBoss, Tomcat, and WebObjects. To deploy your webpages, use the built-in Apache HTTP web server.

Safari provides standards-compliant support for viewing pages that incorporate numerous technologies, including HTML, XML, XHTML, DOM, CSS, Java, and JavaScript. You can also use Safari to test pages that contain multimedia content created for QuickTime, Flash, and Shockwave.

The Simple Object Access Protocol (SOAP) is an object-oriented protocol that defines a way for programs to communicate over a network. XML-RPC is a protocol for performing remote procedure calls between programs. In OS X, you can create clients that use these protocols to gather information from web services across the Internet. To create these clients, you use technologies such as PHP, JavaScript, AppleScript, and Cocoa. 

Representational State Transfer (REST) is an alternative method for transferring data using URLs. OS X provides full support for building REST applications through NSURL, NSURLSession, and related classes. For more information, see *URL Loading System Programming Guide*.

If you want to provide your own web services in OS X, use WebObjects or implement the service using the scripting language of your choice. You then post your script code to a web server, give clients a URL, and publish the message format your script supports. 

For information on how to create client programs using AppleScript, see *[XML-RPC and SOAP Programming Guide](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/soapXMLRPC/chapter1/soapXMLRPC_intro.html#//apple_ref/doc/uid/TP30001126)*. For information on how to create web services, see *[WebObjects Web Services Programming Guide](https://developer.apple.com/library/archive/documentation/WebObjects/Web_Services/About/About.html#//apple_ref/doc/uid/TP30001019)*.



### 9、Mail Stationery

The Mail app provides templates that give users prebuilt email messages that are easily customized. Because templates are HTML based, they can incorporate images and advanced formatting to give the user’s email a much more stylish and sophisticated appearance.

Developers and web designers can create custom template packages for external or internal users. Each template consists of an HTML page, a property list file, and a set of images which are packaged together in a bundle and then stored in the Mail app’s stationery folder. The HTML page and images define the content of the email message and can include drop zones for custom user content. The property list file gives Mail information about the template, such as its name, ID, and the name of its thumbnail image. To learn how to create new stationery templates, see *[Mail Programming Topics](https://developer.apple.com/library/archive/documentation/AppleApplications/Conceptual/MailArticles/Introduction/Introduction.html#//apple_ref/doc/uid/TP40006071)*. 



### 10、Command-Line Tools

Command-line tools are simple programs that manipulate data through a text-based interface. These tools do not use windows, menus, or other user interface elements traditionally associated with apps. Instead, they run from the command-line environment of the Terminal app. Because command-line tools require less explicit knowledge of the system to develop, they are often simpler to write than many other types of software. However, command-line tools are best suited to technically savvy users who are familiar with the conventions and syntax of the command-line interface. 

Xcode supports the creation of command-line tools from several initial code bases. For example, you can create a simple and portable tool using standard C or C++ library calls, or you can create a tool more specific to OS X using frameworks such as Core Foundation, Core Services, or Cocoa Foundation.



### 11、Launch Items and Daemons

Launch items are special programs that launch other programs or perform one-time operations during startup and login periods. Daemons are programs that run continuously and act as servers for processing client requests. You typically use launch items to launch daemons or perform periodic maintenance tasks, such as checking the hard drive for corrupted information. 

Launch items should not be confused with the login items found in the Accounts system preferences. Login items are typically agent applications that run within a given user’s session and can be configured by that user. Launch items are not user-configurable. 

Few developers should ever need to create launch items or daemons. These programs are reserved for special situations in which you need to guarantee the availability of a particular service. For example, OS X provides a launch item to run the DNS daemon. Similarly, a virus-detection program might install a launch item to launch a daemon that monitors the system for virus-like activity. In both cases, the launch item would run its daemon in the root session, which provides services to all users of the system. To learn more about launch items and daemons, see *[Daemons and Services Programming Guide](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/Introduction.html#//apple_ref/doc/uid/10000172i)*. 



### 12、Scripts

A script is a set of text commands that are interpreted at runtime and turned into a sequence of actions. Most scripting languages provide high-level features that make it easy to implement complex workflows quickly. Scripting languages are often very flexible, letting you call other programs and manipulate the data they return. Some scripting languages are also portable across platforms, so that you can use your scripts anywhere. 

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



### 13、Scripting Additions for AppleScript

A scripting addition delivers additional functionality for AppleScript scripts by adding systemwide support for new commands or data types. Developers who need features not available in the current command set can use scripting additions to implement those features and make them available to all apps. For example, one of the built-in scripting additions extends the basic file-handling commands to support the reading and writing of file contents from an AppleScript script. For information on how to create a scripting addition, see Technical Note TN1164, “[Scripting Additions for OS X](http://developer.apple.com/technotes/tn/tn1164.html).”



### 14、Kernel Extensions

Kernel extensions are code modules that load directly into the kernel process space and therefore bypass the protections offered by the OS X core environment. Most developers have little need to create kernel extensions. The situations in which you might need a kernel extension are the following:

- Your code needs to handle a primary hardware interrupt.
- The client of your code is inside the kernel.
- A large number of apps require a resource your code provides. For example, you might implement a file-system stack using a kernel extension.
- Your code has special requirements or needs to access kernel interfaces that are not available in the user space.

Although a device driver is a type of kernel extension, by convention the term *kernel extension* refers to a code module that implements a new network stack or file system. You would not use a kernel extension to communicate with an external device such as a digital camera or a printer. (For information on communicating with external devices, see [Device Drivers](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-TPXREF123).)



**Note:** Kernel data structures have an access model that makes it possible to write nonfragile kernel extensions—that is, kernel extensions that do not break when the kernel data structures change. Developers are highly encouraged to use the kernel-extension API for accessing kernel data structures.



Developing a kernel extension must be signed by a special type of developer ID certificate. Paid members of the developer program can request a kernel signing ID at `https://developer.apple.com/contact/kext/`.

For information about writing kernel extensions, see *[Kernel Programming Guide](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/About/About.html#//apple_ref/doc/uid/TP30000905)*. 



### 15、Device Drivers

Device drivers are a special type of kernel extension that enable OS X to communicate with many hardware devices, including mice, keyboards, and FireWire drives. Device drivers communicate hardware status to the system and facilitate the transfer of device-specific data to and from the hardware. OS X provides default drivers for many types of devices, but these might not meet the needs of all hardware developers. 

Although developers of mice and keyboards might be able to use the standard drivers, many other developers require custom drivers. Developers of hardware such as scanners, printers, AGP cards, and PCI cards typically have to create custom device drivers because these devices require more sophisticated data handling than is usually needed for mice and keyboards. Hardware developers also tend to differentiate their hardware by adding custom features and behavior, which makes it difficult for Apple to provide generic drivers to handle all devices. 

Apple provides code you can use as the basis for your custom drivers. The I/O Kit provides an object-oriented framework for developing device drivers using C++. To learn more about the I/O Kit, see *[IOKit Fundamentals](https://developer.apple.com/library/archive/documentation/DeviceDrivers/Conceptual/IOKitFundamentals/Introduction/Introduction.html#//apple_ref/doc/uid/TP0000011)*.