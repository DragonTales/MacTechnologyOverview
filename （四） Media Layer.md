# 【Mac Technology Overview】（四） Media Layer

[TOC]

***

https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html

***

## 一、概述

Beautiful graphics and high-fidelity multimedia are hallmarks of the OS X user experience. Take advantage of the technologies of the Media layer to incorporate 2D and 3D graphics, animations, image effects, and professional-grade audio and video functionality into your app.

漂亮的图标和高保真的多媒体是 OSX 用户体验的标志。使用媒体层技术来将 二维和三维图形、动画、图像效果和专业级音频和视频功能整合到应用程序中。



![../art/osx_architecture-media_2x.png](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/art/osx_architecture-media_2x.png)





***

## 二、Supported Media Formats 支持的媒体格式

OS X supports more than 100 media types, covering a range of audio, video, image, and streaming formats. Table 3-1 lists some of the more common supported file formats. 

OSX支持100多种媒体类型，包括音频、视频、图像和流媒体格式。表3-1 列出了一些更常见的支持文件格式。

| Image formats               | PICT, BMP, GIF, JPEG, TIFF, PNG, DIB, ICO, EPS, PDF          |
| --------------------------- | ------------------------------------------------------------ |
| Audio file and data formats | AAC, AIFF, WAVE, uLaw, AC3, MPEG-3, MPEG-4 (`.mp4`, `.m4a`), `.snd`, `.au`, `.caf`, Adaptive multi-rate (`.amr`) |
| Video file formats          | AVI, AVR, DV, M-JPEG, MPEG-1, MPEG-2, MPEG-4, AAC, OpenDML, 3GPP, 3GPP2, AMC, H.264, iTunes (`.m4v`), QuickTime (`.mov`, `.qt`) |
| Web streaming protocols     | HTTP, RTP, RTSP                                              |



## 三、Graphics Technologies 图像技术

A distinctive quality of any OS X app is high-quality graphics in its user interface. And on a Retina display, users are more aware than ever of your app’s graphics.

任何OSX应用程序的一个显著特点是 其用户界面中的高质量图形。在视网膜屏幕上，用户比以往任何时候都更清楚你的应用程序的图形。

The simplest, most efficient, and most common way to ensure high-quality graphics in your app is to use the standard views and controls of the AppKit framework, along with prerendered images in different resolutions. In this way, you let the system do the work of rendering the app’s UI appropriately for the current display. Occasionally, you might need to go beyond off-the-shelf views and simple graphics. In these situations, you can take advantage of the powerful OS X graphics technologies. The following sections describe some of these technologies; for summaries of all technologies see [Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW5).

确保应用程序中的高质量图形的最简单、最有效和最常见的方法是 使用AppKit框架的标准视图和控件，以及不同分辨率的预渲染图像。这样你可以让系在展示时，以适合的方式统渲染应用 UI。偶尔的，你可能需要超越现成的视图和简单的图形。这种情况下，你可以使用强大的 OSX 图形技术。接下来的部分将描述这些技术的一部分，查看所有技术的总结，可以参阅  [Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW5)。



### 1、Graphics and Drawing 图像和会话

