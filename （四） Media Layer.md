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

有两种技术可用于更复杂的文本、字体和排版需求：Cocoa 文字系统和 Core Text API。除非你需要使用对布局管理器历程低级别的访问， Cocoa text system  会提供你需要的大部分特性和表现。如果你需要低层级的 API 来绘制任意类型的文本到 `CGContext`。



- **Cocoa text system.** AppKit provides a collection of classes, known as the *Cocoa text system*, that together provide a complete set of high-quality typographical services. With these services, apps can create, edit, display, and store text with all the characteristics of fine typesetting, such as kerning, ligatures, line breaking, and justification. Use the Cocoa Text system to display small or large amounts of text and to customize the default layout manager classes to support custom layout. The Cocoa text system is the recommended technology for most apps that require text handling and typesetting capabilities.

  AppKit also offers a class (`NSFont`), a font manager, and a font panel. In addition, the Cocoa text system supports vertical text and linguistic tagging.

  For an overview of the Cocoa text system, see *[Cocoa Text Architecture Guide](https://developer.apple.com/library/archive/documentation/TextFonts/Conceptual/CocoaTextArchitecture/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009459)*.

  Cocoa text system：AppKit 提供了一系列类，称为 Cocoa 文本系统，它们仪器提供了一整套高质量的因数服务。使用这些服务，应用可以创建、编辑、展示和存储 具有精细排班所有特征的文本，如字距调整、连字、换行和对齐。使用 Cocoa 文字系统来展示少数或大量的文本，自定义默认的布局管理器类来支持自定义布局。Cocoa 文字系统推荐给大部分需要文字处理和打印功能的应用使用。

- **Core Text** (`CoreText.framework`). The Core Text framework contains low-level interfaces for laying out Unicode text and handling Unicode fonts. Core Text provides the underlying implementation for many features of the Cocoa text system. 

  To learn more about the Core Text framework, see [Core Text](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW3).
  
  Core Text 框架包含低级别的接口来布局编码字符，处理编码格式。Core Text 为 Cocoa 文字系统的许多特征 提供 底层实现。关于更多 Core Text 框架，可以参阅  [Core Text](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW3)。

***
### 3、Images 图片

Both AppKit and Quartz let you create objects that represent images (`NSImage` and `CGImageRef`) from various sources, draw these images to an appropriate graphics context, and even composite one image over another according to a given blending mode. Beyond the native capabilities of AppKit and Core Graphics, you can do other things with images using the following frameworks:

AppKit 和 Quartz 都可以帮你创建 表示图片（`NSImage` and `CGImageRef`）的对象。将这些图像绘制到 适当的图形上下文中，甚至根据给定的混合模式 将一个图像合成到另一个图像上。在  AppKit 和 Core Graphics 的原生功能之外，你也可以使用下面框架处理图片：



- **Image Capture Core** (`ImageCaptureCore.framework`). The Image Capture Core framework enables your app to browse locally connected or networked scanners and cameras, to list and download thumbnails and images, to take scans, rotate and delete images and, if the device supports it, to take pictures or control the scan parameters. For more information, see [Other Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW10).

  Image Capture Core  框架可以使你的应用 浏览本地连接或联网 的 扫描仪和照相机，列出并下载缩略图和图像，进行扫描，旋转并删除图像，如果设备支持，则拍照或控制扫描参数。关于更多信息，可以参阅  [Other Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW10)。

  

- **Core Image.** Core Image is an image processing technology that allows developers to process images with system-provided image filters, create custom image filters, and detect features in an image. Examples of built-in filters are those that crop, blur, and warp images. Core Image is implemented by the Quartz Core framework (`QuartzCore.framework`). For more information, see [Core Image](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW30).

  Core Image 是一个图片处理技术，允许开发者 使用系统提供的图片滤镜来处理图片，创建自定义滤镜 ，检测图像中的特征。内置滤镜的例子有 裁剪、模糊 和 扭曲图像。Core Image 是 Quartz Core  框架 (`QuartzCore.framework`) 实现的，更多信息可参阅  [Core Image](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW30)。

  

- **Image Kit.** Image Kit is built on top of the Image Capture Core framework. It provides views you can use in your app to help users connect to cameras and scanners, view and download images from these devices, and edit and process the images. For more information, see [Image Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW9).

  Image Kit 在  Image Capture Core 框架的上层，它同乐你可以再应用中帮助用户连接 照相机和扫描仪、查看和下载这些设备中的图片、编辑和处理图片 的视图。更多信息可参阅 [Image Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW9).

  

- **Image I/O** (`ImageIO.framework`). The Image I/O framework helps you read image data from a source and write image data to a destination. Sources and destinations can be URLs, Core Foundation data objects, and Quartz data consumers and data providers. For more information, see [Image I/O](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW4).

  Image I/O 框架可以帮助你 从输入源 读取图片数据，编写图片数据到目的地。源头和目的地可以是 URLs, Core Foundation 数据对象，Quartz 数据使用者和数据提供者，更多信息可以参阅  [Image I/O](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW4)。



***
### 4、Color Management 颜色管理

ColorSync is the color management system for OS X. It provides essential services for fast, consistent, and accurate color reproduction, proofing, and calibration. It also provides an interface for accessing and managing systemwide settings for color devices such as displays, printers, cameras, and scanners.

ColorSync 是 OSX 的颜色管理系统。它为快速、一致和准确的色彩复制、校对和校准提供必要的服务。它还提供了一个接口，用于访问和管理彩色设备（如显示器、打印机、相机和扫描仪）的系统范围设置。



In most cases, you do not need to call ColorSync functions at all. Quartz and Cocoa automatically use ColorSync to manage pixel data when drawing on the screen or printing. By design, the ICC (International Color Consortium) profiles embedded in the color data of images and PDF documents are fully respected. You are strongly encouraged to use appropriate calibrated color spaces—for example, those based on ICC profiles—when creating your own content. For very special needs, ColorSync also allows you to define a custom color management module (CMM) to use instead of a system-provided CMM to perform required color conversions based on the ICC profiles.

在大多数情况下，你完全不需要调用 ColorSync 的功能。Quartz 和 Cocoa 会自动使用 ColorSync 来在屏幕绘制或打印时 管理像素数据。通过设计，ICC（国际色彩协会 International Color Consortium）的配置文件 嵌入到图像和PDF文档的色彩数据中 得到了充分的认同。你呗强烈建议来使用 恰当的 校准颜色空间，比如，这些在你创建自己内容时 基于 ICC 配置文件。对于特别的需求，ColorSync 同样允许你定义一个自定义颜色管理模块（CMM），来代替系统提供的 CMM 来实现需要的基于 ICC 配置文件的颜色转换。  



For information about creating custom color spaces, see [Making Custom Color Spaces](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DrawColor/Tasks/UsingColorSpaces.html#//apple_ref/doc/uid/TP40001807-96917). For information on the ColorSync API, see *[ColorSync on Mac OS X](https://developer.apple.com/library/archive/technotes/tn2035/_index.html#//apple_ref/doc/uid/DTS10003071)*, and the ColorSync header files in `/System/Library/Frameworks/ApplicationServices.framework/Frameworks/ColorSync.framework/Headers`. 

关于更多创建自定义颜色空间的信息，可以参阅  [Making Custom Color Spaces](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/DrawColor/Tasks/UsingColorSpaces.html#//apple_ref/doc/uid/TP40001807-96917)。ColorSync 相关的 API 信息，可以参阅  *[ColorSync on Mac OS X](https://developer.apple.com/library/archive/technotes/tn2035/_index.html#//apple_ref/doc/uid/DTS10003071)*, 和  `/System/Library/Frameworks/ApplicationServices.framework/Frameworks/ColorSync.framework/Headers` 中的  ColorSync 头文件。



***
### 5、Printing 打印

OS X implements printing support using a collection of APIs and system services that are available to all app environments. Drawing on the capabilities of Quartz, the printing system delivers a consistent human interface and streamlines the development process for printer vendors. It also provides apps with a high degree of control over the user interface elements in printing dialogs. Table 3-2 describes some other features of the OS X printing system.

OSX 使用一组 API 和 系统服务 实现对所有应用环境的打印支持。利用 Quartz 的功能，打印系统提供了一致的人机界面，并简化了打印机供应商的开发过程。它还为应用程序提供了 对打印对话框中用户界面元素的 高度控制。表 3-2 描述了 OSX 打印系统的一些其他特性。




| Feature                       | Description                                                  |
| :---------------------------- | :----------------------------------------------------------- |
| AirPrint <br>云打印           | Users can print to an AirPrint-enabled printer on their network without having to use a third-party driver. <br>用户可以在他们的网络上，无需使用第三方驱动，来使用支持 云打印的打印机。 |
| CUPS                          | Common UNIX Printing System (CUPS), an open source architecture used to handle print spooling and other low-level features, provides the underlying support for printing.<br>标准 UNIX 打印系统，一个用来处理后台打印和其他低级别功能  的 开源架构，为打印提供底层支持。 |
| Desktop printers              | Desktop printers offer users a way to manage printing and print jobs from the Dock or desktop.<br>桌面打印机 提供用户一个 从桌面或 Dock 管理打印和打印任务的方式。 |
| Fax support                   | Fax support means that users can fax documents directly from the Print dialog.<br>传真支持意味着 用户可以从打印会话中直接传真文件。 |
| Native PDF support            | PDF as a native data type lets any app easily save textual and graphical data to the device-independent PDF format.<br> PDF 是一个原始数据类型，让应用可以简单地保存纹理和图形数据到 设备独立的 PDF 格式。 |
| PostScript support            | PostScript support allows apps to use legacy third-party drivers to print to PostScript Level 2–compatible and Level 3–compatible printers and to convert PostScript files directly to PDF.<br> PostScript支持  允许应用程序 使用传统的第三方驱动程序 打印到PostScript 2级兼容和 3级兼容的打印机，并将PostScript 文件直接转换为PDF格式。 |
| Print preview                 | The print preview capability lets users see documents through a PDF viewer app prior to printing.<br> 打印机预览允许 用户 在打印之前 使用 PDF查看器应用 来查看文档。 |
| Printer discovery             | Printer discovery enables users to detect, configure, and add to printer lists those printers that implement Bluetooth or Bonjour.<br> 对于实现蓝牙或 Bonjour 的打印机，打印机发现（Printer discovery） 能让用户去 探测、配置打印机， 和将打印机 添加到打印机列表。 |
| Raster printers (support for) | This support allows apps to print to raster printers using legacy third-party drivers.<br> 这个支持允许应用程序使用传统的第三方驱动 来打印到 光栅打印机。 |
| Speedy spooling               | Speedy spooling enables apps that use PDF to submit PDF files directly to the printing system instead of spooling individual pages.<br> Speedy spooling 让使用 PDF 的应用，直接提交 PDF 给打印系统， 而非后台处理单个界面。 |

To learn more about the Cocoa printing architecture, and about how to support printing in a Cocoa app, see *[Printing Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Printing/osxp_aboutprinting/osxp_aboutprt.html#//apple_ref/doc/uid/10000083i)*; for information about the Core Printing API, see *[Core Printing Reference](https://developer.apple.com/documentation/applicationservices/core_printing)*.

关于更多 Cocoa 打印架构，和如何在 Cocoa 应用中支持打印，可以参阅 *[Printing Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/Printing/osxp_aboutprinting/osxp_aboutprt.html#//apple_ref/doc/uid/10000083i)*; 更多关于 Core Printing API 的信息,  可以参阅 *[Core Printing Reference](https://developer.apple.com/documentation/applicationservices/core_printing)*。

***
## 四、Audio Technologies 音频技术

OS X includes support for high-quality audio recording, synthesis, manipulation, and playback. The frameworks in the following list are ordered from high level to low level, with the AV Foundation framework offering the highest-level interfaces you can use. When choosing an audio technology, remember that higher-level frameworks are easier to use and, for this reason, are usually preferred. Lower-level frameworks offer more flexibility and control but require you to do more work. 

OSX 支持高质量的音频录制、合成、操作和回放。下列框架是按从高到低层级的顺序排列的，AV Foundation 框架提供了您可以使用的最高级别接口。在选择音频技术时，请记住，更高级别的框架更易于使用，因此通常是首选。较低级别的框架提供了更多的灵活性和控制，但需要您做更多的工作。

- **AV Foundation** (`AVFoundation.framework`). AV Foundation supports audio playback, editing, analysis, and recording. Unless you are creating a fast-action game, a virtual music instrument, or a Voice over IP (VoIP) app, look first at AV Foundation. For more information, see [AV Foundation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW25).

  AVFoundation 支持音频播放、编辑、分析和录制。除非你正在创建一个快速动作游戏，一个虚拟音乐工具，或一个IP语音（VoIP）应用，首先看看AV基金会。更多信息可参阅  [AV Foundation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW25)。

  

- **OpenAL** (`OpenAL.framework`). OpenAL implements a cross-platform standard API for 3D audio. OpenAL also lets you add high-performance positional playback in games and other apps. For more information, see [OpenAL](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW16).

  OpenAL 实现了 3D 音频的跨平台标准接口。OpenAL 还允许您在游戏和其他应用程序中添加高性能位置播放。更多信息可参阅  [OpenAL](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW16)。



- **Core Audio** (`CoreAudio.framework`). Core Audio consists of a set of frameworks that provide audio services that support recording, playback, synchronization, signal processing, format conversion, synthesis, and surround sound. Core Audio is well suited for adding VoIP and other high-performance audio features to your app. For more information, see [Core Audio](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-TPXREF165).

  核心音频由一组框架组成，这些框架提供支持录音、回放、同步、信号处理、格式转换、合成和环绕声的音频服务。Core Audio 非常适合在应用程序中添加VoIP和其他高性能音频功能。更多信息可参阅  [Core Audio](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-TPXREF165)。



***
## 五、Video Technologies 视频技术

Whether you are playing movie files from your app or streaming them from the network, OS X provides several technologies to play your video-based content. On systems with the appropriate hardware, you can also use these technologies to capture video and incorporate it into your app.

无论您是从应用程序播放电影文件，还是从网络流媒体播放，OSX 都提供了多种技术来播放基于视频的内容。在具有适当硬件的系统上，您还可以使用这些技术捕获视频，并将其合并到应用程序中。



When choosing a video technology, remember that the higher-level frameworks simplify your work and are, for this reason, usually preferred. The frameworks in the following list are ordered from highest to lowest level, with the AV Foundation framework offering the highest-level interfaces you can use.

在选择视频技术时，请记住，更高层次的框架简化了您的工作，因此通常是首选框架。下表中的框架按从高到低的顺序排列，AV Foundation 框架提供了您可以使用的最高级别接口。



- **AVKit** (`AVKit.framework`). AV Kit supports playing visual content in your application using the standard controls.

  AV Kit 支持使用标准控件 在应用程序中 播放可视内容。

- **AV Foundation** (`AVFoundation.framework`). AV Foundation supports playing, recording, reading, encoding, writing, and editing audiovisual media.

  AV Foundation 支持播放、录制、读取、编码、写入和编辑视听媒体。

- **Core Media** (`CoreMedia.framework`). Core Media provides a low-level C interface for managing audiovisual media. With the Core Media I/O framework, you can create plug-ins that can access media hardware and that can capture video and mixed audio and video streams. 

   Core Media 提供用于管理视听媒体的低级 C 接口。使用 Core Media I/O 框架，您可以创建可以访问媒体硬件 并可以捕获视频和混合音频和视频流的插件。

- **Core Video** (`CoreVideo.framework`). Core Video provides a pipeline model for digital video between a client and the GPU to deliver hardware-accelerated video processing while allowing access to individual frames. Use Core Video only if your app needs to manipulate individual video frames; otherwise, use AV Foundation.

  Core Video 为客户端和GPU之间的数字视频提供管道模型，以提供硬件加速的视频处理，同时允许访问单个帧。仅当你的应用需要 操作单个视频帧时 才使用核心视频；否则，请使用AV Foundation。

For information about each of the video frameworks (as well as other frameworks) in the Media layer, see [Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW5).

更多关于 Media 层的单个视频框架，可以参阅下面的 [Media Layer Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW5)。



## 六、Media Layer Frameworks 媒体层框架

OS X includes numerous technologies for rendering and animating 2D and 3D content (including text) and for playing, recording, and editing audiovisual media. 

OSX 包括许多渲染和动画二维和三维内容（包括文本）以及播放、录制和编辑视听媒体的技术。

### 1、Application Services Umbrella Framework

The Application Services umbrella framework (`ApplicationServices.framework`) includes the following subframeworks. You should not link with these frameworks directly; instead link with (and import) `ApplicationServices.framework`. 

Application Services 伞形框架（`ApplicationServices.framework`） 包含以下子框架。使用子框架的时候，不应该直接引入子框架，而应该引入  `ApplicationServices.framework`。



#### 1.1 Core Graphics 核心图形

The Quartz 2D client API offered by the Core Graphics framework (`CoreGraphics.framework`) provides commands for managing the graphics context and for drawing primitive shapes, images, text, and other content. The Core Graphics framework defines the Quartz 2D interfaces, types, and constants you use in your apps.

 Core Graphics 框架（`CoreGraphics.framework`） 提供的 Quartz 2D 客户端 API， 提供命令来管理图形上下文和 绘制基本形状、图片、文本和其他内容。 Core Graphics 框架定义了你应用中的  Quartz 2D 的接口、类型、和常量。



Quartz 2D provides many important features to apps, including the following:

Quartz 2D 为应用提供了许多重要的特性，包含下列特性：

- High-quality rendering on the screen 

  在屏幕上高质量的渲染

- High-resolution UI support

  高分辨率用户界面支持

- Antialiasing for all graphics and text

  所有图形和文本的抗锯齿

- Support for adding transparency information to windows

  支持向windows添加透明信息

- Internal compression of data

  数据的内部压缩

- A consistent feature set for all printers 

  对所有打印机一致的功能集合

- Automatic PDF generation and support for printing, faxing, and saving as PDF

  自动生成PDF 和 支持打印、传真和保存PDF

- Color management through ColorSync

  通过 ColorSync 管理颜色

For information about the Quartz 2D API, see *[Quartz 2D Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html#//apple_ref/doc/uid/TP30001066)*.

更多关于 Quartz 2D API 的信息，可参阅 *[Quartz 2D Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/drawingwithquartz2d/Introduction/Introduction.html#//apple_ref/doc/uid/TP30001066)*。

***
#### 1.2 Core Text 核心文本

Core Text is a C-based API that provides precise control over text layout and typography. Core Text provides a layered approach to laying out and displaying Unicode text. You can modify as much or as little of the system as suits your needs. Core Text also provides optimized configurations for common scenarios, saving setup time in your app. 

核心文本是一个基于C的API，它提供了对文本布局和排版的精确控制。核心文本提供了一种分层的方法来布局和显示Unicode文本。您可以根据需要 来修改系统的多少。核心文本还为常见场景提供优化配置，节省应用程序中的安装时间。

The Core Text font API is complementary to the Core Text layout engine. Core Text font technology is designed to handle Unicode fonts natively and comprehensively, unifying disparate OS X font facilities so that developers can do everything they need to do without resorting to other APIs. 

For more information about Core Text, see *[Core Text Programming Guide](https://developer.apple.com/library/archive/documentation/StringsTextFonts/Conceptual/CoreText_Programming/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005533)* and *[Core Text Reference Collection](https://developer.apple.com/documentation/coretext)*.

Core Text  的字体 API 是对 Core Text 布局引擎的补充。Core Text 字体技术旨在以原生和全面的方式处理Unicode字体，统一不同的OSX字体功能，以便开发人员 无需借助其他API 即可完成所需的所有工作。



***
#### 1.3 Image I/O

The `NSImage` class takes advantage of all the capabilities of Image I/O and is the preferred method for loading and drawing image resources on OS X. It is particularly important to use `NSImage` if you’re working with images that are visible in the UI, because this class handles multiresolution images.

NSImage类利用了 图像I/O 的所有功能，是在 OS X 上加载和绘制图像资源的首选方法。如果使用的是UI中可见的图像，则使用NSImage尤为重要，因为该类处理多分辨率图像。



Apps can use the Image I/O framework to read and write image data in most file formats in a highly efficient manner. It offers very fast image encoding and decoding facilities, supports image metadata and caching, provides color management, and is able to load image data incrementally. 

应用可以使用 Image I/O  框架以高效的方式读取和写入大多数文件格式的图像数据。它提供非常快速的图像编码和解码设施，支持图像元数据和缓存，提供颜色管理，并能够增量加载图像数据。



The central objects in Image I/O are image sources and image destinations. Sources and destinations can be URLs (`CFURLRef`), data objects (`CFDataRef` and `CFMutableDataRef`), and data consumer and data provider objects (`CGDataConsumerRef` and `CGDataProviderRef`). 

Image I/O 的核心对象是图像源和图像目的地。源和目标可以是 URLs（`CFURLRef`）、数据对象（`CFDataRef`和 `CFMutableDataRef`），以及数据使用者和数据提供程序对象（`CGDataConsumerRef`和`CGDataProviderRef`）。



The Image I/O programmatic interfaces were once part of Quartz 2D (Core Graphics) but have been collected in an separate framework so that apps can use it independently of Core Graphics. To learn more about Image I/O, see *[Image I/O Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/ImageIOGuide/imageio_intro/ikpg_intro.html#//apple_ref/doc/uid/TP40005462)*.

Image I/O 编程接口曾是Quartz 2D（核心图形）的一部分，但已收集在单独的框架中，以便应用程序可以独立于核心图形使用它。要了解有关 Image I/O的更多信息，请参阅  *[Image I/O Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/ImageIOGuide/imageio_intro/ikpg_intro.html#//apple_ref/doc/uid/TP40005462)*。



***
### 2、AV Foundation

The AV Foundation framework (`AVFoundation.framework`) provides services for capturing, playing, inspecting, editing, and reencoding time-based audiovisual media. The framework includes many Objective-C classes, with the core class being `AVAsset`; this class presents a uniform model and inspection interface for all forms and sources of audiovisual media. The services offered by this framework include the following:

AV Foundation 框架（AVFoundation.framework）提供捕获、播放、检查、编辑和 重新编码 基于时间的视听媒体的服务。该框架包含许多Objective-C类，核心类是`AVAsset`，该类为视听媒体的各种形式和来源提供了统一的模型和检查接口。该框架提供的服务包括：

- Movie or audio capture

  电影或音频捕获

- Movie or audio playback, including precise synchronization and audio panning

  电影或音频播放，包括精确同步和音频平移

- Media editing and track management

  媒体编辑与跟踪管理

- Media asset and metadata management

  媒体资产和元数据管理

- Audio file inspection (for example, data format, sample rate, and number of channels)

  音频文件检查（例如，数据格式、采样率和通道数）

For most audio recording and playback requirements, you can use the `AVAudioPlayer` and `AVAudioRecorder` classes.

对于大多数音频录制和播放要求，可以使用  `AVAudioPlayer` 和 `AVAudioRecorder` 类。

AV Foundation is the recommended framework for all new development involving time-based audiovisual media. AV Foundation is also recommended for transitioning existing apps based on QuickTime or QTKit.

AV Foundation 是所有涉及基于时间的视听媒开发的 推荐框架。AV Foundation 还建议用于过度现有的基于 QuickTime/QTKIT 的应用程序。

**Note:** The AV Foundation frameworks for OS X and iOS are almost identical.

For more information about the classes of the AV Foundation framework, see *[AVFoundation Programming Guide](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AVFoundationPG/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40010188)*.

备注： AV Foundation  框架在 iOS 和 macOS 上基本一致。更多关于 AV Foundation 框架的信息可以查阅  *[AVFoundation Programming Guide](https://developer.apple.com/library/archive/documentation/AudioVideo/Conceptual/AVFoundationPG/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40010188)*。



***
### 3、ColorSync

The ColorSync framework (`ColorSync.framework`) implements the color management system for OS X. To find out more about ColorSync, see [Color Management](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-TPXREF160).

The ColorSync framework is a subframework of the Application Services umbrella framework. Your project cannot link to it directly; it must link instead to `ApplicationServices.framework`.

ColorSync 框架实现 OSX 上的颜色管理系统。更多关于  ColorSync, 可以查阅 [Color Management](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-TPXREF160).

ColorSync 框架是  Application Services  伞形框架的子框架。你必须引入  `ApplicationServices.framework` 来使用 ColorSync，而非直接使用 ColorSync。



### 4、Core Audio 核心音频

Core Audio consists of a group of frameworks that offer sophisticated services for manipulating multichannel audio. (Core Audio is also the name of one framework of this group.) You can use Core Audio to generate, record, mix, edit, process, and play audio. You can also use Core Audio to work with MIDI (Musical Instrument Digital Interface) data using both hardware and software MIDI instruments. The frameworks of Core Audio are as follows:

Core Audio 由一组框架组成，这些框架提供 复杂的多声道 音频操作服务。（Core Audio也是 这组框架中的一个框架的名称）可以使用Core Audio生成、录制、混合、编辑、处理和播放音频。您还可以使用核心音频与MIDI（乐器数字接口）数据一起使用硬件和软件MIDI乐器。核心音频的框架如下：

- **Core Audio** (`CoreAudio.framework`). Core Audio provides interfaces that allow your app to interact with audio hardware and obtain and convert the host's time base. It also defines data types used throughout the Core Audio frameworks.

  Core Audio  提供接口，允许您的应用程序与音频硬件交互，并获取和转换主机的时基。它还定义了整个 Core Audio  框架中使用的数据类型。

- **Core Audio Kit** (`CoreAudioKit.framework`). Core Audio Kit contains Objective-C classes that provide user interfaces for audio units.

  核心音频工具包 包含为音频单元提供用户界面的Objective-C类。

- **Audio Toolbox** (`AudioToolbox.framework`). Audio Toolbox provides general audio services to apps, such as audio converters and audio processing graphs, reading and writing audio data in files, managing and playing event tracks, and assigning and reading audio format metadata.

  Audio Toolbox 为应用程序提供通用的音频服务，如音频转换器 和 音频处理图表、读取和写入文件中的音频数据、管理和播放事件轨迹、分配和读取音频格式元数据。

- **Audio Unit** (`AudioUnit.framework`). The Audio Unit framework defines programmatic interfaces for creating and manipulating audio units, plug-ins for handling or generating audio signals.

  音频单元框架定义了用于创建和操作音频单元的编程接口，以及用于处理或生成音频信号的插件。

- **Core MIDI** (`CoreMIDI.framework`). Core MIDI provides MIDI support for apps, allowing them to communicate with MIDI devices, to configure or customize the global state of the MIDI system, and to create MIDI play-through connections between MIDI sources and destinations.

  Core MIDI 为应用程序提供 MIDI支持，允许它们与MIDI设备通信，配置或自定义 MIDI系统的全局状态，并通过 MIDI源 和目标 之间的连接创建 MIDI播放。

Most Core Audio interfaces are C based, providing a low-latency and flexible programming environment that is suitable for real-time apps. You can use Core Audio from any OS X program. Some of the benefits of Core Audio include the following:

大多数核心音频接口是基于C的，提供适合于实时应用的低延迟和灵活的编程环境。您可以使用任何 OSX 程序的核心音频。核心音频的一些好处包括：

- Built-in support for reading and writing a wide variety of audio file and data formats

  内置对多种音频文件和数据格式的读写支持

- Plug-in support for custom formats, audio synthesis, and processing (audio DSP)

  支持自定义格式、音频合成和处理的插件（音频数字信号处理器）

- A modular approach for constructing audio signal chains

  构建音频信号链的模块化方法

- Easy MIDI synchronization

  简易MIDI同步

- Support for scheduled playback and synchronization with access to timing and control information

  支持定时播放和同步，可访问定时和控制信息

- A standardized interface to all built-in and external hardware devices, regardless of connection type (USB, Firewire, PCI, and so on)

  所有内置和外部硬件设备的标准接口，无论连接类型如何（USB、Firewire、PCI等）

Audio queue objects give you access to incoming or outgoing raw audio data while the system mediates playback and recording, employs codecs (if needed), and makes hardware connections. To intercept and process audio as it proceeds through an audio queue object, you use the real-time, callback-based feature known as *audio queue processing taps*. This feature works for input (such as for recording) as well as output (such as for playback). Audio queue processing taps let you insert audio units or other forms of audio processing, effectively tapping into and modifying the data stream within an audio queue. You can also use this technology in a *siphon mode*, in which you gain access to the stream but do not modify it.

To learn more about the Core Audio framework, see *[Core Audio Framework Reference](https://developer.apple.com/documentation/coreaudio)*.

音频队列对象 允许你在 系统调解播放和录制、使用编解码器（如果需要）和进行硬件连接时访问传入或传出的原始音频数据。

要在音频通过音频队列对象时 截取和处理音频，可以使用实时的、基于回调的功能，即 `audio queue processing taps`。此功能可用于输入（例如用于录制）和输出（例如用于播放）。

音频队列处理抽头允许你 插入音频单元或其他形式的音频处理，有效地利用和修改音频队列中的数据流。您也可以在 虹吸模式（`siphon mode`） 下使用此技术，在这种模式下，您可以访问流，但不修改它。



***
### 5、GLKit

GLKit framework (`GLKit.framework`) helps reduce the effort required to create new shader-based apps or to port existing apps that rely on fixed-function vertex or fragment processing provided by earlier versions of OpenGL ES or OpenGL. In addition, the GLKit framework includes APIs that perform several optimized mathematical operations, reduce the effort in loading texture data, and provide standard implementations of commonly needed shader effects.

GLKit 框架 有助于更方便的 创建新的基于着色器的应用程序，或者移植现有的应用程序，这些应用程序依赖于早期版本的 OpenGL ES 或 OpenGL 提供的 固定函数顶点或片段处理。此外，GLKit 框架还包括一些api，这些 api 执行一些优化的数学操作，减少加载纹理数据的工作量，并提供通常需要的着色器效果的标准实现。



**Note:** GLKit requires an OpenGL context that supports the OpenGL 3.2 Core Profile. GLKit is not available to 32-bit apps in OS X.

To learn more about using GLKit in your app, see *[GLKit Framework Reference](https://developer.apple.com/documentation/glkit)*.

备注 ：GLKit 需要支持 OpenGL 3.2 核心概要文件（OpenGL 3.2 Core Profile.）的 OpenGL 上下文。GLKit不适用于OS X中的32位应用程序。

关于更多应用中使用 GLKit 的信息，可参阅  *[GLKit Framework Reference](https://developer.apple.com/documentation/glkit)*。



***
### 6、Instant Messaging 即时消息

OS X provides enables plugins for supporting messaging services:

OSX提供支持消息服务的插件：



- **Instant Message Service Plug-in** (`IMServicePlugin.framework`). The Instant Message Service Plug-in framework enables the creation of bundle plug-ins that let apps talk to instant-messaging services, such as iChat. It includes support for the buddy list, handle availability, handle icon, status messages, instant messaging, and group-chat messaging. 

  Instant Message Service Plug-in (`IMServicePlugin.framework`)，即时消息插件框架可以创建插件包来允许应用和即时消息服务通信，比如 iChat。它包括对好友列表、句柄可用性、句柄图标、状态消息、即时消息和群聊消息的支持。

For more information about using the Instant Message framework, see *Instant Message Programming Guide*. For more information about the Instant Message Service Plug-in framework, see *IMServicePlugIn Protocol Reference* and *IMServicePlugInInstantMessagingSupport Protocol Reference*

更多关于使用  Instant Message 框架的信息，可以阅读  `Instant Message Programming Guide`。

更多关于使用 Instant Message Service Plug-in 框架的信息，可以参阅 `IMServicePlugIn Protocol Reference*`and `IMServicePlugInInstantMessagingSupport Protocol Reference`。

***
### 7、OpenAL

The Open Audio Library (`OpenAL.framework`) is a cross-platform standard framework for delivering 3D audio. OpenAL lets you implement high-performance positional playback in games and other programs. Because it is a cross-platform standard, apps you write using OpenAL in OS X can be ported to run on many other platforms. 

Open Audio Library（`OpenAL.framework`）是一个跨平台的标准框架，用于交付3D音频。OpenAL允许您在游戏和其他程序中实现高性能的位置回放。因为它是一个跨平台的标准，所以你在OS X中使用OpenAL编写的应用程序可以移植到许多其他平台上运行。



OpenAL in OS X supports audio capture, exponential and linear distance models, location offsets, and spatial effects such as reverb and occlusion. The OS X implementation of OpenAL also supports certain Core Audio features, such as mixer sample rates. 

To learn about the OpenAL specification, visit [OpenAL](http://www.openal.org/).

OS X 中的 OpenAL  支持音频捕获、指数和线性距离模型、位置偏移以及空间效果（如混响和遮挡）。OpenAL的 OSX 实现，还支持某些核心音频特性，例如混音器采样率。

更多 OpenAL 的规范，可参阅  [OpenAL](http://www.openal.org/).



***
### 8、OpenGL

OpenGL is an industry wide standard for developing portable three-dimensional (3D) graphics apps. It is specifically designed for apps such as games that need a rich, robust framework for visualizing shapes in two and three dimensions. OpenGL is one of the most widely adopted graphics API standards, which makes code written for OpenGL portable and consistent across platforms. The OpenGL framework (`OpenGL.framework`) in OS X includes a highly optimized implementation of the OpenGL libraries that provides high-quality graphics at a consistently high level of performance. 

OpenGL是开发便携式三维（3D）图形应用程序的行业标准。它是专门为游戏等应用程序而设计的，这些应用程序需要一个丰富、健壮的框架来可视化二维和三维图形。OpenGL是最广泛采用的图形API标准之一，它使得为OpenGL编写的代码 具有可移植性 和跨平台的一致性。OSX 中的 OpenGL 框架包含一个高度优化的OpenGL 库的实现，它提供了高质量的图形和一致的高性能。



OpenGL offers a broad and powerful set of imaging functions, including texture mapping, hidden surface removal, alpha blending (transparency), antialiasing, pixel operations, viewing and modeling transformations, atmospheric effects (fog, smoke, and haze), and other special effects. Each OpenGL command directs a drawing action or causes a special effect, and developers can create lists of these commands for repetitive effects. Although OpenGL is largely independent of the windowing characteristics of each operating system, the standard defines special glue routines to enable OpenGL to work in an operating system’s windowing environment. The OS X implementation of OpenGL implements these glue routines to enable operation with Quartz Compositor.

OpenGL提供了一系列广泛而强大的成像功能，包括纹理映射、隐藏表面移除、alpha混合（透明度）、抗锯齿、像素操作、查看和建模转换、大气效果（雾、烟和霾）以及其他特殊效果。

每个OpenGL命令都指示一个绘图操作，或导致一个特殊的效果，开发人员可以创建这些命令的列表以获得重复的效果。尽管OpenGL在很大程度上独立于每个操作系统的窗口特性，但是标准定义了特殊的粘合例程，使 OpenGL 能够在操作系统的窗口环境中工作。OpenGL的OS X实现实现了这些粘合例程，以启用 Quartz Compositor 的操作。



OpenGL supports the ability to use multiple threads to process graphics data. OpenGL also supports pixel buffer objects, color-managed texture images in the sRGB color space, and 64-bit addressing. It also offers improvements in the shader programming API. 

OpenGL支持使用多线程处理图形数据的能力。OpenGL还支持像素缓冲区对象、sRGB 颜色空间中的颜色管理纹理图像和64位寻址。它还提供了对着色器编程API的改进。



OS X v10.7 added support for Open GL 3.2 Core, which added more extensions as baseline features. Note that routines and mechanisms found in OpenGL 1.*n* and OpenGL 2.*n* are deprecated, including the removal of the fixed-function pipeline that was the main approach to developing OpenGL 1.*n* apps. An OpenGL 3.2 app requires you to create your own shader strategy rather than assuming that a standard graphics pipeline will do everything. As a result, for simple apps you need to write more boilerplate code than was required by previous versions of OpenGL.

For information about using OpenGL in OS X, see *[OpenGL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html#//apple_ref/doc/uid/TP40001987)*. 

OSX 10.7 增加了对 OpenGL3.2核心 的支持，增加了更多的扩展作为基线特性。

注意，OpenGL 1.n 和OpenGL 2.n 中的例程和机制是不推荐使用的，它们包括删除了的 作为开发openGL 1.n应用程序的主要方法的固定函数管道。

OpenGL 3.2应用程序要求您创建自己的着色器策略，而不是假设标准的图形管道将执行所有操作。

因此，对于简单的应用程序，您需要编写比以前版本的OpenGL所需更多的样板代码。
有关在OS X中使用OpenGL的信息，请参阅  *[OpenGL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html#//apple_ref/doc/uid/TP40001987)*。

***
### 9、Quartz

The Quartz umbrella framework includes the following subframeworks. You should not link directly with any of the subframeworks; instead link with (and import) `Quartz.framework`.

Quartz 伞形框架包含下列子框架，使用子框架时，应引入  `Quartz.framework`，而不是直接引入子框架。

***
#### 9.1 Image Kit

The Image Kit (`ImageKit.framework`) is an Objective-C framework that makes it easy to incorporate powerful imaging services into your apps. This framework takes advantage of features in Quartz, Core Image, OpenGL, and Core Animation to provide an advanced and highly optimized development path for implementing the following features: 

Image Kit (`ImageKit.framework`) 是一个Objective-C框架，可以轻松地将强大的图像服务整合到应用程序中。该框架利用了Quartz、Core Image、OpenGL和Core Animation中的特性，为实现以下特性提供了一个高级的、高度优化的开发路径：

- Displaying images

  展示图片

- Rotating, cropping, and performing other image-editing operations 

  旋转、剪切和执行其他图像编辑操作

- Browsing for images 

  浏览图像

- Taking pictures using the built-in picture taker panel

  使用内置的拍照面板拍照

- Displaying slideshows 

  显示幻灯片

- Browsing for Core Image filters 

   Core Image 滤镜的浏览

- Displaying custom views for Core Image filters 

  显示核心图像过滤器的自定义视图

For more information on how to use Image Kit, see *[ImageKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/ImageKitProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004907)* and *Image Kit Reference Collection*.

更多使用 Image Kit 的信息，可参阅  *[ImageKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/ImageKitProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40004907)* and Image Kit Reference Collection。



***
#### 9.2 PDF Kit

PDF Kit (`PDFKit.framework`, a subframework of the Quartz framework) is a Cocoa framework for managing and displaying PDF content directly from your app’s windows and dialogs. You can embed a `PDFView` object in your window and give it a PDF file to display. The PDF view handles the rendering of the PDF content, handles copy-and-paste operations, and provides controls for navigating and setting the zoom level. Other classes let you get the number of pages in a PDF file, find text, manage selections, add annotations, and specify the behavior of some graphical elements, among other actions. 

For more information on PDF Kit, see *[PDFKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/PDFKitGuide/PDFKit_Prog_Intro/PDFKit_Prog_Intro.html#//apple_ref/doc/uid/TP40001863)*. 

PDF Kit  是一个Cocoa框架，用于 直接从应用程序的窗口和对话框 管理和显示PDF内容。您可以在窗口中嵌入一个 `PDFView` 对象，并给它一个PDF文件来显示。PDF视图处理 PDF内容的呈现，处理复制和粘贴操作，并提供导航和设置缩放级别。其他类帮助您获取 PDF文件中的页数、查找文本、管理选择、添加注释以及指定某些图形元素的行为等操作。

更多关于 PDF Kit 的信息可参阅  [PDFKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/PDFKitGuide/PDFKit_Prog_Intro/PDFKit_Prog_Intro.html#//apple_ref/doc/uid/TP40001863)。

***
#### 9.3 Quartz Composer

The Quartz Composer framework (`QuartzComposer.framework`) provides programmatic support for working with Quartz Composer compositions. It enables apps to load, play, and control compositions and to integrate them with Cocoa views, Core Animation layers, or OpenGL rendering.

For more information, see *[Quartz Composer Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/QuartzComposer/qc_intro/qc_intro.html#//apple_ref/doc/uid/TP40001357)*.

Quartz Composer 框架提供编程的方法来使用 Quartz Composer 组成。它允许应用装载、播放和控制组成，来和 Cocoa 视图、Core Animation layers，OpenGL 渲染来整合。

***
#### 9.4 Quick Look UI 快速预览UI

The Quick Look UI framework (`QuickLookUI.framework`) defines an interface for implementing a Quick Look preview panel, which displays the preview of a list of items. The framework also includes the capability for embedding a preview inside a view.

For an example of an app that implements Quick Look preview panels, see *[QuickLookDownloader](https://developer.apple.com/library/archive/samplecode/QuickLookDownloader/Introduction/Intro.html#//apple_ref/doc/uid/DTS40009082)*.

 Quick Look UI 框架定义了一个借口来实现快速预览面板，可以展示项目的列表。这个框架同样包含 在视图中 嵌入预览的功能。实现快速预览面板的样例，可以参考  *[QuickLookDownloader](https://developer.apple.com/library/archive/samplecode/QuickLookDownloader/Introduction/Intro.html#//apple_ref/doc/uid/DTS40009082)*。

***
### 10、Quartz Core

The Quartz Core framework (`QuartzCore.framework`) implements two important system technologies for graphics and imaging Core Animation and Core Image. 

 Quartz Core  框架实现了两个重要的 图形和图片  Core Animation 和 Core Image 系统技术。

***
#### 10.1 Core Animation 核心动画

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



***
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



***
### 11、QuickTime Kit

QTKit (`QTKit.framework`) is a deprecated Objective-C framework for manipulating QuickTime-based media. Use the AV Foundation framework instead; to learn more, see [AV Foundation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW25). 

QTKit 是一个过时的操作基于QuickTime 美体的框架，使用  AV Foundation 框架来替代。更多信息，可以参阅  [AV Foundation](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/MediaLayer/MediaLayer.html#//apple_ref/doc/uid/TP40001067-CH273-SW25)。

***
### 12、Scene Kit

The Scene Kit framework (`SceneKit.framework`) provides a high-level Objective-C API that helps you to efficiently load, manipulate, and render 3D scenes in your app. Scene Kit allows you to import Digital Asset Exchange files (`.dae` files) that are created by popular content-creation applications and gives you access to the objects, lights, cameras, and geometry data that define a 3D scene. Using an approach based on scene graphs, Scene Kit makes it simple to modify, animate, and render your 3D scenes. 

Scene Kit integrates with Image Kit, SpriteKit, and Core Animation, so you do not need advanced 3D graphical programming skills. For example, you can embed a 3D scene into a layer and then use Core Animation compositing capabilities to add overlays and backgrounds. You can also use Core Animation layers as textures for your 3D objects in 3D scenes. To learn how to use Scene Kit in your app, see *[SceneKit Programming Guide](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/SceneKit_PG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40012282)*.

Scene Kit 框架提供了高级的 OC API 来帮助你有效率的 加载、控制和渲染 3D 场景。Scene Kit 允许你导入  由流行的内容创建应用程序创建的 数字资源交换文件（`.dae` 文件），并允许您访问定义三维场景的对象、灯光、相机和几何数据 。使用 基于场景图的方法，Scene Kit  使修改、动画制作和渲染三维场景变得简单。

Scene Kit  集成了 Image Kit, SpriteKit, and Core Animation，因此你不需要高级的三维图形编程技能。

比如，你可以将 3D 场景 嵌入 layer 中，然后使用核心动画合成功能 添加覆盖和背景。也可以将核心动画层用作三维场景中三维对象的纹理。要了解如何在应用程序中使用 Scene Kit，请参阅  *[SceneKit Programming Guide](https://developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/SceneKit_PG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40012282)*。

***
### 13、Sprite Kit

The Sprite Kit framework (`SpriteKit.framework`) provides a graphics rendering and animation infrastructure that you can use to animate arbitrary textured images, or sprites. You use graphical tools to create the sprites. You then create scenes including sprites, light sources, emitters, and physics fields. Sprite Kit animates the scene you specify using a traditional animation loop, doing the work to render frames of animation efficiently using the graphics hardware.

 Sprite Kit 框架提供 图形渲染和动画基础设施的功能，你可以用来 设置任意纹理图像或精灵的动画。使用图形工具创建精灵。然后创建场景，包括精灵、光源、发射器和物理场。 Sprite Kit  使用传统动画循环设置指定场景的动画，使用图形硬件 有效地渲染动画帧。

Sprite kit includes basic sound playback support in addition to physics simulation. In addition, you can create complex special effects and texture atlases directly in Xcode. This combination of framework and tools makes Sprite Kit a good choice for games and other apps that require similar kinds of animation. Animated images created with Sprite Kit work well with SceneKit. To learn how to use Sprite Kit, see *[SpriteKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsAnimation/Conceptual/SpriteKit_PG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013043)*.

除了物理模拟之外，Sprite 工具包还包括基本的声音回放支持。此外，您可以直接在 Xcode中创建复杂的特殊效果和纹理图谱。这种 框架和工具的结合 使得Sprite工具包成为需要类似动画的游戏和其他应用程序的不错选择。使用Sprite工具包创建的动画图像 与 SceneKit很好地配合使用。更多  Sprite Kit 的信息, 可参阅 *[SpriteKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsAnimation/Conceptual/SpriteKit_PG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013043)*。



***
### 14、Other Media Layer Frameworks 其他媒体框架

The Media layer of OS X also has the following frameworks:

- **Audio Video Bridging** (`AudioVideoBridging.framework`). The Audio Video Bridging framework supports Audio Video Bridging (AVB) and implements the IEEE P1722.1 draft standard. AVB enhances the quality of service and provides guaranteed latency and bandwidth for media streams over an AVB network. Audio Video Bridging gives you access to the Entity discovery and control protocols of IEEE P1722.1 over an Ethernet network.

  Audio Video Bridging 框架支持 AVB 和  IEEE P1722.1 标准草案的实现。AVB提高了服务质量，并为 AVB 网络上的媒体流提供有保证的延迟和带宽。音频视频桥接 允许您通过以太网访问 IEEE P1722.1 的实体发现和控制协议。

  

- **Core Media** (`CoreMedia.framework`). The Core Media framework provides low-level audiovisual media objects and tools for managing them. It also defines the fundamental time representation used uniformly throughout AV Foundation.

  For information about using the Core Media framework, see *[Core Media Framework Reference](https://developer.apple.com/documentation/coremedia)*.

  核心媒体框架提供低级视听媒体对象和管理它们的工具。它还定义了在整个 AV Foundation 中统一使用的基本时间表示。关于使用  Core Media 框架的信息，可参阅  *[Core Media Framework Reference](https://developer.apple.com/documentation/coremedia)*。

  

- **Core Media I/O** (`CoreMediaIO.framework`). The Core Media I/O framework publishes the Device Abstraction Layer (DAL) plug-in API. This technology enables you to create plug-ins that can access media hardware and capture video and “muxed” (video combined with audio) streams. Core Media I/O is a replacement for the QuickTime VDig API.

  核心媒体I/O框架发布设备抽象层（DAL）插件API。此技术使您能够创建可以访问媒体硬件并捕获视频和“muxed”（视频与音频组合）流的插件。核心媒体I/O是QuickTime VDig API的替代品。

  

- **Core Video** (`CoreVideo.framework`). Core Video creates a bridge between QuickTime and the graphics card’s GPU to deliver hardware-accelerated video processing. Benefits of Core Video include filters and effects, per-pixel accuracy, and hardware scalability.

  For information about using the Core Video framework, see *[Core Video Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreVideo/CVProg_Intro/CVProg_Intro.html#//apple_ref/doc/uid/TP40001536)*. 

  核心视频在QuickTime 和 图形卡的GPU之间建立了一个桥梁，以提供硬件加速的视频处理。核心视频的好处包括过滤器和效果、每像素精度和硬件可扩展性。Core Video 的好处包括过滤器和效果、每像素精度和硬件可扩展性。

  

- **Disc Recording** (`DiscRecording.framework`). Disc Recording gives apps the ability to burn and erase CDs and DVDs. Your app specifies the content to be burned but the framework (`DiscRecording.framework`) takes over the process of buffering the data, generating the proper file format information, and communicating everything to the burner. 

  The Disc Recording UI framework (`DiscRecordingUI.framework`) provides a complete, standard set of windows for gathering information from the user and displaying the progress of the burn operation.

  For more information about the Disc Recording frameworks, see *Disc Recording Framework Reference* and *Disc Recording UI Framework Reference*. 

  Disc Recording 使应用程序能够刻录和擦除CD和DVD。您的应用程序指定要刻录的内容，但框架（DiscRecording.framework）接管缓冲数据、生成正确文件格式信息以及将所有内容传送到刻录机的过程。

  Disc Recording UI 框架 (`DiscRecordingUI.framework`) 提供一组完整的标准窗口，用于从用户收集信息并显示刻录操作的进度。
  有关光盘录制框架的详细信息，请参阅 `Disc Recording Framework Reference` and `Disc Recording UI Framework Reference`。 



- **DVD Playback** (`DVDPlayback.framework`). The DVD Playback framework embeds DVD viewer capabilities into an app. You use the framework to control various aspects of playback, including menu navigation, viewer location, angle selection, and audio track selection. You can play back DVD data from disc or from a local `VIDEO_TS` directory. 

  For more information about using the DVD Playback framework, see *[DVD Playback Services Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/DVDPlaybackGuide/dvdguide_intro/dvdguide_intro.html#//apple_ref/doc/uid/TP40002163)*.

  DVD Playback 框架 将 DVD查看器功能 嵌入到应用程序中。使用该框架可以控制回放的各个方面，包括菜单导航、查看器位置、角度选择和音频曲目选择。您可以从 光盘 或 本地视频目录（`VIDEO_TS`） 播放DVD数据。
  有关使用DVD播放框架的详细信息，请参见 *[DVD Playback Services Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/DVDPlaybackGuide/dvdguide_intro/dvdguide_intro.html#//apple_ref/doc/uid/TP40002163)*.

  

- **Image Capture Core** (`ImageCaptureCore.framework`). Image Capture Core helps you capture image data from scanners and digital cameras. The interfaces of the framework are device independent, so you can use them to gather data from any devices connected to the system. You can get a list of devices, retrieve information about a specific device or image, and retrieve the image data itself.

  This framework works in conjunction with the Image Capture Devices framework (`ICADevices.framework`) to communicate with imaging hardware. For information on using these frameworks, see *[Image Capture Applications Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/ImageCaptureServicesProgrammingGuide/01Introduction/01Introduction.html#//apple_ref/doc/uid/TP40005196)*. 

  Image Capture Core 帮助您从扫描仪和数码相机捕获图像数据。框架的接口与设备无关，因此可以使用它们从连接到系统的任何设备收集数据。您可以获取设备列表、检索有关特定设备或图像的信息，以及检索图像数据本身。

  此框架与  Capture Devices framework (`ICADevices.framework`) 一起与 与成像硬件通信。更多使用这些框架的信息，可以阅读  *[Image Capture Applications Programming Guide](https://developer.apple.com/library/archive/documentation/Carbon/Conceptual/ImageCaptureServicesProgrammingGuide/01Introduction/01Introduction.html#//apple_ref/doc/uid/TP40005196)*。

  

- **Video Toolbox** (`VideoToolbox.framework`). The Video Toolbox framework comprises the 64-bit replacement for the QuickTime Image Compression Manager. Video Toolbox provide services for video compression and decompression, and for conversion between raster image formats stored in Core Video pixel buffers.

  视频工具箱框架包含 QuickTime 图像压缩管理器（QuickTime Image Compression Manager ） 的64位替换。视频工具箱 为 视频压缩 和 解压缩，以及存储在 核心视频 像素缓冲区中的 光栅图像格式之间的转换提供服务。



***

伊织 2019-12-22（日）小雨

