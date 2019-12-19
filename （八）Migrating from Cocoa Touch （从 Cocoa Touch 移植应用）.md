# 【Mac Technology Overview】（八）Migrating from Cocoa Touch （从 Cocoa Touch 移植应用）

[toc]



***

If you've developed an iOS app, many of the frameworks available in OS X should already seem familiar to you. The basic technology stack in iOS and OSX are identical in many respects. But, despite the similarities, not all of the frameworks in OS X are exactly the same as their iOS counterparts. This chapter describes the differences you may encounter as you create Mac apps and explains how you can adjust your code to handle some of the more significant differences.



## 一、General Migration Notes

In OS X, apps typically have a screen that is larger, and resources that are greater, than in iOS. As a developer, you have more frameworks at your disposal in OS X development and (generally) more programmatic possibilities. This greater range of possibilities may be a pleasant prospect, but it also requires different ways of thinking about user expectations and app design.

As you work on migrating your app, pay attention to the idioms and metaphors that are different on each platform. For example, you would not base your OS X app on a stack of view controllers or include a feature that requires a gyroscope. It’s important that each version of your app looks and behaves as if it’s been designed for the platform it’s running on.

If your Cocoa Touch app is already factored according to the Model-View-Controller design pattern, it should be relatively easy to migrate key portions of your app to OS X.



### 1、Migrating the Data Model

Cocoa Touch apps whose data model is based on classes in the Foundation and Core Foundation frameworks can be brought over to OS X with little or no modification. OS X includes both frameworks, and they are virtually identical to their iOS counterparts. Most of the differences that do exist are relatively minor or are related to features that are not present in iOS. For example, iOS apps do not support AppleScript. For a detailed list of differences, see [Foundation Framework Differences](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW2). 