OS X offers several system technologies for graphics and drawing. Many of these technologies provide support for making your rendered content look good at different screen resolutions. To learn how to make sure that your app looks good on a high-resolution display, see *[High Resolution Guidelines for OS X](https://developer.apple.com/library/archive/documentation/GraphicsAnimation/Conceptual/HighResolutionOSX/Introduction/Introduction.html#//apple_ref/doc/uid/TP40012302)*.

OSX 为图像和会话提供了一些系统技术。这些技术提供了支持，让你在不同屏幕分辨率下良好的渲染内容。学习关于如何让你的应用在高分辨率上看起来不错，可以参阅 [High Resolution Guidelines for OS X](https://developer.apple.com/library/archive/documentation/GraphicsAnimation/Conceptual/HighResolutionOSX/Introduction/Introduction.html#//apple_ref/doc/uid/TP40012302)。



#### 1.1 Cocoa Drawing Cocoa 绘图

The AppKit framework provides object-oriented wrappers for many of the features found in Quartz 2D. Cocoa provides support for drawing primitive shapes such as lines, rectangles, ovals, arcs, and Bezier paths. It supports drawing in both standard and custom color spaces and it supports content manipulations using graphics transforms. Drawing calls made from Cocoa are composited along with all other Quartz 2D content. You can even mix Quartz 2D drawing calls (and drawing calls from other system graphics technologies) with Cocoa calls in your code.

The AppKit framework is described in [AppKit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CocoaApplicationLayer/CocoaApplicationLayer.html#//apple_ref/doc/uid/TP40001067-CH274-SW6). For more information on how to draw using Cocoa features, see *[Cocoa Drawing Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaDrawingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40003290)*. 

AppKit 提供 Quartz 2D 中特性的面向对象的封装。Cocoa 支持绘制基本形状，如直线、矩形、椭圆、圆弧和Bezier路径。它同时支持绘制标准图形，和自定义颜色空间的兔皮昂，它还支持使用图形转化 进行内容操作。由Cocoa 发出的绘图调用 与所有其他 Quartz 2D 内容一起合成。甚至可以在代码中混合使用Quartz 2D绘图调用（以及来自其他系统图形技术的绘图调用）和Cocoa调用。你甚至可以在你的代码中，混合使用Cocoa 调用和 Quartz 2D 的绘图调用（和其它系统绘图技术）。



#### 1.2 Metal

Metal provides the lowest-overhead access to the GPU, enabling you to maximize the graphics and compute potential of your app. With a streamlined API, precompiled shaders, and support for efficient multi-threading, Metal can take your game or graphics app to the next level of performance and capability.

The Metal framework is described in *[Metal Programming Guide](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014221)*, *Metal Shading Language Guide*, and the associated references. 

Metal 提供了对GPU的最低开销访问，使您能够最大化图形并计算应用程序的潜力。使用 流线型 API，预编译的阴影，并支持高效的多线程，Metal 可以把你的游戏或图形应用程序的性能和能力的下一个层次。 



#### 1.3 Other Frameworks for Graphics and Drawing 其它图形和绘图框架

In addition to AppKit (specifically, its Cocoa drawing interface), there are several other important frameworks for graphics and drawing. By design, Cocoa drawing integrates well with the other graphics and drawing technologies listed next.

AppKit 之外有其他机构重要的 图形和绘图框架。Cocoa 绘图很好的继承了下列其它图形和绘图技术：

- **Core Graphics** (`CoreGraphics.framework`). Core Graphics (also known as *Quartz 2D*) offers native 2D vector- and image-based rendering capabilities that are resolution- and device-independent. These capabilities include path-based drawing, painting with transparency, shading, drawing of shadows, transparency layers, color management, antialiased rendering, and PDF document generation. The Core Graphics framework is in the Application Services umbrella framework.

  Core Graphics 提供了 基于二维矢量和图像的渲染功能，与分辨率和设备无关。这些功能包含了基于路径的绘制，使用透明度绘制、着色、阴影绘制、透明度层、颜色管理、抗锯齿渲染和PDF文档生成。Core Graphics 框架在 Application Services 这个伞形框架中。

  

  Quartz is at the heart of the OS X graphics and windowing environment. It provides rendering support for 2D content and combines a rich imaging model with on-the-fly rendering, compositing, and antialiasing of content. It also implements the windowing system for OS X and provides low-level services such as event routing and cursor management (for more information, see [Core Graphics](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-BBCEADBC)).

  Quartz 是 OSX 图像和窗口环境的核心。它提供了 2D 内容的渲染支持，整合了 丰富的图像模型与内容的实时渲染、合成和抗锯齿结合起来。它同时实现了 OSX 的窗口系统，提供了低级别的服务，比如时间路由和贯标管理（关于更多信息，可以参阅 [Core Graphics](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-BBCEADBC)）。

- **Core Animation.** Core Animation enables your app to create fluid animations using advanced compositing effects. It defines a hierarchical view-like abstraction that mirrors a hierarchy of views and is used to perform complex animations of user interfaces. Core Animation is implemented by the Quartz Core framework (`QuartzCore.framework`) (for more information, see [Core Animation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW29)).

  核心动画使你的应用可以 使用高级合成效果 创建流程的动画效果。它定义了一个类似于层次视图的抽象，该抽象反映了视图的层次结构，并用于执行用户界面的复杂动画。Core Animation 由 Quartz Core 框架（`QuartzCore.framework`）执行。更多信息可参阅  [Core Animation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW29)。

- **SpriteKit** (`SpriteKit.framework`). SpriteKit provides the tools and methods for creating and rendering and animating textured images, or sprites. You use graphical editors for creating sprites, and then use those sprites in scenes that simulate game physics. In addition to sprites, you can add lights, emitters, and different kinds of fields to scenes. SpriteKit animates your scene and calls back to your code for events such as collisions. To learn more, see [Sprite Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW34).

  SpriteKit 提供了创建、渲染和动画 纹理图像或精灵🧚‍♂️。你可以使用 图像编辑器来创建精灵，然后在场景中使用 sprites 来模拟游戏。在 sprites 之外，你可以添加  灯光、发射器和不同类型的场地 到场景中。SpriteKit 让你的场景动起来，并会冲突等事件回调你的代码。更多信息可参阅  [Sprite Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW34).



- **Scene Kit** (`SceneKit.framework`). Scene Kit provides a high-level, Objective-C graphics API that you can use to efficiently load, manipulate, and render 3D scenes. Powerful and easy-to-use Scene Kit integrates well with Core Animation and SpriteKit, allowing you to use built-in materials or custom GLSL shaders to render your 3D scenes (for more information, see [Scene Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW33)).

   Scene Kit  提供了高级的 OC 图形 API，你可以用来快速加载、操作和渲染 3D 场景。功能强大和易于使用的 Scene Kit 良好的配合了 Core Animation 和 SpriteKit。允许你使用内置材料和自定义的 GLSL 着色器来渲染你的 3D 场景（更多信息可参阅 [Scene Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW33) ）。



- **Metal** *Metal.framework* provides extremely low-overhead access to the capabilities of modern GPUs and enables high-performance 2D and 3D graphics, and parallel computational tasks. A more flexible and efficient alternative to OpenGL and OpenCL, Metal is intended for use by games and graphics-intensive applications that require fine-grained control over the GPU. To learn more about Metal, see *[Metal Programming Guide](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014221)* and *Metal Shading Language Guide*

  Metal 框架（`Metal.framework`）提供了 对现代GPU功能的极低开销访问，并支持高性能的二维和三维图形，以及并行的计算任务。作为 OpenGL 和 OpenCL 更灵活和搞笑的代替，Metal 用于 需要对GPU进行细粒度控制的游戏 和 图形密集型应用程序。更多 Metal 的信息可参阅  *[Metal Programming Guide](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014221)* and *Metal Shading Language Guide*。



- MetalKit MetalKit.framework provides libraries of commonly needed functions and classes to reduce the overall time for developing a Metal application. For more information, see *[MetalKit Framework Reference](https://developer.apple.com/documentation/metalkit)* and *[MetalKit Functions Reference](https://developer.apple.com/documentation/metalkit/metalkit_functions)*.

  MetalKit 框架（`MetalKit.framework`）提供了库，包含常用的功能和类，来减少开发 Metal 应用程序的总体时间。更多信息可参阅  [MetalKit Framework Reference](https://developer.apple.com/documentation/metalkit) 和 *[MetalKit Functions Reference](https://developer.apple.com/documentation/metalkit/metalkit_functions)*。



- **OpenGL** (`OpenGL.framework`). OpenGL is an open, standards-based technology for creating and animating real-time 2D and 3D graphics. It is primarily used for games and other apps with real-time rendering needs. To learn more about OpenGL in OS X, see [OpenGL](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW8).

  OpenGL 是一个 用于创建和动画 二维和三维图形的 开发的、标准的技术。它主要用于游戏和其他应用的实时渲染需求。更多 OSX 中的 OpenGL 信息可参阅 [OpenGL](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW8)。



- **GLKit** (`GLKit.framework`). GLKit provides libraries of commonly needed functions and classes that reduce the effort required to create shader-based apps or to port existing apps that rely on fixed-function vertex or fragment processing provided by earlier versions of OpenGL ES or OpenGL. To learn more about the GLKit framework, see [GLKit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW24).

  GLKit 提供了常用的函数和类的库，这些类和类减少了 创建 基于着色器的应用程序 所需的努力，或者移植了依赖于OpenGL ES或OpenGL的早期版本提供的 固定函数顶点 或 片段处理 的现有应用程序。



***
### 2、Text, Typography, and Fonts  文字、印刷和字体

OS X provides extensive support for advanced typography for Cocoa apps. With this support, your app can control the fonts, layout, typesetting, text input, and text storage when managing the display and editing of text. For the most basic text requirements, you can use the text fields, text views, and other text-displaying objects provided by the AppKit framework. 

OSX 为 Cocoa 的应用程序的高级排版提供了广泛的支持。有这项支持，你的应用可以在管理展示和编辑文本时，控制字体、布局、排版、文字输入和文本存储。作为最基础的文本需求，你可以使用 text fields, text views 和其他 AppKit 提供的文本展示对象。



There are two technologies to draw upon for more sophisticated text, font, and typography needs: the Cocoa text system and the Core Text API. Unless you need low-level access to the layout manager routines, the Cocoa text system should provide most of the features and performance you need. If you need a lower-level API for drawing any kind of text into a `CGContext`, then you should consider using the Core Text API.

- **Cocoa text system.** AppKit provides a collection of classes, known as the *Cocoa text system*, that together provide a complete set of high-quality typographical services. With these services, apps can create, edit, display, and store text with all the characteristics of fine typesetting, such as kerning, ligatures, line breaking, and justification. Use the Cocoa Text system to display small or large amounts of text and to customize the default layout manager classes to support custom layout. The Cocoa text system is the recommended technology for most apps that require text handling and typesetting capabilities.

  AppKit also offers a class (`NSFont`), a font manager, and a font panel. In addition, the Cocoa text system supports vertical text and linguistic tagging. 

  For an overview of the Cocoa text system, see *[Cocoa Text Architecture Guide](https://developer.apple.com/library/archive/documentation/TextFonts/Conceptual/CocoaTextArchitecture/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009459)*.

- **Core Text** (`CoreText.framework`). The Core Text framework contains low-level interfaces for laying out Unicode text and handling Unicode fonts. Core Text provides the underlying implementation for many features of the Cocoa text system. 

  To learn more about the Core Text framework, see [Core Text](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW3).



### 3、Images

Both AppKit and Quartz let you create objects that represent images (`NSImage` and `CGImageRef`) from various sources, draw these images to an appropriate graphics context, and even composite one image over another according to a given blending mode. Beyond the native capabilities of AppKit and Core Graphics, you can do other things with images using the following frameworks:

- **Image Capture Core** (`ImageCaptureCore.framework`). The Image Capture Core framework enables your app to browse locally connected or networked scanners and cameras, to list and download thumbnails and images, to take scans, rotate and delete images and, if the device supports it, to take pictures or control the scan parameters. For more information, see [Other Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW10).

- **Core Image.** Core Image is an image processing technology that allows developers to process images with system-provided image filters, create custom image filters, and detect features in an image. Examples of built-in filters are those that crop, blur, and warp images. Core Image is implemented by the Quartz Core framework (`QuartzCore.framework`). For more information, see [Core Image](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW30).

- **Image Kit.** Image Kit is built on top of the Image Capture Core framework. It provides views you can use in your app to help users connect to cameras and scanners, view and download images from these devices, and edit and process the images. For more information, see [Image Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW9).

  

- **Image I/O** (`ImageIO.framework`). The Image I/O framework helps you read image data from a source and write image data to a destination. Sources and destinations can be URLs, Core Foundation data objects, and Quartz data consumers and data providers. For more information, see [Image I/O](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW4).



### 4、Color Management

ColorSync is the color management system for OS X. It provides essential services for fast, consistent, and accurate color reproduction, proofing, and calibration. It also provides an interface for accessing and managing systemwide settings for color devices such as displays, printers, cameras, and scanners.

In most cases, you do not need to call ColorSync functions at all. Quartz and Cocoa automatically use ColorSync to manage pixel data when drawing on the screen or printing. By design, the ICC (International Color Consortium) profiles embedded in the color data of images and PDF documents are fully respected. You are strongly encouraged to use appropriate calibrated color spaces—for example, those based on ICC profiles—when creating your own content. For very special needs, ColorSync also allows you to define a custom color management module (CMM) to use instead of a system-provided CMM to perform required color conversions based on the ICC profiles.

For information about creating custom color spaces, see [Making Custom Color Spaces](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DrawColor/Tasks/UsingColorSpaces.html#//apple_ref/doc/uid/TP40001807-96917). For information on the ColorSync API, see *[ColorSync on Mac OS X](https://developer.apple.com/library/archive/technotes/tn2035/_index.html#//apple_ref/doc/uid/DTS10003071)*, and the ColorSync header files in `/System/Library/Frameworks/ApplicationServices.framework/Frameworks/ColorSync.framework/Headers`. 



### 5、Printing

OS X implements printing support using a collection of APIs and system services that are available to all app environments. Drawing on the capabilities of Quartz, the printing system delivers a consistent human interface and streamlines the development process for printer vendors. It also provides apps with a high degree of control over the user interface elements in printing dialogs. Table 3-2 describes some other features of the OS X printing system.



| Feature                       | Description                                                  |
| :---------------------------- | :----------------------------------------------------------- |
| AirPrint                      | Users can print to an AirPrint-enabled printer on their network without having to use a third-party driver. |
| CUPS                          | Common UNIX Printing System (CUPS), an open source architecture used to handle print spooling and other low-level features, provides the underlying support for printing. |
| Desktop printers              | Desktop printers offer users a way to manage printing and print jobs from the Dock or desktop. |
| Fax support                   | Fax support means that users can fax documents directly from the Print dialog. |
| Native PDF support            | PDF as a native data type lets any app easily save textual and graphical data to the device-independent PDF format. |
| PostScript support            | PostScript support allows apps to use legacy third-party drivers to print to PostScript Level 2–compatible and Level 3–compatible printers and to convert PostScript files directly to PDF. |
| Print preview                 | The print preview capability lets users see documents through a PDF viewer app prior to printing. |
| Printer discovery             | Printer discovery enables users to detect, configure, and add to printer lists those printers that implement Bluetooth or Bonjour. |
| Raster printers (support for) | This support allows apps to print to raster printers using legacy third-party drivers. |
| Speedy spooling               | Speedy spooling enables apps that use PDF to submit PDF files directly to the printing system instead of spooling individual pages. |

To learn more about the Cocoa printing architecture, and about how to support printing in a Cocoa app, see *[Printing Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Printing/osxp_aboutprinting/osxp_aboutprt.html#//apple_ref/doc/uid/10000083i)*; for information about the Core Printing API, see *[Core Printing Reference](https://developer.apple.com/documentation/applicationservices/core_printing)*.



## 四、Audio Technologies

OS X includes support for high-quality audio recording, synthesis, manipulation, and playback. The frameworks in the following list are ordered from high level to low level, with the AV Foundation framework offering the highest-level interfaces you can use. When choosing an audio technology, remember that higher-level frameworks are easier to use and, for this reason, are usually preferred. Lower-level frameworks offer more flexibility and control but require you to do more work. 

- **AV Foundation** (`AVFoundation.framework`). AV Foundation supports audio playback, editing, analysis, and recording. Unless you are creating a fast-action game, a virtual music instrument, or a Voice over IP (VoIP) app, look first at AV Foundation. For more information, see [AV Foundation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW25).
- **OpenAL** (`OpenAL.framework`). OpenAL implements a cross-platform standard API for 3D audio. OpenAL also lets you add high-performance positional playback in games and other apps. For more information, see [OpenAL](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW16).
- **Core Audio** (`CoreAudio.framework`). Core Audio consists of a set of frameworks that provide audio services that support recording, playback, synchronization, signal processing, format conversion, synthesis, and surround sound. Core Audio is well suited for adding VoIP and other high-performance audio features to your app. For more information, see [Core Audio](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-TPXREF165).



## 五、Video Technologies

Whether you are playing movie files from your app or streaming them from the network, OS X provides several technologies to play your video-based content. On systems with the appropriate hardware, you can also use these technologies to capture video and incorporate it into your app.

When choosing a video technology, remember that the higher-level frameworks simplify your work and are, for this reason, usually preferred. The frameworks in the following list are ordered from highest to lowest level, with the AV Foundation framework offering the highest-level interfaces you can use.

- **AVKit** (`AVKit.framework`). AV Kit supports playing visual content in your application using the standard controls.
- **AV Foundation** (`AVFoundation.framework`). AV Foundation supports playing, recording, reading, encoding, writing, and editing audiovisual media.
- **Core Media** (`CoreMedia.framework`). Core Media provides a low-level C interface for managing audiovisual media. With the Core Media I/O framework, you can create plug-ins that can access media hardware and that can capture video and mixed audio and video streams. 
- **Core Video** (`CoreVideo.framework`). Core Video provides a pipeline model for digital video between a client and the GPU to deliver hardware-accelerated video processing while allowing access to individual frames. Use Core Video only if your app needs to manipulate individual video frames; otherwise, use AV Foundation.

For information about each of the video frameworks (as well as other frameworks) in the Media layer, see [Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW5).



## 六、Media Layer Frameworks

OS X includes numerous technologies for rendering and animating 2D and 3D content (including text) and for playing, recording, and editing audiovisual media. 



### 1、Application Services Umbrella Framework

The Application Services umbrella framework (`ApplicationServices.framework`) includes the following subframeworks. You should not link with these frameworks directly; instead link with (and import) `ApplicationServices.framework`. 



#### 1.1 Core Graphics

The Quartz 2D client API offered by the Core Graphics framework (`CoreGraphics.framework`) provides commands for managing the graphics context and for drawing primitive shapes, images, text, and other content. The Core Graphics framework defines the Quartz 2D interfaces, types, and constants you use in your apps.



Quartz 2D provides many important features to apps, including the following:

- High-quality rendering on the screen 
- High-resolution UI support
- Antialiasing for all graphics and text
- Support for adding transparency information to windows
- Internal compression of data
- A consistent feature set for all printers 
- Automatic PDF generation and support for printing, faxing, and saving as PDF
- Color management through ColorSync

For information about the Quartz 2D API, see *[Quartz 2D Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html#//apple_ref/doc/uid/TP30001066)*.



#### 1.2 Core Text

Core Text is a C-based API that provides precise control over text layout and typography. Core Text provides a layered approach to laying out and displaying Unicode text. You can modify as much or as little of the system as suits your needs. Core Text also provides optimized configurations for common scenarios, saving setup time in your app. 

The Core Text font API is complementary to the Core Text layout engine. Core Text font technology is designed to handle Unicode fonts natively and comprehensively, unifying disparate OS X font facilities so that developers can do everything they need to do without resorting to other APIs. 

For more information about Core Text, see *[Core Text Programming Guide](https://developer.apple.com/library/archive/documentation/StringsTextFonts/Conceptual/CoreText_Programming/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005533)* and *[Core Text Reference Collection](https://developer.apple.com/documentation/coretext)*.



#### 1.3 Image I/O

The `NSImage` class takes advantage of all the capabilities of Image I/O and is the preferred method for loading and drawing image resources on OS X. It is particularly important to use `NSImage` if you’re working with images that are visible in the UI, because this class handles multiresolution images.

Apps can use the Image I/O framework to read and write image data in most file formats in a highly efficient manner. It offers very fast image encoding and decoding facilities, supports image metadata and caching, provides color management, and is able to load image data incrementally. 

The central objects in Image I/O are image sources and image destinations. Sources and destinations can be URLs (`CFURLRef`), data objects (`CFDataRef` and `CFMutableDataRef`), and data consumer and data provider objects (`CGDataConsumerRef` and `CGDataProviderRef`). 

The Image I/O programmatic interfaces were once part of Quartz 2D (Core Graphics) but have been collected in an separate framework so that apps can use it independently of Core Graphics. To learn more about Image I/O, see *[Image I/O Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/ImageIOGuide/imageio_intro/ikpg_intro.html#//apple_ref/doc/uid/TP40005462)*.



### 2、AV Foundation

The AV Foundation framework (`AVFoundation.framework`) provides services for capturing, playing, inspecting, editing, and reencoding time-based audiovisual media. The framework includes many Objective-C classes, with the core class being `AVAsset`; this class presents a uniform model and inspection interface for all forms and sources of audiovisual media. The services offered by this framework include the following:

- Movie or audio capture
- Movie or audio playback, including precise synchronization and audio panning
- Media editing and track management
- Media asset and metadata management
- Audio file inspection (for example, data format, sample rate, and number of channels)

For most audio recording and playback requirements, you can use the `AVAudioPlayer` and `AVAudioRecorder` classes.

AV Foundation is the recommended framework for all new development involving time-based audiovisual media. AV Foundation is also recommended for transitioning existing apps based on QuickTime or QTKit.



**Note:** The AV Foundation frameworks for OS X and iOS are almost identical.



For more information about the classes of the AV Foundation framework, see *[AVFoundation Programming Guide](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AVFoundationPG/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40010188)*.



### 3、ColorSync

The ColorSync framework (`ColorSync.framework`) implements the color management system for OS X. To find out more about ColorSync, see [Color Management](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-TPXREF160).

The ColorSync framework is a subframework of the Application Services umbrella framework. Your project cannot link to it directly; it must link instead to `ApplicationServices.framework`.



### 4、Core Audio

Core Audio consists of a group of frameworks that offer sophisticated services for manipulating multichannel audio. (Core Audio is also the name of one framework of this group.) You can use Core Audio to generate, record, mix, edit, process, and play audio. You can also use Core Audio to work with MIDI (Musical Instrument Digital Interface) data using both hardware and software MIDI instruments. The frameworks of Core Audio are as follows:

- **Core Audio** (`CoreAudio.framework`). Core Audio provides interfaces that allow your app to interact with audio hardware and obtain and convert the host's time base. It also defines data types used throughout the Core Audio frameworks.
- **Core Audio Kit** (`CoreAudioKit.framework`). Core Audio Kit contains Objective-C classes that provide user interfaces for audio units.
- **Audio Toolbox** (`AudioToolbox.framework`). Audio Toolbox provides general audio services to apps, such as audio converters and audio processing graphs, reading and writing audio data in files, managing and playing event tracks, and assigning and reading audio format metadata.
- **Audio Unit** (`AudioUnit.framework`). The Audio Unit framework defines programmatic interfaces for creating and manipulating audio units, plug-ins for handling or generating audio signals.
- **Core MIDI** (`CoreMIDI.framework`). Core MIDI provides MIDI support for apps, allowing them to communicate with MIDI devices, to configure or customize the global state of the MIDI system, and to create MIDI play-through connections between MIDI sources and destinations.

Most Core Audio interfaces are C based, providing a low-latency and flexible programming environment that is suitable for real-time apps. You can use Core Audio from any OS X program. Some of the benefits of Core Audio include the following:

- Built-in support for reading and writing a wide variety of audio file and data formats
- Plug-in support for custom formats, audio synthesis, and processing (audio DSP)
- A modular approach for constructing audio signal chains
- Easy MIDI synchronization
- Support for scheduled playback and synchronization with access to timing and control information
- A standardized interface to all built-in and external hardware devices, regardless of connection type (USB, Firewire, PCI, and so on)

Audio queue objects give you access to incoming or outgoing raw audio data while the system mediates playback and recording, employs codecs (if needed), and makes hardware connections. To intercept and process audio as it proceeds through an audio queue object, you use the real-time, callback-based feature known as *audio queue processing taps*. This feature works for input (such as for recording) as well as output (such as for playback). Audio queue processing taps let you insert audio units or other forms of audio processing, effectively tapping into and modifying the data stream within an audio queue. You can also use this technology in a *siphon mode*, in which you gain access to the stream but do not modify it.

To learn more about the Core Audio framework, see *[Core Audio Framework Reference](https://developer.apple.com/documentation/coreaudio)*.



### 5、GLKit

GLKit framework (`GLKit.framework`) helps reduce the effort required to create new shader-based apps or to port existing apps that rely on fixed-function vertex or fragment processing provided by earlier versions of OpenGL ES or OpenGL. In addition, the GLKit framework includes APIs that perform several optimized mathematical operations, reduce the effort in loading texture data, and provide standard implementations of commonly needed shader effects.



**Note:** GLKit requires an OpenGL context that supports the OpenGL 3.2 Core Profile. GLKit is not available to 32-bit apps in OS X.



To learn more about using GLKit in your app, see *[GLKit Framework Reference](https://developer.apple.com/documentation/glkit)*.



### 6、Instant Messaging

OS X provides enables plugins for supporting messaging services:

- **Instant Message Service Plug-in** (`IMServicePlugin.framework`). The Instant Message Service Plug-in framework enables the creation of bundle plug-ins that let apps talk to instant-messaging services, such as iChat. It includes support for the buddy list, handle availability, handle icon, status messages, instant messaging, and group-chat messaging. 

For more information about using the Instant Message framework, see *Instant Message Programming Guide*. For more information about the Instant Message Service Plug-in framework, see *IMServicePlugIn Protocol Reference* and *IMServicePlugInInstantMessagingSupport Protocol Reference*



### 7、OpenAL

The Open Audio Library (`OpenAL.framework`) is a cross-platform standard framework for delivering 3D audio. OpenAL lets you implement high-performance positional playback in games and other programs. Because it is a cross-platform standard, apps you write using OpenAL in OS X can be ported to run on many other platforms. 

OpenAL in OS X supports audio capture, exponential and linear distance models, location offsets, and spatial effects such as reverb and occlusion. The OS X implementation of OpenAL also supports certain Core Audio features, such as mixer sample rates. 

To learn about the OpenAL specification, visit [OpenAL](http://www.openal.org/).



### 8、OpenGL

OpenGL is an industry wide standard for developing portable three-dimensional (3D) graphics apps. It is specifically designed for apps such as games that need a rich, robust framework for visualizing shapes in two and three dimensions. OpenGL is one of the most widely adopted graphics API standards, which makes code written for OpenGL portable and consistent across platforms. The OpenGL framework (`OpenGL.framework`) in OS X includes a highly optimized implementation of the OpenGL libraries that provides high-quality graphics at a consistently high level of performance. 

OpenGL offers a broad and powerful set of imaging functions, including texture mapping, hidden surface removal, alpha blending (transparency), antialiasing, pixel operations, viewing and modeling transformations, atmospheric effects (fog, smoke, and haze), and other special effects. Each OpenGL command directs a drawing action or causes a special effect, and developers can create lists of these commands for repetitive effects. Although OpenGL is largely independent of the windowing characteristics of each operating system, the standard defines special glue routines to enable OpenGL to work in an operating system’s windowing environment. The OS X implementation of OpenGL implements these glue routines to enable operation with Quartz Compositor.

OpenGL supports the ability to use multiple threads to process graphics data. OpenGL also supports pixel buffer objects, color-managed texture images in the sRGB color space, and 64-bit addressing. It also offers improvements in the shader programming API. 

OS X v10.7 added support for Open GL 3.2 Core, which added more extensions as baseline features. Note that routines and mechanisms found in OpenGL 1.*n* and OpenGL 2.*n* are deprecated, including the removal of the fixed-function pipeline that was the main approach to developing OpenGL 1.*n* apps. An OpenGL 3.2 app requires you to create your own shader strategy rather than assuming that a standard graphics pipeline will do everything. As a result, for simple apps you need to write more boilerplate code than was required by previous versions of OpenGL.

For information about using OpenGL in OS X, see *[OpenGL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html#//apple_ref/doc/uid/TP40001987)*. 



### 9、Quartz

The Quartz umbrella framework includes the following subframeworks. You should not link directly with any of the subframeworks; instead link with (and import) `Quartz.framework`.



#### 9.1 Image Kit

The Image Kit (`ImageKit.framework`) is an Objective-C framework that makes it easy to incorporate powerful imaging services into your apps. This framework takes advantage of features in Quartz, Core Image, OpenGL, and Core Animation to provide an advanced and highly optimized development path for implementing the following features: 

- Displaying images
- Rotating, cropping, and performing other image-editing operations 
- Browsing for images 
- Taking pictures using the built-in picture taker panel
- Displaying slideshows 
- Browsing for Core Image filters 
- Displaying custom views for Core Image filters 

For more information on how to use Image Kit, see *[ImageKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/ImageKitProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004907)* and *Image Kit Reference Collection*.



#### 9.2 PDF Kit

PDF Kit (`PDFKit.framework`, a subframework of the Quartz framework) is a Cocoa framework for managing and displaying PDF content directly from your app’s windows and dialogs. You can embed a `PDFView` object in your window and give it a PDF file to display. The PDF view handles the rendering of the PDF content, handles copy-and-paste operations, and provides controls for navigating and setting the zoom level. Other classes let you get the number of pages in a PDF file, find text, manage selections, add annotations, and specify the behavior of some graphical elements, among other actions. 

For more information on PDF Kit, see *[PDFKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/PDFKitGuide/PDFKit_Prog_Intro/PDFKit_Prog_Intro.html#//apple_ref/doc/uid/TP40001863)*. 



#### 9.3 Quartz Composer

The Quartz Composer framework (`QuartzComposer.framework`) provides programmatic support for working with Quartz Composer compositions. It enables apps to load, play, and control compositions and to integrate them with Cocoa views, Core Animation layers, or OpenGL rendering.

For more information, see *[Quartz Composer Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/QuartzComposer/qc_intro/qc_intro.html#//apple_ref/doc/uid/TP40001357)*.



#### 9.4 Quick Look UI

The Quick Look UI framework (`QuickLookUI.framework`) defines an interface for implementing a Quick Look preview panel, which displays the preview of a list of items. The framework also includes the capability for embedding a preview inside a view.

For an example of an app that implements Quick Look preview panels, see *[QuickLookDownloader](https://developer.apple.com/library/archive/samplecode/QuickLookDownloader/Introduction/Intro.html#//apple_ref/doc/uid/DTS40009082)*.



### 10、Quartz Core

The Quartz Core framework (`QuartzCore.framework`) implements two important system technologies for graphics and imaging Core Animation and Core Image. 



#### 10.1 Core Animation

Core Animation is a set of Objective-C classes used for sophisticated 2D rendering and animation. Using Core Animation, you can create everything from basic window content to carousel–style user interfaces (such as the Front Row interface), and achieve respectable animation performance without having to tune your code using OpenGL or other low-level drawing routines. This performance is achieved using server-side content caching, which restricts the compositing operations performed by the server to only those parts of a view or window whose contents actually change. 

At the heart of the Core Animation programming model are layer objects, which are similar in many ways to Cocoa views. As with views, you can arrange layers in hierarchies, change their size and position, and tell them to draw themselves. Unlike views, layers do not support event handling, accessibility, or drag and drop. 

You can manipulate the layout of layers in more ways than the layout of traditional Cocoa views. In addition to positioning layers using a layout manager, you can apply 3D transforms to layers to rotate, scale, skew, or translate them in relation to their parent layer. 

Layer content can be animated implicitly or explicitly depending on the actions you take. Modifying specific properties of a layer—such as its geometry, visual attributes, or children—typically triggers an implicit animation to transition from the property’s old state to the new one. For example, adding a child layer triggers an animation that causes the child layer to fade gradually into view. You can also trigger animations explicitly in a layer by modifying its transformation matrix. 

You can manipulate layers independent of, or in conjunction with, the views and windows of your app. Cocoa apps can take advantage of Core Animation’s integration with the `NSView` class to add animation effects to windows. Layers can also support the following types of content: 

- Quartz and Cocoa drawing content
- OpenGL content
- Quartz Composer compositions
- Core Image filter effects

For information about Core Animation, see *[Animation Overview](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/Animation_Overview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004952)*.



#### 10.2 Core Image

Core Image extends the basic graphics capabilities of the system to provide a framework for implementing complex visual behaviors in your app. Core Image uses GPU-based acceleration and 32-bit floating-point support to provide fast image processing and pixel-level accurate content. Its plug-in–based architecture lets you expand the capabilities of Core Image through the creation of image units, which implement the desired visual effects.

Core Image includes built-in image units that allow you to do the following:

- Crop, composite, blur, and sharpen images 
- Correct color, including performing white-point adjustments
- Apply color effects, such as sepia tone
- Warp the geometry of an image by applying an affine transform or a displacement effect
- Generate color, checkerboard patterns, Gaussian gradients, and other pattern images
- Add transition effects to images or video
- Provide real-time control, such as color adjustment and support for sports mode, vivid mode, and other video modes
- Apply linear lighting effects, such as spotlights
- Face detection including mouth and eye bounds.

You can use both the built-in and custom image units in your app to implement special effects and perform other types of image manipulations.

For information about how to use Core Image or how to write custom image units, see *[Core Image Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreImaging/ci_intro/ci_intro.html#//apple_ref/doc/uid/TP30001185)* and *[Core Image Reference Collection](https://developer.apple.com/documentation/coreimage)*. For information about the built-in filters in Core Image, see *[Core Image Filter Reference](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Reference/CoreImageFilterReference/index.html#//apple_ref/doc/uid/TP40004346)*. 



### 11、QuickTime Kit

QTKit (`QTKit.framework`) is a deprecated Objective-C framework for manipulating QuickTime-based media. Use the AV Foundation framework instead; to learn more, see [AV Foundation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW25). 







### 12、Scene Kit

The Scene Kit framework (`SceneKit.framework`) provides a high-level Objective-C API that helps you to efficiently load, manipulate, and render 3D scenes in your app. Scene Kit allows you to import Digital Asset Exchange files (`.dae` files) that are created by popular content-creation applications and gives you access to the objects, lights, cameras, and geometry data that define a 3D scene. Using an approach based on scene graphs, Scene Kit makes it simple to modify, animate, and render your 3D scenes. 

Scene Kit integrates with Image Kit, SpriteKit, and Core Animation, so you do not need advanced 3D graphical programming skills. For example, you can embed a 3D scene into a layer and then use Core Animation compositing capabilities to add overlays and backgrounds. You can also use Core Animation layers as textures for your 3D objects in 3D scenes. To learn how to use Scene Kit in your app, see *[SceneKit Programming Guide](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/SceneKit_PG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40012282)*.



### 13、Sprite Kit

The Sprite Kit framework (`SpriteKit.framework`) provides a graphics rendering and animation infrastructure that you can use to animate arbitrary textured images, or sprites. You use graphical tools to create the sprites. You then create scenes including sprites, light sources, emitters, and physics fields. Sprite Kit animates the scene you specify using a traditional animation loop, doing the work to render frames of animation efficiently using the graphics hardware.

Sprite kit includes basic sound playback support in addition to physics simulation. In addition, you can create complex special effects and texture atlases directly in Xcode. This combination of framework and tools makes Sprite Kit a good choice for games and other apps that require similar kinds of animation. Animated images created with Sprite Kit work well with SceneKit. To learn how to use Sprite Kit, see *[SpriteKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsAnimation/Conceptual/SpriteKit_PG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013043)*.



### 14、Other Media Layer Frameworks

The Media layer of OS X also has the following frameworks:

- **Audio Video Bridging** (`AudioVideoBridging.framework`). The Audio Video Bridging framework supports Audio Video Bridging (AVB) and implements the IEEE P1722.1 draft standard. AVB enhances the quality of service and provides guaranteed latency and bandwidth for media streams over an AVB network. Audio Video Bridging gives you access to the Entity discovery and control protocols of IEEE P1722.1 over an Ethernet network.

- **Core Media** (`CoreMedia.framework`). The Core Media framework provides low-level audiovisual media objects and tools for managing them. It also defines the fundamental time representation used uniformly throughout AV Foundation.

  For information about using the Core Media framework, see *[Core Media Framework Reference](https://developer.apple.com/documentation/coremedia)*.

- **Core Media I/O** (`CoreMediaIO.framework`). The Core Media I/O framework publishes the Device Abstraction Layer (DAL) plug-in API. This technology enables you to create plug-ins that can access media hardware and capture video and “muxed” (video combined with audio) streams. Core Media I/O is a replacement for the QuickTime VDig API.

- **Core Video** (`CoreVideo.framework`). Core Video creates a bridge between QuickTime and the graphics card’s GPU to deliver hardware-accelerated video processing. Benefits of Core Video include filters and effects, per-pixel accuracy, and hardware scalability.

  For information about using the Core Video framework, see *[Core Video Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreVideo/CVProg_Intro/CVProg_Intro.html#//apple_ref/doc/uid/TP40001536)*. 

- **Disc Recording** (`DiscRecording.framework`). Disc Recording gives apps the ability to burn and erase CDs and DVDs. Your app specifies the content to be burned but the framework (`DiscRecording.framework`) takes over the process of buffering the data, generating the proper file format information, and communicating everything to the burner. 

  The Disc Recording UI framework (`DiscRecordingUI.framework`) provides a complete, standard set of windows for gathering information from the user and displaying the progress of the burn operation.

  For more information about the Disc Recording frameworks, see *Disc Recording Framework Reference* and *Disc Recording UI Framework Reference*. 

- **DVD Playback** (`DVDPlayback.framework`). The DVD Playback framework embeds DVD viewer capabilities into an app. You use the framework to control various aspects of playback, including menu navigation, viewer location, angle selection, and audio track selection. You can play back DVD data from disc or from a local `VIDEO_TS` directory. 

  For more information about using the DVD Playback framework, see *[DVD Playback Services Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/DVDPlaybackGuide/dvdguide_intro/dvdguide_intro.html#//apple_ref/doc/uid/TP40002163)*.

- **Image Capture Core** (`ImageCaptureCore.framework`). Image Capture Core helps you capture image data from scanners and digital cameras. The interfaces of the framework are device independent, so you can use them to gather data from any devices connected to the system. You can get a list of devices, retrieve information about a specific device or image, and retrieve the image data itself.

  This framework works in conjunction with the Image Capture Devices framework (`ICADevices.framework`) to communicate with imaging hardware. For information on using these frameworks, see *[Image Capture Applications Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/ImageCaptureServicesProgrammingGuide/01Introduction/01Introduction.html#//apple_ref/doc/uid/TP40005196)*. 

- **Video Toolbox** (`VideoToolbox.framework`). The Video Toolbox framework comprises the 64-bit replacement for the QuickTime Image Compression Manager. Video Toolbox provide services for video compression and decompression, and for conversion between raster image formats stored in Core Video pixel buffers.