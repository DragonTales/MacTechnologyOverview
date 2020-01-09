# 【Mac Technology Overview】（八）Migrating from Cocoa Touch （从 Cocoa Touch 移植应用）

[TOC]



***
原文地址： <https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW1>
***
If you`ve developed an iOS app, many of the frameworks available in OS X should already seem familiar to you. The basic technology stack in iOS and OSX are identical in many respects. But, despite the similarities, not all of the frameworks in OS X are exactly the same as their iOS counterparts. This chapter describes the differences you may encounter as you create Mac apps and explains how you can adjust your code to handle some of the more significant differences.

如果你已经开发了一个iOS应用程序，那么OS X中的许多框架对你来说应该已经很熟悉了。iOS 和 OSX 的基本技术堆栈 在许多方面是相同的。但是，尽管有相似之处，并不是OS X中的所有框架都与iOS中的完全相同。本章描述了你在创建Mac应用程序时可能遇到的差异，并解释了如何调整代码来处理一些更重要的差异。

## 一、General Migration Notes 

In OS X, apps typically have a screen that is larger, and resources that are greater, than in iOS. As a developer, you have more frameworks at your disposal in OS X development and (generally) more programmatic possibilities. This greater range of possibilities may be a pleasant prospect, but it also requires different ways of thinking about user expectations and app design.

As you work on migrating your app, pay attention to the idioms and metaphors that are different on each platform. For example, you would not base your OS X app on a stack of view controllers or include a feature that requires a gyroscope. It’s important that each version of your app looks and behaves as if it’s been designed for the platform it’s running on.

If your Cocoa Touch app is already factored according to the Model-View-Controller design pattern, it should be relatively easy to migrate key portions of your app to OS X.



在OS X中，应用程序的屏幕通常比iOS更大，资源也更丰富。作为开发人员，你可以在OS X开发中使用更多的框架，并且(通常)有更多的编程可能性。这种更大范围的可能性可能是一个令人愉快的前景，但它也需要考虑用户期望和应用程序设计的不同方式。

在迁移应用程序时，请注意每个平台上不同的习惯用法和隐喻。例如，你不会将OS X 应用程序建立在 视图控制器的堆栈上，也不会包含需要陀螺仪的功能。重要的是，你的应用程序的每个版本的外观和行为，好像它是为它所运行的平台设计的。

如果你的Cocoa Touch应用程序已经根据 模型-视图-控制器设计（MVC） 模式进行了分解，那么将应用程序的关键部分迁移到OS X应该是相对容易的。



### 1、Migrating the Data Model 迁移数据模型

Cocoa Touch apps whose data model is based on classes in the Foundation and Core Foundation frameworks can be brought over to OS X with little or no modification. OS X includes both frameworks, and they are virtually identical to their iOS counterparts. Most of the differences that do exist are relatively minor or are related to features that are not present in iOS. For example, iOS apps do not support AppleScript. For a detailed list of differences, see [Foundation Framework Differences](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW2). 

If your Cocoa Touch app is built on top of Core Data, you can easily migrate that data model to an OS X app. The Core Data framework in OS X supports binary and SQLite data stores (as it does in iOS), and it also supports XML data stores. For the supported data stores, you can copy your Core Data resource files to your OS X app project and use them as is. For information on how to use Core Data in your app, see *[Core Data Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CoreData/index.html#//apple_ref/doc/uid/TP40001075)*. 

Because OS X apps can display much more data on the screen than iOS apps can, you can expand your data model as part of your migration, as long as it doesn’t degrade the user experience. In addition to having access to more display space, an OS X app also has access to more resources, including memory. Although you can work with larger data sets, be sure that your algorithms scale to the new platform so that you don’t introduce inefficiencies when you migrate your app. 



Cocoa Touch 应用程序的数据模型是基于 Foundation 和 Core Foundation 框架中的类，可以在 很少或不做修改的情况下，移植到OS X。OS X包含了这两种框架，它们实际上与iOS版本完全相同。存在的大多数差异相对较小，或者与iOS中不存在的功能相关。例如，iOS应用程序不支持AppleScript。有关差异的详细列表，请参见  [Foundation Framework Differences](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW2) 。

如果你的 Cocoa Touch 应用程序构建在Core Data之上，那么你可以轻松地将数据模型迁移到OS X应用程序中。OS X 中的 Core Data 框架支持二进制和 SQLite数据存储(就像在iOS中一样)，它还支持 XML数据存储。对于支持的数据存储，你可以将你的核心数据资源文件 复制到 OS X 应用程序项目中，并按原样使用它们。有关如何在应用程序中使用Core Data的信息，请参阅  *[Core Data Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CoreData/index.html#//apple_ref/doc/uid/TP40001075)*。

由于 OS X 应用程序可以在屏幕上显示比 iOS 应用程序 多得多的数据，所以你可以扩展你的数据模型作为你迁移的一部分，只要它不会降低用户体验。除了可以访问更多的显示空间，OS X应用程序还可以访问更多的资源，包括内存。尽管你可以处理更大的数据集，但请确保你的算法可以扩展到新的平台，这样在迁移应用程序时就不会引入低效的问题。



### 2、Migrating the User Interface 迁移用户界面

For various reasons, the structure and implementation of the user interface (UI) in an OS X app is very different from that in an iOS app. Adapting your app to these differences is the main work of migration. As you bring your iOS app to OS X, keep the following themes in mind. 

- **Device differences impact the user experience.** In contrast to an iOS app, an OS X app has access to a larger screen, a more dependable supply of power, and a much larger pool of memory. These differences affect how an app presents information to users and how users interact with the app. For example, there is generally only one window per app in iOS, and that window has a fixed size, plays a limited role in the UI, and cannot be manipulated by users. On the other hand, an OS X app often has multiple windows. These windows can contain separate documents, or they might display auxiliary information, such as tool palettes or app preferences. Users can move, resize, close, minimize, and perform other operations with the windows in an OS X app. 

- **Users interact with apps differently on each platform.** Because people use touch gestures to interact with iOS apps, the onscreen UI objects must be large enough to manipulate with a human finger. In OS X, people use a mouse, trackpad, or other input device to move the onscreen pointer and interact with UI objects. Because the pointer is much more precise than a finger, the layout of an OS X app tends to be very different from the layout of an iOS app.

  

- **Users are not always aware of the file system.** iOS users have no direct access to the file system; instead, an iOS app reads and writes files to prescribed locations in its sandbox. In OS X, users can access the file system using the Finder interface. Although not all OS X apps expose the file system to users, those that do must also be prepared to handle issues related to document format, file encoding, and so on. Some OS X apps—for example, iPhoto and iTunes—keep their databases in an app-specific location and provide users with ways to manage their content without interacting with the file system.



When you create a new OS X app project in Xcode, you don’t get the same app templates to choose from that you do when you start an iOS app project. (Although OS X defines a few app types—described in [Apps](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-SW10)—these types are not directly related to the project templates.) The Cocoa app template is the typical choice for developing a standard OS X app.

For comprehensive information about the UI design principles of OS X, see *OS X Human Interface Guidelines*. For programmatic information about the windows and views you use to build your interface, and the underlying architecture on which they are based, see *[Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)*. 



由于各种原因，OS X 应用程序的用户界面(UI)的结构 和实现与iOS应用程序有很大的不同。让应用程序 适应这些差异 是迁移的主要工作。当你将你的iOS应用程序带到 OS X时，请记住以下主题。

- **设备差异影响用户体验。**与iOS应用程序相比，OS X应用程序拥有更大的屏幕、更可靠的电源供应和更大的内存池。这些差异影响了应用如何向用户呈现信息，以及用户与应用的交互方式。例如，在iOS中，每个应用通常只有一个窗口，窗口大小固定，在UI中发挥的作用有限，用户无法操作。另一方面，OS X应用程序通常有多个窗口。这些窗口可以包含单独的文档，也可以显示辅助信息，如工具面板或应用程序首选项。用户可以在OS X应用程序中移动、调整大小、关闭、最小化和执行其他操作。

- **用户在每个平台上与应用程序的交互方式不同。**由于人们使用触摸手势与iOS应用程序进行交互，所以屏幕上的UI对象必须足够大，可以用人类手指操作。在OS X中，人们使用鼠标、触摸板或其他输入设备来移动屏幕指针并与UI对象交互。由于指针比手指精确得多，OS X应用程序的布局往往与iOS应用程序的布局非常不同。
- **用户并不总是知道文件系统。** iOS 用户无法直接访问文件系统;相反，iOS 应用程序会将文件读写到沙盒中的指定位置。在OS X中，用户可以使用 Finder 接口访问文件系统。虽然不是所有 OS X 应用程序都向用户公开文件系统，但是那些公开文件系统的应用程序，也必须准备好处理与文档格式、文件编码等相关的问题。一些OS X应用程序(例如，iPhoto和itune) 将它们的数据库保存在特定于应用程序的位置，并为用户提供在 不与文件系统交互的情况下 管理其内容的方法。



当你在Xcode中创建一个新的OS X 应用程序项目时，你不会得到 与你启动iOS应用程序项目时相同的应用程序模板 供你选择。(尽管OS X定义了几个应用程序 [Apps](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-SW10) —— 不直接与项目模板类型相关。Cocoa 应用程序模板 是开发标准 OS X 应用程序的典型选择。

有关OS X的UI设计原则的详细信息，请参阅 *OS X Human Interface Guidelines*。有关用于 构建接口的窗口和视图 及 其基础架构的编程信息，请参阅 *[Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)*。



***

### 3、Migration Strategies 迁移策略

When migrating your app from iOS to OS X, there are several approaches you can use to minimize the amount of code refactoring necessary in your view and controller classes. Each approach has its advantages and disadvantages, and is thus best used in specific instances, as described in Table 7-1.

当你将你的应用从iOS迁移到OS X时，你可以使用几种方法来 最小化视图和控制器类中必要的代码重构。每种方法都有其优点和缺点，因此最好在特定的实例中使用，如表 7-1 中所述。



| Situation                                                    | Migration approach                                           | Advantages                                                   | Disadvantages                                                |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| When you have heavily platform-dependent code                | Mirror your code across both platforms, customizing as necessary. | Offers flexibility                                           | Code duplication, resulting in greater maintenance and testing costs |
| When a common, lower-level framework provides necessary functionality | Use the common framework. For example, drop down from `UIKit` and `AppKit` to a lower-level, shared framework, to maximize code re-use and and minimize maintenance. | Maximizes code reuse, minimizes maintenance                  | Significant refactoring of your existing code, and less functionality provided by the lower-level framework |
| When dealing with an underlying API that’s significantly different between the two platforms (option 1) | Use an adapter pattern, a design pattern that allows the interface of an existing class to be accessed from another interface. | Maximizes code reuse, provides simplified interface, requires less maintenance | Additional code to write                                     |
| When dealing with an underlying API that’s significantly different between the two platforms (option 2) | Create an adapter using the `#define` preprocessor macro. For example, replace every instance of your color class with either `UIColor` or `NSColor`. This approach also gives you compile-time error checking.<br> 使用`#define`  预处理器宏创建适配器。例如，用`UIColor `或 `NSColor` 替换 color类的每个实例。 | Minimizes new code to write, provides compile-time error checking | Can only be used for supported classes: `UIColor` and `NSColor`; `UIFont` and `NSFont`; `UIImage` and `NSImage`; `UIBezierPath` and `NSBezierPath`. Limited API coverage within supported classes. Requires custom archiving approach. |