If your Cocoa Touch app is built on top of Core Data, you can easily migrate that data model to an OS X app. The Core Data framework in OS X supports binary and SQLite data stores (as it does in iOS), and it also supports XML data stores. For the supported data stores, you can copy your Core Data resource files to your OS X app project and use them as is. For information on how to use Core Data in your app, see *[Core Data Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CoreData/index.html#//apple_ref/doc/uid/TP40001075)*. 

Because OS X apps can display much more data on the screen than iOS apps can, you can expand your data model as part of your migration, as long as it doesn’t degrade the user experience. In addition to having access to more display space, an OS X app also has access to more resources, including memory. Although you can work with larger data sets, be sure that your algorithms scale to the new platform so that you don’t introduce inefficiencies when you migrate your app. 



### 2、Migrating the User Interface

For various reasons, the structure and implementation of the user interface (UI) in an OS X app is very different from that in an iOS app. Adapting your app to these differences is the main work of migration. As you bring your iOS app to OS X, keep the following themes in mind. 

- **Device differences impact the user experience.** In contrast to an iOS app, an OS X app has access to a larger screen, a more dependable supply of power, and a much larger pool of memory. These differences affect how an app presents information to users and how users interact with the app. For example, there is generally only one window per app in iOS, and that window has a fixed size, plays a limited role in the UI, and cannot be manipulated by users. On the other hand, an OS X app often has multiple windows. These windows can contain separate documents, or they might display auxiliary information, such as tool palettes or app preferences. Users can move, resize, close, minimize, and perform other operations with the windows in an OS X app. 

- **Users interact with apps differently on each platform.** Because people use touch gestures to interact with iOS apps, the onscreen UI objects must be large enough to manipulate with a human finger. In OS X, people use a mouse, trackpad, or other input device to move the onscreen pointer and interact with UI objects. Because the pointer is much more precise than a finger, the layout of an OS X app tends to be very different from the layout of an iOS app.

  

- **Users are not always aware of the file system.** iOS users have no direct access to the file system; instead, an iOS app reads and writes files to prescribed locations in its sandbox. In OS X, users can access the file system using the Finder interface. Although not all OS X apps expose the file system to users, those that do must also be prepared to handle issues related to document format, file encoding, and so on. Some OS X apps—for example, iPhoto and iTunes—keep their databases in an app-specific location and provide users with ways to manage their content without interacting with the file system.



When you create a new OS X app project in Xcode, you don’t get the same app templates to choose from that you do when you start an iOS app project. (Although OS X defines a few app types—described in [Apps](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SoftwareProducts/SoftwareProducts.html#//apple_ref/doc/uid/TP40001067-CH206-SW10)—these types are not directly related to the project templates.) The Cocoa app template is the typical choice for developing a standard OS X app.



For comprehensive information about the UI design principles of OS X, see *OS X Human Interface Guidelines*. For programmatic information about the windows and views you use to build your interface, and the underlying architecture on which they are based, see *[Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)*. 



***

### 3、Migration Strategies

When migrating your app from iOS to OS X, there are several approaches you can use to minimize the amount of code refactoring necessary in your view and controller classes. Each approach has its advantages and disadvantages, and is thus best used in specific instances, as described in Table 7-1.



| Situation                                                    | Migration approach                                           | Advantages                                                   | Disadvantages                                                |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| When you have heavily platform-dependent code                | Mirror your code across both platforms, customizing as necessary. | Offers flexibility                                           | Code duplication, resulting in greater maintenance and testing costs |
| When a common, lower-level framework provides necessary functionality | Use the common framework. For example, drop down from `UIKit` and `AppKit` to a lower-level, shared framework, to maximize code re-use and and minimize maintenance. | Maximizes code reuse, minimizes maintenance                  | Significant refactoring of your existing code, and less functionality provided by the lower-level framework |
| When dealing with an underlying API that’s significantly different between the two platforms (option 1) | Use an adapter pattern, a design pattern that allows the interface of an existing class to be accessed from another interface. | Maximizes code reuse, provides simplified interface, requires less maintenance | Additional code to write                                     |
| When dealing with an underlying API that’s significantly different between the two platforms (option 2) | Create an adapter using the `#define` preprocessor macro. For example, replace every instance of your color class with either `UIColor` or `NSColor`. This approach also gives you compile-time error checking. | Minimizes new code to write, provides compile-time error checking | Can only be used for supported classes: `UIColor` and `NSColor`; `UIFont` and `NSFont`; `UIImage` and `NSImage`; `UIBezierPath` and `NSBezierPath`. Limited API coverage within supported classes. Requires custom archiving approach. |



**Video::** [WWDC 2013 Bringing Your iOS Apps to OS X](http://devstreaming.apple.com/videos/wwdc/2013/216xcx4x7if809qdggi7vcc/216/ref.mov#t=28:32,41:49)

[WWDC 2014 Sharing code between iOS and OS X](https://developer.apple.com/videos/wwdc/2014/#233)





### 4、Migrating the Controller Layer

Controller objects are a critical area of difference between app development for iOS and for OS X. In iOS, `UIViewController` objects are key components that support the presentation of data and handle many device-specific behaviors such as orientation changes. In OS X v10.10 there are three view controllers: `NSViewController`, `NSSplitViewController`, and `NSTableViewController`. Each view controller type participates in the event message chain and is able to respond to event messages.

Before OS X v10.10 there was only one view controller class, `NSViewController`, that do not receive event messages. In those earlier versions, the `NSWindowController` class is most similar to `UIViewController`. In OS X, a window controller manages a window and its current contents. 

OS X has no equivalent to the iOS navigation controller which manages a stack of view controllers. If your iOS app uses a view controller stack to display the UI, you need to redesign your app to take advantage of the larger device display and multiple windows that are available in OS X.

In addition to the view and window controller classes, OS X also has the `NSController` class. Instances of this class (and its concrete subclasses) are controller objects that are used in the Cocoa bindings technology. (Cocoa bindings, which is not available in iOS, connects data in a model object with the presentation of that data in a view object, so that both objects are updated when the data changes.) Because controller objects manage an app’s data model and not its views, they can be considered data controllers rather than view controllers.

For information about view controllers in OS X, see *[NSViewController Class Reference](https://developer.apple.com/documentation/appkit/nsviewcontroller)*, and for information about window controllers see *[NSWindowController Class Reference](https://developer.apple.com/documentation/appkit/nswindowcontroller)*. To learn more about `NSController` objects and Cocoa bindings, see *[Cocoa Bindings Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaBindings/CocoaBindings.html#//apple_ref/doc/uid/10000167i)*.



## 二、Differences Between the UIKit and AppKit Frameworks

In OS X, the AppKit framework provides the infrastructure for building graphical apps, managing the event loop, and performing other UI-related tasks. Although AppKit and UIKit (the corresponding iOS framework) provide similar support to apps, the implementation is very different. When you migrate an iOS app to OS X, you replace a significant number of UIKit classes with functionality provided by AppKit.

For information about the classes of AppKit, see *[Application Kit Framework Reference](https://developer.apple.com/documentation/appkit)*.



### 1、User Events and Event Handling

Handling events in OS X differs significantly from handling events in iOS apps, mainly because the types of user events on each platform are different. If your iOS app does its own event handling, you will have to rewrite much if not all of the event-handling code when you migrate the app to OS X. 

Unlike iOS, which defines touch events and motion events, OS X defines mouse events, keyboard events, trackpad events, tablet events, and tracking-area events. All of these event types relate to peripheral devices that can be attached to a computer. In addition, most of these event types include phases (for example, key-*up* and mouse-*down*) or modifiers (for example, pressing the Control key and a character key simultaneously) that event-handling code often has to test for. 

Although the AppKit framework also defines touch (`NSTouch`) objects and gesture events, these events are appropriate only for laptops or desktop computers with supported trackpads. In the OS X version of your app, it’s important to handle events from as many types of input devices as possible.

The basic techniques for handling events on each platform are similar. For example, a custom view must opt in to handle events. Then, to handle an event, a custom view must implement one or more methods declared by the responder class of the app framework. 

Common examples of iOS event handlers that you need to replace in OS X are `UITapGestureRecognizer` and `UILongPressGestureRecognizer`. `UITapGestureRecognizer` can be replaced in OS X with the `mouseUp:` method of `NSResponder` or subclasses, while UILongPressGestureRecognizer is typically replaced by a right-click event, with a menu displayed using the `menuForEvent:` method of `NSView`. 

You can do some event-handling tasks in OS X apps that have no parallel in iOS apps, such as tracking the movement of the pointer and monitoring incoming events in your own app or another app.

For more information about handling events in OS X apps, see *[Cocoa Event Handling Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/EventOverview/Introduction/Introduction.html#//apple_ref/doc/uid/10000060i)*.



### 2、Windows

At a basic level, windows in AppKit play the same role they do in UIKit: They present graphical content in a rectangular area of the screen, they are at the root of a view hierarchy, they coordinate drawing operations, and they help to distribute events. In most other respects, windows and the framework objects that represent them in OS X and in iOS are different. Here are a few key differences between iOS and OS X windows. 

- Most iOS apps have only one fixed size window. In contrast, an OS X app can have multiple windows of varying sizes and styles, and those windows share the screen space with the windows of other apps. Unlike an iOS window, which has no visual adornments, an OS X window usually displays a title and can include controls for moving, closing, resizing, and minimizing the window.

- An OS X app can have one or more main or secondary windows (an app that has multiple main windows is typically a document-based app). A main window is the principal focus of user events and presents an app’s data. A secondary window generally serves an auxiliary function and might provide additional control over the data presented in the main window. Secondary windows are often panels—that is, instances of the `NSPanel` class.

  

- In UIKit, the `UIWindow` class is a subclass of `UIView`, but in AppKit, the `NSWindow` class is a subclass of `NSResponder`. Consequently, windows in AppKit are not backed by Core Animation layers as they are in UIKit. This difference means that you have to perform animation explicitly, at the view level. For a summary of Core Animation differences, see [Table 7-3](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW15).



### 3、Menus

Most OS X apps have a much larger command set than comparable iOS apps have. In OS X, apps use the systemwide menu bar to present these commands, whereas iOS apps present commands in UI elements such as toolbars, buttons, table views, and switches. As you migrate your iOS app to OS X, think about the best way to move many of the commands invoked by these elements into menus.



**Note:** OS X apps can have pop-up lists, contextual menus, and menu-like controls such as the combo box in addition to menus in the menu bar.



By default, an OS X app’s menu bar has some standard menus—such as the Apple menu, the app menu, File, Edit, and so on—and each of these menus contains standard menu items. When you create an OS X app project in Xcode, the nib-file template gives you a “starter set” of menus for your menu bar; remove and add menus and menu items to customize this set for your app. 

Menu items use the target-action model to send commands (that is, *action messages*) to appropriate objects in the app. Some of the template menu items prewire their target and action properties. You can assign key equivalents to menu items that are most frequently invoked.

To learn more about menus, read *[Application Menu and Pop-up List Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/MenuList/MenuList.html#//apple_ref/doc/uid/10000032i)*. 



### 4、Documents

A document-based app enables users to create, edit, save, and open multiple documents, such as word-processing or spreadsheet documents. 

iOS provides a model for document-based apps through the abstract base class `UIDocument`. When you adopt the `UIDocument` approach, your app gets significant behavior with minimal coding effort on your part, including integration with iCloud storage, background reading and writing of data, and an optimized auto-save model. 

OS X takes support for documents a step farther, defining an extensive architecture for document-based apps, because this content model is common for the platform. The OS X document architecture is closely based on the Model-View-Controller design pattern. Each document has its own main window and can have secondary windows for auxiliary functions. When you use Xcode to develop a document-based app, you get appropriately configured nib files and stub source files for the `NSDocument` subclass used to manage your documents.

To learn more about the document architecture, read *[Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)*. 



### 5、Views and Controls

Some of the ready-to-use views that AppKit offers are similar to UIKit views in form, function, and interface. But even with these views, there are differences you should be aware of when migrating your code. Other UIKit views have no counterpart in AppKit because they would not work well in OS X; for these views, you must find a suitable alternative. For example, AppKit uses the `NSBrowser`class to manage the display of hierarchical information; in contrast, an iOS app would use navigation controllers. Some views that seem similar on both platforms have different inheritance characteristics. For example, in iOS `UITableView` inherits from the `UIScrollView` class, whereas in OS X `NSTableView` inherits from `NSControl`. 

Although the view base classes—that is, `UIView` and `NSView`—are somewhat similar on both platforms, there are some fundamental differences between them. 

- **Core Animation layers.** iOS views are layer backed by default. iOS apps typically manipulate views by changing properties of the view. In OS X, an app must opt in to make its views layer-backed. Consequently, it is more common for AppKit views to perform the same manipulations in their `drawRect:` method. [Table 7-3](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW15) gives more information about differences related to Core Animation layers.
- **Default coordinate system.** The default coordinate systems used in drawing operations are different in iOS and OS X. In iOS, the drawing origin is at the upper-left corner of a view; in OS X, the drawing origin is at the lower-left corner of a view. See [Graphics, Drawing, and Printing](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MigratingFromCocoaTouch/MigratingFromCocoaTouch.html#//apple_ref/doc/uid/TP40001067-CH8-SW14) for additional information.
- **Use of cells for controls.** Because AppKit views can incur significant overhead, some AppKit controls use cells (that is, `NSCell` objects) as a lightweight alternative to views. A cell holds the information that its control needs in order to send an action message; a cell also draws itself when commanded by its control. Cells make possible controls such as a matrix object and a table view that have two-dimensional arrays of active subregions. 
- **Drawing in relation to view bounds.** `UIView` subviews can draw outside their view bounds. By default, `NSView` subviews clip to view bounds, which is typically the desired behavior. 

For functional descriptions of the views and controls available in OS X, along with information on how to use them in your app, see *OS X Human Interface Guidelines*. To learn about the common characteristics and behavior of AppKit views, see *[View Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaViewsGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40002978)*.



### 6、File System 

Many OS X apps let users locate files and directories in the file system, save files to specific file-system locations, open files, and do other file-system operations. An iOS app, on the other hand, must perform all file-reading and file-writing operations within the confines of its sandbox. In OS X v10.7 and later, Mac apps can also be “sandboxed,” and this can restrict the file-system operations they can perform (for more information, see [App Sandbox](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreOSLayer/CoreOSLayer.html#//apple_ref/doc/uid/TP40001067-CH9-SW3)). Nonetheless, even these apps might have to be prepared to open and save files in the file system as the user directs (assuming that the user has the necessary file permissions). 

An OS X app enables these file-system behaviors largely through the Open and Save panels (implemented by the AppKit classes `NSOpenPanel` and `NSSavePanel`). Through instances of these objects, the app can present file-system browsers to users, prevent files it doesn’t recognize from being selected, and obtain users’ choices. You can also attach custom accessory views to these browsers. 

In addition to making use of the Open and Save panels, your app can call methods of the `NSFileManager` and `NSWorkspace` classes for many file-system interactions. `NSFileManager` lets your app create, move, copy, remove, and link file-system items. It also offers other capabilities, such as discovering directory contents, and getting and setting file and directory attributes. Operations of the `NSWorkspace` class augment those of `NSFileManager`; these operations include launching apps, opening specific files, mounting local volumes and removable media, setting the Finder information of files and directories, and tracking file-system changes. (Sandboxed apps can’t use `NSWorkspace` in many situations.)

If your iOS app writes and reads files in the `Documents` directory, it uses the `NSSearchPathForDirectoriesInDomains` function to get the proper directory path in the app sandbox. In OS X, you use the `URLsForDirectory:inDomains:` method of the `NSFileManager` class instead; for this platform you might need to specify domains other than the user domain, and standard directory locations other than `Documents`. For example, your app might want to write or read data in the user’s home directory, in `Library/Application Support`.



**Note:** OS X apps should always store files they create in an appropriate location in the user’s `Library` directory; they should not store files in `~/Documents` unless the user selects that location. 



To learn more about file-system domains, standard file-system locations, filename extensions, BSD file permissions, AppKit facilities for managing file-system operations, and other information related to the OS X file system, read *[File System Programming Guide](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/FileSystemProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010672)*. 



### 7、Graphics, Drawing, and Printing

There are many parallels between the graphics and drawing APIs of AppKit and those of UIKit, as shown in Table 7-2. Both frameworks have classes whose instances represent images, colors, and fonts. Both have classes for drawing Bezier paths and categories for drawing strings. Both have functions for stroking and filling rectangles. Both have programmatic facilities for obtaining and transforming graphics contexts of various types. In some cases, you can migrate code that uses UIKit methods and functions to corresponding AppKit methods and functions with little more than name changes.



|                       | iOS (UIKit)                           | OS X (AppKit)                                         | Comments                                                     |
| :-------------------- | :------------------------------------ | :---------------------------------------------------- | :----------------------------------------------------------- |
| **Images**            | `UIImage`                             | `NSImage`                                             | `NSImage` can render an image from source data appropriate to an output destination. |
| **Colors**            | `UIColor`                             | `NSColor`, `NSColorSpace`, color-related view classes | Apps can use `NSColorSpace` to more precisely define the colors represented by `NSColor`objects. |
| **Bezier paths**      | `UIBezierPath`                        | `NSBezierPath`                                        |                                                              |
| **Graphics contexts** | Functions declared in `UIGraphics.h`. | `NSGraphicsContext`                                   |                                                              |
| **PDF**               | Functions declared in `UIGraphics.h`. | PDF Kit framework                                     | OS X provides richer PDF support than iOS does.              |
| **Printing**          | Multiple classes                      | Multiple classes                                      | The classes and techniques for printing in each platform are completely different. |

On both platforms, you can call Core Graphics functions when the framework-supplied methods or functions don’t suffice for a particular purpose.

The drawing model for AppKit views is nearly identical to the drawing model for UIKit views, with one exception. UIKit views use a coordinate system where the origin for windows and views is in the upper-left corner by default, with positive axes extending down and to the right. In AppKit, the default origin point is in the bottom-left corner and the positive axes extend up and to the right. This is the *default coordinate system* of AppKit, which happens to coincide with the default coordinate system of Core Graphics. To change the default origin of an Appkit view, override the view’s `isFlipped` method and return `YES`. The following types of views are are already flipped by default: `NSButton, NSScrollView, NSSplitView, NSTabView,` and `NSTableView`. 



**Note:** Whereas UIKit uses Core Graphics data types for rectangles, points, and other geometric primitives, AppKit uses its own defined types for the same purpose—for example, `NSRect` and `NSPoint`.



For information about graphics and drawing in OS X, see *[Cocoa Drawing Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaDrawingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003290)*. To learn more about printing in OS X, see *[NSPrintInfo Class Reference](https://developer.apple.com/documentation/appkit/nsprintinfo)*.



### 8、Text

AppKit offers apps a sophisticated system for performing text-related tasks ranging from simple text entry to custom text layout and typesetting. Because the Cocoa text system is based on the Core Text framework and provides a comparable set of behaviors, Cocoa apps rarely need to use Core Text directly. 

The native text support of UIKit is limited. Still there is some correspondence between that support and the support offered by AppKit—namely, text views, text fields, font objects, string drawing, and HTML content. If your iOS app uses Core Text to draw and manage fonts and text layout, you can migrate much of that code to your OS X app. 

For an introduction to the text system of AppKit, see *[Cocoa Text Architecture Guide](https://developer.apple.com/library/archive/documentation/TextFonts/Conceptual/CocoaTextArchitecture/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009459)*.



### 9、Table Views

Table views in AppKit are structurally different from table views in UIKit. In UIKit, a table view has any number of rows, and one or more sections but it has only one column. In AppKit, a table view can have any number of rows and columns (and there is no formal notion of sections). An iOS app typically uses a series of UIKit table views, each in their own screen, to present a hierarchical data set. An OS X app, on the other hand, typically uses a single AppKit table view to present all of a data set at the same time. 

The structures of these table views differ because of the differences between the platforms. Table views, perhaps the most versatile UI object in iOS, are ideal for displaying data on a smaller screen. Apps use them to navigate hierarchies of data, to present master-detail relationships among data, to facilitate quick retrieval of indexed items, and to serve as lists from which users can select options. 

Table views in OS X exist largely to present tabular data in a larger window. AppKit provides other UI objects that are suitable for some of the roles played by UIKit table views—for example, lists (pop-up lists, checkboxes, and radio buttons) and navigation of data hierarchies (browsers and outline views). Consequently, when you migrate your app’s table views to OS X, you should first consider whether another AppKit view better suits your app’s needs than a table view. 

Table views in AppKit are `NSTableView` objects. Cells occupy the region where the rows and columns of the table view intersect. A table view’s cells can be based on `NSCell` objects or, in OS X v10.7 and later, `NSView` objects. View-based table views are the preferred alternative. Populating AppKit table views is similar to populating UIKit table views: A data source is queried for the number of rows in the table view and is then asked for the value to put into each cell. Table views in OS X have these other parallels with UIKit table views: 

- **Cell reuse**. The delegate of a view-based table view can return a view to use for a cell; the view has an identifier. On the first request, the table view loads this view from a nib file and then caches the view for subsequent requests. 
- **Animated operations**. Both `NSCell`-based and `NSView`-based table views have methods for inserting, removing, and moving rows and items, optionally with an animation.

`NSOutlineView`, a subclass of `NSTableView`, has many of these same behaviors. For more information about creating and using table views, see *[Table View Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/TableView/Introduction/Introduction.html#//apple_ref/doc/uid/10000026i)*. [NSStackView](https://developer.apple.com/documentation/appkit/nsstackview)is an Auto Layout–based view that creates and manages the constraints needed to create horizontal or vertical stacks of views. For more information about creating and using stack views, see *[View Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaViewsGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40002978)*. 



### 10、Other Interface Differences

When migrating your app, you should keep in mind other technology differences between UIKit and AppKit; Table 7-3 summarizes these differences. 



| Difference                         | Discussion                                                   |
| :--------------------------------- | :----------------------------------------------------------- |
| Core Animation layers              | Every drawing surface in OS X can be backed by a Core Animation layer (as in iOS), but an app has to explicitly request this backing for its views. Once this request is made, animation is supported for changes in the properties of the views. In AppKit you don’t get the same easy-to-use view-based animation support that you do in UIKit.AppKit also includes the animation features of layer hosting, animation proxies, and classes for animating multiple windows and views.For information about the animation capabilities and features of OS X, see *[Animation Overview](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/Animation_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004952)*. |
| Target-action model                | Target-action in AppKit defines only one form for method signatures, unlike UIKit, which has three forms. Controls in AppKit send their action messages in response to a discrete user action, such as a mouse click; the notion of multiple actions associated with multiple interaction phases does not exist on the platform. However, a control composed of multiple cells can send a different action message for each cell.For more information about controls and the target-action model in OS X apps, see *[Control and Cell Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ControlCell/ControlCell.html#//apple_ref/doc/uid/10000015i)*. |
| Responder chain                    | The responder chain in OS X differs slightly from the responder chain in iOS. As of OS X v10.10, view controllers are added as part of the chain for either user events or action messages. In earlier versions of OS X, view controllers are *not* part of the chain. For action messages, the responder chain in OS X includes window controllers and the view hierarchies of key windows and main windows. AppKit also uses the responder chain for cooperative error handling.To learn more about the responder chain, see *[Cocoa Event Handling Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/EventOverview/Introduction/Introduction.html#//apple_ref/doc/uid/10000060i)*. |
| User preferences                   | In OS X, all preferences belong in your app; there is no separation of preferences between those managed by your app and those managed by the system. OS X has nothing comparable to the Settings bundle used by iOS apps to specify user preferences presented by the Settings app. Instead apps must create a secondary window for the user preferences. Users open this window by choosing Preferences from the app menu. In addition, OS X integrates user preferences into Cocoa bindings and enables command-line access to the underlying defaults system. One commonality is that both AppKit and UIKit apps use the `NSUserDefaults` class to retrieve user preferences. For more information, see *[Preferences and Settings Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/UserDefaults/Introduction/Introduction.html#//apple_ref/doc/uid/10000059i)*. |
| Accessor methods versus properties | UIKit makes extensive use of properties throughout its class declarations, but AppKit mostly declares accessor methods instead of properties. |



## 三、Foundation Framework Differences

A slightly different version of the Foundation framework in iOS is available in OS X. Most of the classes you would expect to be present are available in both versions—for example, both framework versions provide support for managing values, strings, collections, threads, and many other common types of data. There are, however, some technologies that are present in Foundation in OS X but not included in iOS. These technologies are listed in Table 7-4. 



| Technology                                          | Notes                                                        |
| :-------------------------------------------------- | :----------------------------------------------------------- |
| Spotlight metadata management                       | Spotlight is a technology for organizing and accessing information on a computer using file metadata. (Metadata is data about a file, rather than the actual file contents.) If you want your app to create Spotlight queries and interact with the results, you use special query and predicate objects.For more information, see *[Spotlight Overview](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/MetadataIntro/MetadataIntro.html#//apple_ref/doc/uid/TP40001268)*. |
| Cocoa bindings                                      | Cocoa bindings is a technology that lets you, during development, establish a connection between an item of data encapsulated by a model object and the presentation of that data in a view. It eliminates the need for glue code in the controller layer of an app. For more information, see *[Cocoa Bindings Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaBindings/CocoaBindings.html#//apple_ref/doc/uid/10000167i)*. |
| Cocoa scripting (AppleScript)                       | Using certain classes of Foundation along with supporting technology, you can make an app scriptable. A scriptable app is one that responds to commands in AppleScript scripts. To learn more about this technology, see *[Cocoa Scripting Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ScriptableCocoaApplications/SApps_intro/SAppsIntro.html#//apple_ref/doc/uid/TP40002164)*. |
| Distributed objects and port name server management | Distributed objects is an interprocess messaging technology. With distributed objects, an object in an app can send a message to an object in a different Cocoa app in the same network or in a different network. The port name server is an object that provides a port-registration service to distributed objects. For information about this technology, see *[Distributed Objects Programming Topics](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DistrObjects/DistrObjects.html#//apple_ref/doc/uid/10000102i)*. |

The Foundation framework in OS X provides support for both event-driven and tree-based XML processing. The `NSXMLParser` class (also available in iOS) supports the parsing of a stream of XML. In addition, the framework provides the NSXML classes (so called because the names of these classes begin with “NSXML”). Instances of these classes represent an XML document as a tree structure of nodes, including elements and attributes. 

For a list of the specific classes that are available in OS X but not in iOS, see the class hierarchy diagram in The Foundation Framework in *[Foundation Framework Reference](https://developer.apple.com/documentation/foundation)*.



***
## 四、Differences in the Audio and Video Frameworks

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



## 五、Differences in Other Frameworks Common to Both Platforms

Table 7-5 lists the key differences in other OS X frameworks from their counterparts in iOS.



| Framework                       | Differences                                                  |
| :------------------------------ | :----------------------------------------------------------- |
| `AddressBook.framework`         | Contains the interfaces for accessing user contacts. Although it shares the same name, the OS X version of this framework is very different from its iOS counterpart.OS X has no framework for presenting an interface for contacts, whereas iOS does. For more information, see *[Address Book Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AddressBook/AddressBook.html#//apple_ref/doc/uid/10000117i)*. |
| `CFNetwork.framework`           | Contains the Core Foundation Network interfaces. In OS X, the CFNetwork framework is a subframework of an umbrella framework, Core Services. Most of the interfaces, however, are the same for iOS and OS X. For more information, see *[CFNetwork Framework Reference](https://developer.apple.com/documentation/cfnetwork)*. |
| `CoreGraphics.framework`        | Contains the Quartz interfaces. You can use Quartz to create paths, gradients, shadings, patterns, colors, images, and bitmaps in exactly the same way you do in iOS. The OS X version of Quartz has features not present in iOS, including PostScript support, image sources and destinations, Quartz Display Services support, and Quartz Event Services support. In OS X, the Core Graphics framework is a subframework of the Application Services umbrella framework and is not a top-level framework, as it is in iOS. For more information, see *[Quartz 2D Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html#//apple_ref/doc/uid/TP30001066)*. |
| `EventKit.framework`            | Provides classes for accessing and manipulating calendar events and reminders. The iOS version does not include reminder items. |
| `GameKit.framework`             | Provides APIs that help you incorporate Game Center, peer-to-peer connectivity, and in-game voice chat into your game. Some of the classes that present UI are different on iOS and OS X. |
| `GLKit.framework`               | Provides functions and classes that reduce the effort required to create new shader-based apps or to port existing apps that rely on fixed-function vertex or fragment processing provided by earlier versions of OpenGL ES or OpenGL. The iOS version includes classes that simplify the creation of OpenGL ES-aware views and view controllers. In OS X, `NSOpenGLView` class subsumes the `GLKView` and `GLKViewController` classes in iOS. |
| `OpenGL.framework`              | OS X uses OpenGL instead of the OpenGL ES framework used in iOS. This fuller-featured version of OpenGL is intended for desktop systems. The programmatic interface of OpenGL is much larger than the one for OpenGLES. OpenGL has many extensions that are not available in the embedded version of the framework. For information about the OpenGL support in OS X, see *[OpenGL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html#//apple_ref/doc/uid/TP40001987)*. |
| `QuartzCore.framework`          | Contains the Core Animation, Core Image, and Core Video interfaces. Most of the Core Animation interfaces are the same for OS X and iOS. However, the iOS version of the framework lacks the API support for layout constraints and Core Image filters found in the OS X version. For more information, see *Quartz Core Framework Reference*. |
| `Security.framework`            | Contains the security interfaces. Its OS X version includes more capabilities and programmatic interfaces. It has authentication and authorization interfaces and supports the display of certificate contents. In addition, its keychain interfaces are more comprehensive than the ones used in iOS. For information about the security support in OS X, see *[Security Overview](https://developer.apple.com/library/archive/documentation/Security/Conceptual/Security_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP30000976)*. |
| `SystemConfiguration.framework` | Contains networking interfaces. The OS X version contains the complete interfaces, not just the reachability interfaces you find in iOS. For more information, see *[System Configuration Programming Guidelines](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/SystemConfigFrameworks/SC_Intro/SC_Intro.html#//apple_ref/doc/uid/TP40001065)*. |