**Video::** [WWDC 2013 Bringing Your iOS Apps to OS X](http://devstreaming.apple.com/videos/wwdc/2013/216xcx4x7if809qdggi7vcc/216/ref.mov#t=28:32,41:49)

[WWDC 2014 Sharing code between iOS and OS X](https://developer.apple.com/videos/wwdc/2014/#233)





### 4、Migrating the Controller Layer 迁移控制器层

Controller objects are a critical area of difference between app development for iOS and for OS X. In iOS, `UIViewController` objects are key components that support the presentation of data and handle many device-specific behaviors such as orientation changes. In OS X v10.10 there are three view controllers: `NSViewController`, `NSSplitViewController`, and `NSTableViewController`. Each view controller type participates in the event message chain and is able to respond to event messages.

Before OS X v10.10 there was only one view controller class, `NSViewController`, that do not receive event messages. In those earlier versions, the `NSWindowController` class is most similar to `UIViewController`. In OS X, a window controller manages a window and its current contents. 

OS X has no equivalent to the iOS navigation controller which manages a stack of view controllers. If your iOS app uses a view controller stack to display the UI, you need to redesign your app to take advantage of the larger device display and multiple windows that are available in OS X.

In addition to the view and window controller classes, OS X also has the `NSController` class. Instances of this class (and its concrete subclasses) are controller objects that are used in the Cocoa bindings technology. (Cocoa bindings, which is not available in iOS, connects data in a model object with the presentation of that data in a view object, so that both objects are updated when the data changes.) Because controller objects manage an app’s data model and not its views, they can be considered data controllers rather than view controllers.

For information about view controllers in OS X, see *[NSViewController Class Reference](https://developer.apple.com/documentation/appkit/nsviewcontroller)*, and for information about window controllers see *[NSWindowController Class Reference](https://developer.apple.com/documentation/appkit/nswindowcontroller)*. To learn more about `NSController` objects and Cocoa bindings, see *[Cocoa Bindings Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaBindings/CocoaBindings.html#//apple_ref/doc/uid/10000167i)*.



控制器对象是iOS应用程序开发与OS x应用程序开发的一个关键区别领域。在iOS中，`UIViewController` 对象是支持数据表示的关键组件，并处理许多设备特定的行为，如方向改变。在OS X v10.10中有三个视图控制器: `NSViewController `， ` NSSplitViewController `和` NSTableViewController `。每个视图控制器类型都参与事件消息链，并能够响应事件消息。

在OS X v10.10之前，只有一个视图控制器类 `NSViewController`，它不接收事件消息。在那些早期的版本中，` NSWindowController `类最类似于` UIViewController `。在OS X中，窗口控制器管理窗口及其当前内容。

OS X没有与 管理视图控制器堆栈 的iOS导航控制器 等价的东西。如果你的 iOS 应用程序 使用 视图控制器堆栈 来显示UI，你需要重新设计你的应用程序来利用OS X中更大的设备显示和多个窗口。

除了视图和窗口控制器类，OS X还有`NSController `类。此类(及其具体子类)的实例 是Cocoa绑定技术中 使用的控制器对象。(Cocoa bindings在iOS中不可用，它将模型对象中的数据 与视图对象中的数据表示连接起来，以便在数据更改时 更新这两个对象。) 因为控制器对象管理应用程序的数据模型 而不是视图，所以它们可以被视为数据控制器而不是视图控制器。

有关OS X中的视图控制器的信息，请参阅  *[NSViewController Class Reference](https://developer.apple.com/documentation/appkit/nsviewcontroller)*, 有关窗口控制器的信息，请参阅  *[NSWindowController Class Reference](https://developer.apple.com/documentation/appkit/nswindowcontroller)*, 有关 `NSController` 对象和 Cocoa绑定的更多信息，请参见 *[Cocoa Bindings Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaBindings/CocoaBindings.html#//apple_ref/doc/uid/10000167i)*。



## 二、Differences Between the UIKit and AppKit Frameworks UIKit和AppKit框架的不同

In OS X, the AppKit framework provides the infrastructure for building graphical apps, managing the event loop, and performing other UI-related tasks. Although AppKit and UIKit (the corresponding iOS framework) provide similar support to apps, the implementation is very different. When you migrate an iOS app to OS X, you replace a significant number of UIKit classes with functionality provided by AppKit.

For information about the classes of AppKit, see *[Application Kit Framework Reference](https://developer.apple.com/documentation/appkit)*.

在OS X中，AppKit 框架提供了 构建图形化应用程序、管理事件循环 和 执行其他UI 相关任务的基础结构。虽然 AppKit 和 UIKit(对应的iOS框架) 对应用程序提供了类似的支持，但其实现是非常不同的。当你将一个iOS 应用迁移到OS X时，你需要用AppKit提供的功能替换了大量的UIKit类。

有关AppKit类的信息，请参见  *[Application Kit Framework Reference](https://developer.apple.com/documentation/appkit)*。





### 1、User Events and Event Handling 用户时间和事件处理

Handling events in OS X differs significantly from handling events in iOS apps, mainly because the types of user events on each platform are different. If your iOS app does its own event handling, you will have to rewrite much if not all of the event-handling code when you migrate the app to OS X. 

Unlike iOS, which defines touch events and motion events, OS X defines mouse events, keyboard events, trackpad events, tablet events, and tracking-area events. All of these event types relate to peripheral devices that can be attached to a computer. In addition, most of these event types include phases (for example, key-*up* and mouse-*down*) or modifiers (for example, pressing the Control key and a character key simultaneously) that event-handling code often has to test for. 

Although the AppKit framework also defines touch (`NSTouch`) objects and gesture events, these events are appropriate only for laptops or desktop computers with supported trackpads. In the OS X version of your app, it’s important to handle events from as many types of input devices as possible.

The basic techniques for handling events on each platform are similar. For example, a custom view must opt in to handle events. Then, to handle an event, a custom view must implement one or more methods declared by the responder class of the app framework. 

Common examples of iOS event handlers that you need to replace in OS X are `UITapGestureRecognizer` and `UILongPressGestureRecognizer`. `UITapGestureRecognizer` can be replaced in OS X with the `mouseUp:` method of `NSResponder` or subclasses, while UILongPressGestureRecognizer is typically replaced by a right-click event, with a menu displayed using the `menuForEvent:` method of `NSView`. 

You can do some event-handling tasks in OS X apps that have no parallel in iOS apps, such as tracking the movement of the pointer and monitoring incoming events in your own app or another app.

For more information about handling events in OS X apps, see *[Cocoa Event Handling Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/EventOverview/Introduction/Introduction.html#//apple_ref/doc/uid/10000060i)*.



在OS X 中处理事件与在iOS应用程序中处理事件有很大的不同，主要是因为每个平台上的用户事件类型不同。如果你的 iOS应用程序有自己的事件处理，当你将应用程序迁移到OS X时，你将不得不重写大量的事件处理代码。

与定义触摸事件和运动事件的iOS不同，OS X定义了鼠标事件、键盘事件、触摸板事件、平板电脑事件和 跟踪区域事件。所有这些事件类型都与可以连接到计算机的外设有关。此外，大多数事件类型，包括事件处理代码经常要测试的阶段(例如， `key-up` and `mouse-down`) 或修饰符 (例如，同时按下Control键和字符键)。

虽然 AppKit 框架 还定义了触摸(`NSTouch`)对象和手势事件，但这些事件 仅适用于支持 trackpad 的笔记本电脑或台式电脑。在应用程序的 OS X版本中，处理来自 尽可能多的 输入设备的事件非常重要。

处理每个平台上的事件的基本技术是类似的。例如，自定义视图必须选择处理事件。然后，为了处理一个事件，自定义视图必须实现一个或多个由app框架的responder类声明的方法。

你需要在OS X中替换的iOS事件处理程序的常见例子是 `UITapGestureRecognizer` 和 `UILongPressGestureRecognizer` 。 `UITapGestureRecognizer` 可以用 `NSResponder` 或子类的 `mouseUp:` 方法在OS X中替换，而 `UILongPressGestureRecognizer` 通常被一个右击事件替换，菜单显示使用 `menuForEvent:` 方法的 `NSView` 。

你可以在OS X应用程序 中完成一些iOS应用程序中 没有的事件处理任务，比如跟踪指针的移动 和 监控自己或其他应用程序中的传入事件。

有关在OS X应用程序中处理事件的更多信息，请参见 *[Cocoa Event Handling Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/EventOverview/Introduction/Introduction.html#//apple_ref/doc/uid/10000060i)*。 



***

### 2、Windows 窗口

At a basic level, windows in AppKit play the same role they do in UIKit: They present graphical content in a rectangular area of the screen, they are at the root of a view hierarchy, they coordinate drawing operations, and they help to distribute events. In most other respects, windows and the framework objects that represent them in OS X and in iOS are different. Here are a few key differences between iOS and OS X windows. 

- Most iOS apps have only one fixed size window. In contrast, an OS X app can have multiple windows of varying sizes and styles, and those windows share the screen space with the windows of other apps. Unlike an iOS window, which has no visual adornments, an OS X window usually displays a title and can include controls for moving, closing, resizing, and minimizing the window.

- An OS X app can have one or more main or secondary windows (an app that has multiple main windows is typically a document-based app). A main window is the principal focus of user events and presents an app’s data. A secondary window generally serves an auxiliary function and might provide additional control over the data presented in the main window. Secondary windows are often panels—that is, instances of the `NSPanel` class.

  

- In UIKit, the `UIWindow` class is a subclass of `UIView`, but in AppKit, the `NSWindow` class is a subclass of `NSResponder`. Consequently, windows in AppKit are not backed by Core Animation layers as they are in UIKit. This difference means that you have to perform animation explicitly, at the view level. For a summary of Core Animation differences, see [Table 7-3](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW15).

  

在基本层面上，AppKit中的窗口扮演着与UIKit中相同的角色: 它们在屏幕的矩形区域中显示图形内容，它们位于视图层次结构的根部，它们协调绘图操作，并且它们帮助分发事件。在大多数其他方面，windows和它们的框架对象，在OS X和iOS中表示是不同的。以下是iOS和OS X 窗口之间的一些关键区别。

- 大多数iOS应用程序只有一个固定大小的窗口。相比之下，一个OS X 应用程序可以有多个不同大小和风格的窗口，这些窗口与其他应用程序的窗口共享屏幕空间。与没有视觉装饰的iOS窗口不同，OS X 窗口通常显示一个标题，可以包含移动、关闭、调整大小和最小化窗口的控件。

- OS X 应用程序可以有 一个或多个主窗口或辅助窗口(具有多个主窗口的应用程序 通常是基于文档的应用程序)。

  主窗口是用户事件的主要焦点，并显示应用程序的数据。

  辅助窗口通常具有辅助功能，可以对主窗口中的数据提供 额外的控制。辅助窗口通常是窗格(panels) ---- 也就是说，`NSPanel` 类的实例。

- 在UIKit中，`UIWindow` 类是 `UIView` 的子类，但在AppKit中，` NSWindow` 类是` NSResponder` 的子类。因此，AppKit中的窗口 不像在UIKit中那样 得到核心动画层的支持。这个区别意味着，你必须在视图级 显式地执行动画。有关核心动画差异的摘要，请参阅  [Table 7-3](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW15)。



***
### 3、Menus 菜单

Most OS X apps have a much larger command set than comparable iOS apps have. In OS X, apps use the systemwide menu bar to present these commands, whereas iOS apps present commands in UI elements such as toolbars, buttons, table views, and switches. As you migrate your iOS app to OS X, think about the best way to move many of the commands invoked by these elements into menus.

**Note:** OS X apps can have pop-up lists, contextual menus, and menu-like controls such as the combo box in addition to menus in the menu bar.

By default, an OS X app’s menu bar has some standard menus—such as the Apple menu, the app menu, File, Edit, and so on—and each of these menus contains standard menu items. When you create an OS X app project in Xcode, the nib-file template gives you a  `starter set`  of menus for your menu bar; remove and add menus and menu items to customize this set for your app. 

Menu items use the target-action model to send commands (that is, *action messages*) to appropriate objects in the app. Some of the template menu items prewire their target and action properties. You can assign key equivalents to menu items that are most frequently invoked.

To learn more about menus, read *[Application Menu and Pop-up List Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/MenuList/MenuList.html#//apple_ref/doc/uid/10000032i)*. 



大多数OS X 应用程序 的命令集 都比同类iOS应用程序大得多。在 OS X 中，应用程序使用系统范围的菜单栏 来显示这些命令，而iOS 应用程序在UI元素中显示命令，如工具栏、按钮、表视图和开关。当你将 iOS应用程序迁移到OS X时，请考虑将这些元素调用的许多命令 移动到 菜单中的最佳方式。

**注意:** OS X 应用程序除了 菜单栏中的菜单外，还可以有弹出列表、上下文菜单和类似菜单的控件，如组合框。

默认情况下，OS X应用程序的菜单栏有一些标准菜单，比如苹果菜单、应用程序菜单、文件、编辑等，而且每个菜单都包含标准菜单项。当你在 Xcode 中创建一个 OS X 应用程序项目时，nib-file 模板会为你的菜单栏提供一个` 初始菜单集（`starter set`）”；删除和添加菜单和菜单项，以自定义这一套为你的应用程序。

菜单项 使用 目标-操作模型 发送命令(即*操作消息*) 到应用程序中适当的对象。一些模板菜单项 预先连接了它们的目标 和操作属性。可以将 键等价物分配给最频繁调用的菜单项。

要了解更多关于菜单的信息，请阅读 *[Application Menu and Pop-up List Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/MenuList/MenuList.html#//apple_ref/doc/uid/10000032i)*。

***

### 4、Documents 文档

A document-based app enables users to create, edit, save, and open multiple documents, such as word-processing or spreadsheet documents. 

iOS provides a model for document-based apps through the abstract base class `UIDocument`. When you adopt the `UIDocument` approach, your app gets significant behavior with minimal coding effort on your part, including integration with iCloud storage, background reading and writing of data, and an optimized auto-save model. 

OS X takes support for documents a step farther, defining an extensive architecture for document-based apps, because this content model is common for the platform. The OS X document architecture is closely based on the Model-View-Controller design pattern. Each document has its own main window and can have secondary windows for auxiliary functions. When you use Xcode to develop a document-based app, you get appropriately configured nib files and stub source files for the `NSDocument` subclass used to manage your documents.

To learn more about the document architecture, read *[Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)*. 



基于文档的应用程序 允许用户创建、编辑、保存和打开多个文档，如文字处理或电子表格文档。

iOS通过抽象基类 `UIDocument` 为基于文档的应用程序提供了一个模型。当你采用 `UIDocument` 方法时，你的应用程序通过你这方面的最小编码工作 获得了显著的性能，包括与 iCloud存储的集成、数据的后台读写 和 优化的自动保存模型。

OS X 对文档的支持更进一步，为基于文档的应用程序定义了广泛的架构，因为这种内容模型在平台上很常见。OS X文档体系结构紧密地基于 模型-视图-控制器 设计模式。每个文档都有自己的主窗口，可以有辅助功能的辅助窗口。

当你使用Xcode开发一个基于文档的应用程序时，你将获得用于管理文档的 `NSDocument ` 子类的适当配置的nib文件和存根源文件。

要了解更多关于文档架构的信息，请阅读  *[Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)*。



***
### 5、Views and Controls 视图和控制

Some of the ready-to-use views that AppKit offers are similar to UIKit views in form, function, and interface. But even with these views, there are differences you should be aware of when migrating your code. Other UIKit views have no counterpart in AppKit because they would not work well in OS X; for these views, you must find a suitable alternative. For example, AppKit uses the `NSBrowser`class to manage the display of hierarchical information; in contrast, an iOS app would use navigation controllers. Some views that seem similar on both platforms have different inheritance characteristics. For example, in iOS `UITableView` inherits from the `UIScrollView` class, whereas in OS X `NSTableView` inherits from `NSControl`. 

Although the view base classes—that is, `UIView` and `NSView`—are somewhat similar on both platforms, there are some fundamental differences between them. 

- **Core Animation layers.** iOS views are layer backed by default. iOS apps typically manipulate views by changing properties of the view. In OS X, an app must opt in to make its views layer-backed. Consequently, it is more common for AppKit views to perform the same manipulations in their `drawRect:` method. [Table 7-3](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW15) gives more information about differences related to Core Animation layers.
- **Default coordinate system.** The default coordinate systems used in drawing operations are different in iOS and OS X. In iOS, the drawing origin is at the upper-left corner of a view; in OS X, the drawing origin is at the lower-left corner of a view. See [Graphics, Drawing, and Printing](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW14) for additional information.
- **Use of cells for controls.** Because AppKit views can incur significant overhead, some AppKit controls use cells (that is, `NSCell` objects) as a lightweight alternative to views. A cell holds the information that its control needs in order to send an action message; a cell also draws itself when commanded by its control. Cells make possible controls such as a matrix object and a table view that have two-dimensional arrays of active subregions. 
- **Drawing in relation to view bounds.** `UIView` subviews can draw outside their view bounds. By default, `NSView` subviews clip to view bounds, which is typically the desired behavior. 

For functional descriptions of the views and controls available in OS X, along with information on how to use them in your app, see *OS X Human Interface Guidelines*. To learn about the common characteristics and behavior of AppKit views, see *[View Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaViewsGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40002978)*.



AppKit 提供的一些即时可用的视图在形式、功能和接口上类似于 UIKit 视图。但是，即使使用这些视图，在迁移代码时也应该注意到一些差异。其他 UIKit 视图 在 AppKit 中没有对应的，因为它们在 OS X 中不能很好地工作；对于这些视图，你必须找到一个合适的替代方案。例如，AppKit使用 `NSBrowser ` 类来管理层次信息的显示；相比之下，iOS应用程序将使用导航控制器。在两个平台上看起来相似的一些视图具有不同的继承特征。例如，在iOS中 `UITableView` 继承自 `UIScrollView` 类，而在OS X中 `NSTableView`继承自 `NSControl ` 类。

虽然视图基类——也就是`UIView`和 `NSView` ——在两个平台上有点类似，但它们之间有一些基本的区别。

- **核心动画层。**  iOS视图默认支持图层（layer ）。iOS应用程序 通常通过改变视图的属性来操作视图。在OS X中，应用程序必须选择让它的视图支持分层。因此，AppKit视图在其  `drawRect: ` 方法中执行相同的操作更为常见。[表7-3](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#// doc/uid/TP40001067-CH8-SW15)给出了更多关于核心动画层差异的信息。

- **默认的坐标系统。** 在iOS和OS x中，绘图操作使用的默认坐标系统不同。在iOS中，绘图原点位于视图的左上角; 在OS X中，绘图原点位于视图的左下角。参见 [Graphics, Drawing, and Printing](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW14) 。

- **使用cells作为控件。** 因为AppKit 视图会产生大量的开销，一些 AppKit 控件使用cells (即`NSCell` 对象)作为视图的轻量级替代。cells 持有其控件发送操作消息所需的信息；一个cell 在它的控制下也会绘制自己。Cells 使矩阵对象 和 表视图等控件成为可能，这些控件具有活动子区域的二维数组。
- **根据视图边界绘制。** `UIView` 子视图可以绘制在其视图范围之外。默认情况下，`NSView` 子视图剪辑到视图边界，这通常是期望的行为。

有关OS X中可用的视图和控件的功能描述，以及如何在应用程序中使用它们的信息，请参见 *OS X Human Interface Guidelines*。要了解AppKit视图的常见特征和行为，请参见 *[View Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaViewsGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40002978)*。



***
### 6、File System  文件系统

Many OS X apps let users locate files and directories in the file system, save files to specific file-system locations, open files, and do other file-system operations. An iOS app, on the other hand, must perform all file-reading and file-writing operations within the confines of its sandbox. In OS X v10.7 and later, Mac apps can also be  `sandboxed,`  and this can restrict the file-system operations they can perform (for more information, see [App Sandbox](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html#//apple_ref/doc/uid/TP40001067-CH9-SW3)). Nonetheless, even these apps might have to be prepared to open and save files in the file system as the user directs (assuming that the user has the necessary file permissions). 

An OS X app enables these file-system behaviors largely through the Open and Save panels (implemented by the AppKit classes `NSOpenPanel` and `NSSavePanel`). Through instances of these objects, the app can present file-system browsers to users, prevent files it doesn’t recognize from being selected, and obtain users’ choices. You can also attach custom accessory views to these browsers. 

In addition to making use of the Open and Save panels, your app can call methods of the `NSFileManager` and `NSWorkspace` classes for many file-system interactions. `NSFileManager` lets your app create, move, copy, remove, and link file-system items. It also offers other capabilities, such as discovering directory contents, and getting and setting file and directory attributes. Operations of the `NSWorkspace` class augment those of `NSFileManager`; these operations include launching apps, opening specific files, mounting local volumes and removable media, setting the Finder information of files and directories, and tracking file-system changes. (Sandboxed apps can’t use `NSWorkspace` in many situations.)

If your iOS app writes and reads files in the `Documents` directory, it uses the `NSSearchPathForDirectoriesInDomains` function to get the proper directory path in the app sandbox. In OS X, you use the `URLsForDirectory:inDomains:` method of the `NSFileManager` class instead; for this platform you might need to specify domains other than the user domain, and standard directory locations other than `Documents`. For example, your app might want to write or read data in the user’s home directory, in `Library/Application Support`.



**Note:** OS X apps should always store files they create in an appropriate location in the user’s `Library` directory; they should not store files in `~/Documents` unless the user selects that location. 



To learn more about file-system domains, standard file-system locations, filename extensions, BSD file permissions, AppKit facilities for managing file-system operations, and other information related to the OS X file system, read *[File System Programming Guide](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010672)*. 



许多 OS X 应用程序允许用户在文件系统中定位文件和目录，将文件保存到特定的文件系统位置，打开文件，以及执行其他文件系统操作。另一方面，iOS 应用程序必须在 沙盒范围内 执行所有文件读取和文件写入操作。在 OS X v10.7 后来，Mac 的应用程序也可以 沙盒化，这可以限制他们可以执行文件系统操作(有关更多信息,请参见 [App Sandbox](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html#//apple_ref/doc/uid/TP40001067-CH9-SW3) )。尽管如此，即使是这些应用程序也可能需要根据用户的指示，在文件系统中打开和保存文件(假设用户具有必要的文件权限)。

OS X应用程序主要通过 Open and Save panels (由AppKit类`  NSOpenPanel ` 和`  NSSavePanel ` 实现) 来实现这些文件系统行为。通过这些对象的实例，应用程序可以将 文件系统浏览器（file-system browsers） 呈现给用户，防止不识别的文件被选中，并获得用户的选择。你还可以将自定义的附件视图 附加到这些浏览器。



除了使用 打开和保存面板，你的应用程序还可以为许多文件系统交互调用`  NSFileManager ` 和`  NSWorkspace ` 类的方法。

`  NSFileManager ` 让你的应用程序创建、移动、复制、删除和链接文件系统项。它还提供其他功能，如发现目录内容、获取和设置文件和目录属性。

` NSWorkspace` 类的操作扩充了 ` NSFileManager` 类的操作；这些操作包括 启动应用程序、打开特定文件、装入本地卷和可移动媒体、设置文件和目录的查找信息以及跟踪文件系统更改。(沙箱应用程序在很多情况下不能使用`NSWorkspace`。)



如果你的iOS应用程序在 “文档” 目录下读写文件，它会使用 `NSSearchPathForDirectoriesInDomains` 函数来获取应用沙箱中正确的目录路径。

在OS X中，可以使用`NSFileManager` 类的 `URLsForDirectory:inDomains:`方法；对于这个平台，你可能需要指定用户域之外的域，以及“文档”之外的标准目录位置。例如，你的应用程序可能想要在用户的主目录 `Library/Application Support` 中写入或读取数据。

**注意:** OS X应用程序应该总是 将它们创建的文件存储在用户的 `Library` 目录的适当位置；它们不应该将文件存储在 `~/Documents` 中，除非用户选择该位置。

要了解更多关于文件系统域、标准文件系统位置、文件名扩展、BSD文件权限、用于管理文件系统操作的AppKit工具，以及与OS X文件系统相关的其他信息，请阅读  *[File System Programming Guide](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010672)*。



***
### 7、Graphics, Drawing, and Printing  图表、画图和打印

There are many parallels between the graphics and drawing APIs of AppKit and those of UIKit, as shown in Table 7-2. Both frameworks have classes whose instances represent images, colors, and fonts. Both have classes for drawing Bezier paths and categories for drawing strings. Both have functions for stroking and filling rectangles. Both have programmatic facilities for obtaining and transforming graphics contexts of various types. In some cases, you can migrate code that uses UIKit methods and functions to corresponding AppKit methods and functions with little more than name changes.

AppKit 的图形和绘图api 与UIKit的图形和绘图api 有很多相似之处，如表7-2所示。这两个框架都有一些类，它们的实例表示图像、颜色和字体。它们都有用于绘制 Bezier 路径的类 和用于绘制字符串的类别。两者都有描边和填充矩形的功能。它们都具有用于获取和转换各种类型的图形上下文的程序化功能。在某些情况下，你可以将使用 UIKit 方法和函数的代码，迁移到相应的AppKit方法和函数，只需更改名称即可。



|                       | iOS (UIKit)                           | OS X (AppKit)                                         | Comments                                                     |
| :-------------------- | :------------------------------------ | :---------------------------------------------------- | :----------------------------------------------------------- |
| **Images**            | `UIImage`                             | `NSImage`                                             | `NSImage` can render an image from source data appropriate to an output destination. <br> NSImage 可以从元数据渲染图片到制定的输出 |
| **Colors**            | `UIColor`                             | `NSColor`, `NSColorSpace`, color-related view classes | Apps can use `NSColorSpace` to more precisely define the colors represented by `NSColor`objects. <br>应用程序可以使用`NSColorSpace`更精确地定义由`NSColor`对象表示的颜色。 |
| **Bezier paths**      | `UIBezierPath`                        | `NSBezierPath`                                        |                                                              |
| **Graphics contexts** | Functions declared in `UIGraphics.h`. | `NSGraphicsContext`                                   |                                                              |
| **PDF**               | Functions declared in `UIGraphics.h`. | PDF Kit framework                                     | OS X provides richer PDF support than iOS does.    <br>    OS X提供了比iOS更丰富的PDF支持。       |
| **Printing**          | Multiple classes                      | Multiple classes                                      | The classes and techniques for printing in each platform are completely different. <br>每个平台中用于打印的类和技术是完全不同的。 |

On both platforms, you can call Core Graphics functions when the framework-supplied methods or functions don’t suffice for a particular purpose.

The drawing model for AppKit views is nearly identical to the drawing model for UIKit views, with one exception. UIKit views use a coordinate system where the origin for windows and views is in the upper-left corner by default, with positive axes extending down and to the right. In AppKit, the default origin point is in the bottom-left corner and the positive axes extend up and to the right. This is the *default coordinate system* of AppKit, which happens to coincide with the default coordinate system of Core Graphics. To change the default origin of an Appkit view, override the view’s `isFlipped` method and return `YES`. The following types of views are are already flipped by default: `NSButton, NSScrollView, NSSplitView, NSTabView,` and `NSTableView`. 

**Note:** Whereas UIKit uses Core Graphics data types for rectangles, points, and other geometric primitives, AppKit uses its own defined types for the same purpose—for example, `NSRect` and `NSPoint`.

For information about graphics and drawing in OS X, see *[Cocoa Drawing Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaDrawingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003290)*. To learn more about printing in OS X, see *[NSPrintInfo Class Reference](https://developer.apple.com/documentation/appkit/nsprintinfo)*.





在这两个平台上，当框架提供的方法或函数不能满足特定目的时，可以调用核心图形函数。
AppKit视图的绘图模型几乎与 UIKit视图的绘图模型相同，但有一个例外：
UIKit视图使用一个坐标系统，其中窗口和视图的原点默认位于左上角，正轴向下延伸到右边。
在AppKit中，默认原点位于左下角，正轴向上并向右延伸。这是AppKit的默认坐标系统，与Core Graphics的默认坐标系统是一致的。
要更改Appkit视图的默认原点，请覆盖视图的 `isFlipped` 方法并返回 `YES`。以下类型的视图在默认情况下已经被翻转: `NSButton, NSScrollView, NSSplitView, NSTabView,` 和 `NSTableView`。

**注意:** UIKit为矩形、点和其他几何原语 使用核心图形数据类型，而 AppKit 为同样的目的 使用自己定义的类型——例如， `NSRect` 和 `NSPoint`。

有关OS X中的图形和绘图的信息，请参阅  *[Cocoa Drawing Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaDrawingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003290)*。有关在OS X中打印的更多信息，请参见  *[NSPrintInfo Class Reference](https://developer.apple.com/documentation/appkit/nsprintinfo)*。



***
### 8、Text 文本

AppKit offers apps a sophisticated system for performing text-related tasks ranging from simple text entry to custom text layout and typesetting. Because the Cocoa text system is based on the Core Text framework and provides a comparable set of behaviors, Cocoa apps rarely need to use Core Text directly. 

The native text support of UIKit is limited. Still there is some correspondence between that support and the support offered by AppKit—namely, text views, text fields, font objects, string drawing, and HTML content. If your iOS app uses Core Text to draw and manage fonts and text layout, you can migrate much of that code to your OS X app. 

For an introduction to the text system of AppKit, see *[Cocoa Text Architecture Guide](https://developer.apple.com/library/archive/documentation/TextFonts/Conceptual/CocoaTextArchitecture/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009459)*.



AppKit 为应用程序提供了一个复杂的系统，用于执行与文本相关的任务，从简单的文本输入到自定义文本布局和排版。因为Cocoa文本系统是基于核心文本框架（ Core Text framework ）的，并且提供了一组可比较的行为，所以Cocoa应用很少需要直接使用核心文本。

UIKit 的本地文本支持是有限的。但是，这种支持与 AppKit 提供的支持之间 仍然存在一些对应关系，即文本视图、文本字段、字体对象、字符串绘图和HTML内容。如果你的 iOS应用程序 使用核心文本来 绘制和管理字体和文本布局，你可以将大部分代码迁移到你的OS X 应用程序。

有关AppKit的文本系统的介绍，请参阅 *[Cocoa Text Architecture Guide](https://developer.apple.com/library/archive/documentation/TextFonts/Conceptual/CocoaTextArchitecture/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009459)*。



***
### 9、Table Views 表格视图

Table views in AppKit are structurally different from table views in UIKit. In UIKit, a table view has any number of rows, and one or more sections but it has only one column. In AppKit, a table view can have any number of rows and columns (and there is no formal notion of sections). An iOS app typically uses a series of UIKit table views, each in their own screen, to present a hierarchical data set. An OS X app, on the other hand, typically uses a single AppKit table view to present all of a data set at the same time. 

The structures of these table views differ because of the differences between the platforms. Table views, perhaps the most versatile UI object in iOS, are ideal for displaying data on a smaller screen. Apps use them to navigate hierarchies of data, to present master-detail relationships among data, to facilitate quick retrieval of indexed items, and to serve as lists from which users can select options. 

Table views in OS X exist largely to present tabular data in a larger window. AppKit provides other UI objects that are suitable for some of the roles played by UIKit table views—for example, lists (pop-up lists, checkboxes, and radio buttons) and navigation of data hierarchies (browsers and outline views). Consequently, when you migrate your app’s table views to OS X, you should first consider whether another AppKit view better suits your app’s needs than a table view. 

Table views in AppKit are `NSTableView` objects. Cells occupy the region where the rows and columns of the table view intersect. A table view’s cells can be based on `NSCell` objects or, in OS X v10.7 and later, `NSView` objects. View-based table views are the preferred alternative. Populating AppKit table views is similar to populating UIKit table views: A data source is queried for the number of rows in the table view and is then asked for the value to put into each cell. Table views in OS X have these other parallels with UIKit table views: 

- **Cell reuse**. The delegate of a view-based table view can return a view to use for a cell; the view has an identifier. On the first request, the table view loads this view from a nib file and then caches the view for subsequent requests. 
- **Animated operations**. Both `NSCell`-based and `NSView`-based table views have methods for inserting, removing, and moving rows and items, optionally with an animation.

`NSOutlineView`, a subclass of `NSTableView`, has many of these same behaviors. For more information about creating and using table views, see *[Table View Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/TableView/Introduction/Introduction.html#//apple_ref/doc/uid/10000026i)*. [NSStackView](https://developer.apple.com/documentation/appkit/nsstackview)is an Auto Layout–based view that creates and manages the constraints needed to create horizontal or vertical stacks of views. For more information about creating and using stack views, see *[View Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaViewsGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40002978)*. 



AppKit中的表视图与UIKit中的表视图在结构上是不同的。在UIKit中，一个表视图有任意数量的行，一个或多个section，但它只有一个列。在AppKit中，一个表视图可以有任意数量的行和列(没有分段 sections 的正式概念)。iOS 应用程序通常使用一系列的UIKit表视图，每个视图都在自己的屏幕上，来呈现层次数据集。而OS X 应用程序通常使用一个 AppKit 表视图来同时呈现所有的数据集。

由于平台之间的不同，这些表视图的结构也不同。表视图可能是iOS中最通用的 UI对象，非常适合在较小的屏幕上显示数据。应用程序使用它们来 导航数据的层次结构，显示数据之间的主从关系，方便快速检索索引项，并作为用户可以从中选择选项的列表。

OS X中的表视图主要用于在较大的窗口中显示表格数据。AppKit 提供了其他UI对象，这些对象适合于 UIKit表视图 所扮演的一些角色——例如，列表(弹出列表、复选框和单选按钮) 和数据层次结构的导航(浏览器和大纲视图)。因此，当你将应用程序的表视图迁移到 OS X 时，首先应该考虑另一个 AppKit 视图是否比表视图更适合应用程序的需要。

AppKit中的表视图是 `NSTableView` 对象。单元格占据表视图的行和列相交的区域。一个表视图的单元格可以基于 `NSCell` 对象，也可以基于OS X v10.7以及之后的 `NSView` 对象。基于视图的表视图是更好的选择。填充AppKit 表视图类似于填充 UIKit表视图:数据源查询表视图中的行数，然后询问要放入每个单元格的值。OS X 中的表视图与UIKit表视图有其他相似之处:

- **Cell 重用**。基于视图的表视图的委托可以返回用于单元格的视图；视图有一个标识符。对于第一个请求，表视图从nib文件加载该视图，然后为后续请求缓存该视图。
- **动画操作**。基于`NSCell` 和基于 `NSView` 的表视图都有用于插入、删除和移动行和项的方法，可以选择使用动画。

`NSOutlineView` 是 `NSTableView` 的子类，有很多相同的行为。有关创建和使用表视图的更多信息，请参见  *[Table View Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/TableView/Introduction/Introduction.html#//apple_ref/doc/uid/10000026i)*。 [NSStackView](https://developer.apple.com/documentation/appkit/nsstackview) 是一个基于自动布图的视图，用于创建和管理创建水平或垂直视图堆栈所需的约束。有关创建和使用堆栈视图的更多信息，请参见  *[View Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaViewsGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40002978)*。





***
### 10、Other Interface Differences 其它接口差异

When migrating your app, you should keep in mind other technology differences between UIKit and AppKit; Table 7-3 summarizes these differences. 

在迁移你的应用程序时，你应该记住UIKit和AppKit之间的其他技术差异; 表7-3总结了这些差异。



| Difference                         | Discussion                                                   |
| :--------------------------------- | :----------------------------------------------------------- |
| Core Animation layers              | Every drawing surface in OS X can be backed by a Core Animation layer (as in iOS), but an app has to explicitly request this backing for its views. Once this request is made, animation is supported for changes in the properties of the views. In AppKit you don’t get the same easy-to-use view-based animation support that you do in UIKit.AppKit also includes the animation features of layer hosting, animation proxies, and classes for animating multiple windows and views.For information about the animation capabilities and features of OS X, see *[Animation Overview](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/Animation_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004952)*. <br> OS X中的每个绘图表面 都可以由一个核心动画层(如iOS)来支持，但是应用程序必须明确地请求这个视图的支持。一旦发出此请求，就会支持对视图属性进行动画更改。在AppKit中，你不能得到和在UIKit中一样的易于使用的 基于视图的动画支持。AppKit还包括 层托管、动画代理 和 用于 动画多个窗口和视图的类 的动画特性。有关OS X的动画功能和特性的信息，请参阅 *[Animation Overview](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/Animation_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004952)* |
| Target-action model                | Target-action in AppKit defines only one form for method signatures, unlike UIKit, which has three forms. Controls in AppKit send their action messages in response to a discrete user action, such as a mouse click; the notion of multiple actions associated with multiple interaction phases does not exist on the platform. However, a control composed of multiple cells can send a different action message for each cell.For more information about controls and the target-action model in OS X apps, see *[Control and Cell Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ControlCell/ControlCell.html#//apple_ref/doc/uid/10000015i)*. <br> AppKit 中的 Target-action 只为方法签名 定义了一个表单，而 UIKit 有三个表单。AppKit 中的控件发送它们的动作消息，来响应离散的用户动作，例如鼠标单击; 与多个交互阶段相关联的多个操作的概念，在平台上并不存在。但是，由多个单元组成的控件 可以为每个单元发送不同的操作消息。有关 OS X 应用程序中的控件 和 目标-操作模型的更多信息，请参见 *[Control and Cell Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ControlCell/ControlCell.html#//apple_ref/doc/uid/10000015i)*. |
| Responder chain                    | The responder chain in OS X differs slightly from the responder chain in iOS. As of OS X v10.10, view controllers are added as part of the chain for either user events or action messages. In earlier versions of OS X, view controllers are *not* part of the chain. For action messages, the responder chain in OS X includes window controllers and the view hierarchies of key windows and main windows. AppKit also uses the responder chain for cooperative error handling.To learn more about the responder chain, see *[Cocoa Event Handling Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/EventOverview/Introduction/Introduction.html#//apple_ref/doc/uid/10000060i)*. <br> OS X 中的响应链 与iOS中的响应链 略有不同。从OS X v10.10开始，视图控制器 被添加为用户事件 或操作消息链的一部分。在OS X 的早期版本中，视图控制器 **不是** 链的一部分。对于操作消息，OS X 中的响应链 包括窗口控制器 和键窗口 和主窗口的视图层次结构。AppKit还使用响应链进行协作错误处理。要了解更多关于responder chain，见 *[Cocoa Event Handling Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/EventOverview/Introduction/Introduction.html#//apple_ref/doc/uid/10000060i)*。 |
| User preferences                   | In OS X, all preferences belong in your app; there is no separation of preferences between those managed by your app and those managed by the system. OS X has nothing comparable to the Settings bundle used by iOS apps to specify user preferences presented by the Settings app. Instead apps must create a secondary window for the user preferences. Users open this window by choosing Preferences from the app menu. In addition, OS X integrates user preferences into Cocoa bindings and enables command-line access to the underlying defaults system. One commonality is that both AppKit and UIKit apps use the `NSUserDefaults` class to retrieve user preferences. For more information, see *[Preferences and Settings Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/UserDefaults/Introduction/Introduction.html#//apple_ref/doc/uid/10000059i)*. <br> 在OS X中，所有的偏好设置都属于你的应用; 在你的应用程序管理的偏好 和系统管理的偏好之间没有区别。OS X 与iOS应用程序 用于指定设置应用程序所呈现的用户首选项的设置包没有可比性。相反，应用程序必须为用户首选项 创建一个辅助窗口。用户通过选择应用程序菜单中的首选项 来打开此窗口。此外，OS X 将用户首选项集成到 Cocoa绑定中，并支持对底层默认系统的命令行访问。一个共同点是，AppKit 和 UIKit 应用程序都使用 `NSUserDefaults `类来检索用户的首选项。有关更多信息，请参见 *[Preferences and Settings Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/UserDefaults/Introduction/Introduction.html#//apple_ref/doc/uid/10000059i)* |
| Accessor methods versus properties | UIKit makes extensive use of properties throughout its class declarations, but AppKit mostly declares accessor methods instead of properties. <br> UIKit 在它的类声明中大量使用了属性，但是 AppKit 主要声明了访问方法而不是属性。 |



***
## 三、Foundation Framework Differences Foundation框架的差异

A slightly different version of the Foundation framework in iOS is available in OS X. Most of the classes you would expect to be present are available in both versions — for example, both framework versions provide support for managing values, strings, collections, threads, and many other common types of data. There are, however, some technologies that are present in Foundation in OS X but not included in iOS. These technologies are listed in Table 7-4. 

iOS 中 Foundation框架 的一个稍微不同的版本 可以在OS X 使用。大部分你会用到的类，都会出现在两个版本 —— 例如，这两个框架版本提供支持管理值，字符串，集合，线程，以及许多其他常见的类型的数据。然而，有一些技术存在于 OS X的 Foundation中，但不包括在iOS中。表7-4 中列出了这些技术：

| Technology                                          | Notes                                                        |
| :-------------------------------------------------- | :----------------------------------------------------------- |
| Spotlight metadata management <br>                  | Spotlight is a technology for organizing and accessing information on a computer using file metadata. (Metadata is data about a file, rather than the actual file contents.) If you want your app to create Spotlight queries and interact with the results, you use special query and predicate objects.For more information, see *[Spotlight Overview](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/MetadataIntro/MetadataIntro.html#//apple_ref/doc/uid/TP40001268)*.  <br> Spotlight是一种 使用文件元数据组织和访问计算机上的信息的技术。( 元数据是关于文件的数据，而不是实际的文件内容。) 如果您希望您的应用程序创建重点查询并与结果交互，您可以使用特殊的查询和谓词对象。有关更多信息，请参见 *[Spotlight Overview](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/MetadataIntro/MetadataIntro.html#//apple_ref/doc/uid/TP40001268)* 。 |
| Cocoa bindings                                      | Cocoa bindings is a technology that lets you, during development, establish a connection between an item of data encapsulated by a model object and the presentation of that data in a view. It eliminates the need for glue code in the controller layer of an app. For more information, see *[Cocoa Bindings Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaBindings/CocoaBindings.html#//apple_ref/doc/uid/10000167i)*.  <br>Cocoa bindings 是一种允许您在开发期间，在模型对象封装的数据项 和视图中数据的表示之间 建立连接的技术。它消除了在应用程序的控制器层中粘贴代码的需要， 更多信息可参阅 [Cocoa Bindings Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaBindings/CocoaBindings.html#//apple_ref/doc/uid/10000167i) |
| Cocoa scripting (AppleScript)                       | Using certain classes of Foundation along with supporting technology, you can make an app scriptable. A scriptable app is one that responds to commands in AppleScript scripts. To learn more about this technology, see *[Cocoa Scripting Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ScriptableCocoaApplications/SApps_intro/SAppsIntro.html#//apple_ref/doc/uid/TP40002164)*.  <br> 使用特定的基础类和支持技术，你可以使一个应用程序脚本化。可编写脚本的应用程序是响应AppleScript脚本中的命令的应用程序。要了解关于此技术的更多信息，请参见 [Cocoa Scripting Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ScriptableCocoaApplications/SApps_intro/SAppsIntro.html#//apple_ref/doc/uid/TP40002164)。 |
| Distributed objects and port name server management | Distributed objects is an interprocess messaging technology. With distributed objects, an object in an app can send a message to an object in a different Cocoa app in the same network or in a different network. The port name server is an object that provides a port-registration service to distributed objects. For information about this technology, see *[Distributed Objects Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DistrObjects/DistrObjects.html#//apple_ref/doc/uid/10000102i)*.  <br> 分布式对象是一种进程间消息传递技术。使用分布式对象，应用程序中的对象 可以向同一网络 或 不同网络中的 不同Cocoa应用程序中的对象 发送消息。端口名称服务器是一个对象，它为分布式对象提供端口注册服务。有关此技术的信息，请参阅 [Distributed Objects Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DistrObjects/DistrObjects.html#//apple_ref/doc/uid/10000102i) |

The Foundation framework in OS X provides support for both event-driven and tree-based XML processing. The `NSXMLParser` class (also available in iOS) supports the parsing of a stream of XML. In addition, the framework provides the NSXML classes (so called because the names of these classes begin with  `NSXML` ). Instances of these classes represent an XML document as a tree structure of nodes, including elements and attributes. 

For a list of the specific classes that are available in OS X but not in iOS, see the class hierarchy diagram in The Foundation Framework in *[Foundation Framework Reference](https://developer.apple.com/documentation/foundation)*.

OS X 中的 Foundation 框架 同时支持事件驱动 和 基于树的XML处理。`NSXMLParser` 类(在iOS中也可用) 支持XML流的解析。此外，框架还提供了 NSXML类(之所以这么叫是因为这些类的名称以 `NSXML` 开头)。这些类的实例将XML文档表示为节点的树结构，包括元素和属性。

有关OS X中可用但在iOS中不可用的特定类的列表，请参阅Foundation Framework中的类层次关系图  *[Foundation Framework Reference](https://developer.apple.com/documentation/foundation)*。

***
## 四、Differences in the Audio and Video Frameworks 音视频框架的差异

In OS X and iOS the primary framework for audiovisual media is AV Foundation. The programmatic interfaces of the framework are almost the same in each platform. Just about any code you write using the iOS version of the framework should be valid with the OS X version. The presentation of audiovisual media, however, is different on the two platforms—specifically, OS X does not have the Media Player framework.

There are substantial differences between the audio frameworks of iOS and the audio frameworks of OS X. The following are the audio technologies of OS X that are not present in iOS:

- Programmatic interfaces in the Audio Unit framework for creating dynamically loadable plug-ins for audio processing (audio units) and conversion (audio codecs), along with bundled user interfaces for audio units
- Additional built-in audio units and audio codecs, along with additional capabilities in like-named audio units
- Programmatic interfaces in the Core Audio framework for interacting with audio hardware
- Programmatic interfaces in the I/O Kit framework for creating and using audio drivers
- Additional capabilities in the OpenAL framework, such as the ability to record audio and to use multichannel audio and surround sound
- Programmatic interfaces in the Core MIDI framework for music sequencing
- Audio development tools (AU Lab, `auval`, `afconvert`)



**Note:** AV Foundation includes classes for playing and recording audio. These classes are adequate to the audio needs of many apps.



iOS, on the other hand, has audio technologies that are not present in OS X—for example, the Media Player framework, the vibration capabilities of the Audio Toolbox framework, the programmatic interfaces for input clicks, and the audio-session interfaces in the Audio Toolbox and AV Foundation frameworks, including the notions of audio session categories, interruptions, and route changes. 

OS X also offers Quick Time, a legacy set of multimedia technologies for playing, creating, editing, importing, compressing, and streaming media of various types. Quick Time is available in both OS X and Windows systems. 

To learn more about AV Foundation, see *[AVFoundation Programming Guide](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AVFoundationPG/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40010188)*. 



在OS X 和iOS中，视听媒体的主要框架是 AV Foundation。框架的编程接口在每个平台中几乎是相同的。你使用 iOS 版本框架 编写 的任何代码，在OS X版本中都应该是有效的。然而，视听媒体在这两个平台上的表现是不同的——特别是，OS X没有 Media Player  框架。

iOS 的音频框架和 OS X的音频框架有很大的区别，以下是iOS中没有的OS X的音频技术:

- Audio Unit 框架中的编程接口，用于为音频处理(音频单元) 和转换(音频编解码器) 创建可动态加载的插件，以及为音频单元绑定的用户接口；
- 附加的内置音频单元 和 音频编解码器，以及类似命名的音频单元中的附加功能；
- Core Audio 框架中的编程接口，用于与音频硬件进行交互；
-  I/O Kit 框架中的编程接口，用于创建和使用音频驱动程序；
- OpenAL 框架中的附加功能，如录制音频 和使用多通道音频和环绕声的能力；
- Core MIDI框架中的编程接口，用于音乐排序；
- Audio 开发工具（AU Lab, `auval`, `afconvert`）

**注:** AV Foundation 包括播放和录制音频类。这些类足以满足许多应用程序的音频需求。

另一方面，iOS 有 OSX 中没有的音频技术。比如：Media Player 框架， Audio Toolbox 框架的振动功能，Audio Toolbox 和 AV Foundation  框架编程接口 输入点击，包括音频会话的概念范畴，中断，路线的改变。

OS X 还提供了Quick Time，这是一套用于播放、创建、编辑、导入、压缩和各种类型流媒体的传统多媒体技术。Quick Time 在OS X和Windows系统中都可用。

有关AV Foundation的更多信息，请参见  *[AVFoundation Programming Guide](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AVFoundationPG/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40010188)*。



***
## 五、Differences in Other Frameworks Common to Both Platforms 两个平台上共有框架的差异

Table 7-5 lists the key differences in other OS X frameworks from their counterparts in iOS.

表7-5列出了其他 OS X 框架与 iOS框架 的主要区别。

| Framework                       | Differences                                                  |
| :------------------------------ | :----------------------------------------------------------- |
| `AddressBook.framework`         | Contains the interfaces for accessing user contacts. Although it shares the same name, the OS X version of this framework is very different from its iOS counterpart .OS X has no framework for presenting an interface for contacts, whereas iOS does. For more information, see *[Address Book Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AddressBook/AddressBook.html#//apple_ref/doc/uid/10000117i)*. <br> 包含用于访问用户联系人的接口。虽然名称相同，但OS X版本的框架与iOS版本有很大的不同。OS X 没有为联系人提供接口的框架，而iOS有。有关更多信息，请参见 *[Address Book Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AddressBook/AddressBook.html#//apple_ref/doc/uid/10000117i)*。|
| `CFNetwork.framework`           | Contains the Core Foundation Network interfaces. In OS X, the CFNetwork framework is a subframework of an umbrella framework, Core Services. Most of the interfaces, however, are the same for iOS and OS X. For more information, see *[CFNetwork Framework Reference](https://developer.apple.com/documentation/cfnetwork)*. <br> 包含 Core Foundation 网络接口。在OS X中，CFNetwork 框架是伞形框架(核心服务)的子框架。但是，大多数接口对于 iOS 和 OS X 是相同的。 |
| `CoreGraphics.framework`        | Contains the Quartz interfaces. You can use Quartz to create paths, gradients, shadings, patterns, colors, images, and bitmaps in exactly the same way you do in iOS. The OS X version of Quartz has features not present in iOS, including PostScript support, image sources and destinations, Quartz Display Services support, and Quartz Event Services support. In OS X, the Core Graphics framework is a subframework of the Application Services umbrella framework and is not a top-level framework, as it is in iOS. For more information, see *[Quartz 2D Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html#//apple_ref/doc/uid/TP30001066)*. <br> 包含 Quartz 接口。您可以使用 Quartz创建路径、渐变、阴影、图案、颜色、图像和位图，其方式与在iOS中完全相同。Quartz 的OS X 版本具有iOS中没有的功能，包括 PostScript支持、图像源和目的地、Quartz显示服务支持和Quartz事件服务支持。在OS X中，核心图形(Core Graphics)框架是 Application Services 伞形框架的子框架，而不是iOS中的顶层框架。有关更多信息，请参见 *[Quartz 2D Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html#//apple_ref/doc/uid/TP30001066)*|
| `EventKit.framework`            | Provides classes for accessing and manipulating calendar events and reminders. The iOS version does not include reminder items. <br> 提供用于访问 和操作日历事件和提醒的类。iOS版本不包含提醒项目。 |
| `GameKit.framework`             | Provides APIs that help you incorporate Game Center, peer-to-peer connectivity, and in-game voice chat into your game. Some of the classes that present UI are different on iOS and OS X. <br> 提供api，帮助您将游戏中心、对等连接 和 游戏内语音聊天 合并到您的游戏中。在iOS和OS X上呈现 UI 的一些类是不同的。|
| `GLKit.framework`               | Provides functions and classes that reduce the effort required to create new shader-based apps or to port existing apps that rely on fixed-function vertex or fragment processing provided by earlier versions of OpenGL ES or OpenGL. The iOS version includes classes that simplify the creation of OpenGL ES-aware views and view controllers. In OS X, `NSOpenGLView` class subsumes the `GLKView` and `GLKViewController` classes in iOS. <br> 提供一些函数和类，这些函数和类 可以减少 创建新的基于着色器的应用程序，或移植依赖于 固定功能顶点或片段处理的 现有应用程序所需的工作。iOS版本包含了简化 OpenGL 感知视图 和视图控制器创建的类。在OS X中，`NSOpenGLView` 类包含了iOS中的 `GLKView` 和 `GLKViewController`类。 |
| `OpenGL.framework`              | OS X uses OpenGL instead of the OpenGL ES framework used in iOS. This fuller-featured version of OpenGL is intended for desktop systems. The programmatic interface of OpenGL is much larger than the one for OpenGLES. OpenGL has many extensions that are not available in the embedded version of the framework. For information about the OpenGL support in OS X, see *[OpenGL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html#//apple_ref/doc/uid/TP40001987)*. <br> OS X 使用 OpenGL ，而非iOS中使用的 OpenGL ES 框架。这个功能全面的OpenGL 版本是为桌面系统设计的。OpenGL 的编程接口比 OpenGLES 的要大得多。OpenGL 有许多扩展，这些扩展在框架的嵌入式版本中是不可用的。有关OS X中OpenGL支持的信息，可参阅 *[OpenGL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html#//apple_ref/doc/uid/TP40001987)* |
| `QuartzCore.framework`          | Contains the Core Animation, Core Image, and Core Video interfaces. Most of the Core Animation interfaces are the same for OS X and iOS. However, the iOS version of the framework lacks the API support for layout constraints and Core Image filters found in the OS X version. For more information, see *Quartz Core Framework Reference*. <br> 包含Core Animation、Core Image 和 Core Video 接口。大多数的核心动画界面对 OS X和iOS 是相同的。然而，该框架的 iOS版本 缺乏 OS X 版本中对布局约束 和核心图像过滤器的API支持。有关更多信息，请参见 *Quartz Core Framework Reference* |
| `Security.framework`            | Contains the security interfaces. Its OS X version includes more capabilities and programmatic interfaces. It has authentication and authorization interfaces and supports the display of certificate contents. In addition, its keychain interfaces are more comprehensive than the ones used in iOS. For information about the security support in OS X, see *[Security Overview](https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP30000976)*. <br> 包含安全接口。它的OS X版本包含了更多的功能和编程接口。它具有身份验证和授权接口，并支持显示证书内容。此外，它的密钥链接口比iOS中使用的更全面。有关OS X中的安全支持的信息，请参阅 [Security Overview](https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP30000976) |
| `SystemConfiguration.framework` | Contains networking interfaces. The OS X version contains the complete interfaces, not just the reachability interfaces you find in iOS. For more information, see *[System Configuration Programming Guidelines](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/SystemConfigFrameworks/SC_Intro/SC_Intro.html#//apple_ref/doc/uid/TP40001065)*.<br>  包含网络接口。OS X版本包含了完整的接口，而不仅仅是iOS中的 reachability 接口。有关更多信息，请参见 [System Configuration Programming Guidelines](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/SystemConfigFrameworks/SC_Intro/SC_Intro.html#//apple_ref/doc/uid/TP40001065) |