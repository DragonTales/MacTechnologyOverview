# 【Mac Technology Overview】（九）OS X Frameworks

[toc]

***

The OS X frameworks provide the interfaces you need to write software for Mac. Some of these frameworks contain simple sets of interfaces while others contain multiple subframeworks. Where applicable, the tables in this appendix list the key prefixes used by the classes, methods, functions, types, or constants of the framework. You should avoid using any of the specified prefixes in your own symbol names. 

OSX 框架提供接口来编写 Mac 上的应用。这些框架中的一些包含简单的几组接口，一些则包含多个子框架。在适用的地方，本附录中的表列出了 框架的类，方法，函数，类型或常量所使用的键前缀。你可以在自己的符号名字钱避免使用这些前缀。



## 一、System Frameworks

Table A-1 describes the frameworks located in the `/System/Library/Frameworks` directory and lists the first version of OS X in which each became available. 

描述了  `/System/Library/Frameworks`  文件夹中的框架，也标记了最开始出现在 OSX 中的 OSX 版本。

| Name                                | First available | Prefixes                                                     | Description                                                  |
| :---------------------------------- | :-------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| `Accelerate.framework`              | 10.3            | `cblas`, `vDSP`, `vv`                                        | Umbrella framework for vector-optimized operations. See [Accelerate Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCGHCCJ). |
| `Accounts.framework`                | 10.8            | `AC`                                                         | Provides access to user accounts stored in the Accounts database. See *[Accounts Framework Reference](https://developer.apple.com/documentation/accounts)*. |
| `AddressBook.framework`             | 10.2            | `AB`, `ABV`                                                  | Provides access to the Address Book, which is a centralized database of user contact information. Apps that target OS X v10.11 or greater should use `Contacts.framework`. |
| `AGL.framework`                     | 10.0            | `AGL`, `GL`, `glm`, `GLM`, `glu`, `GLU`                      | Contains Carbon interfaces for OpenGL. See *[AGL Reference](https://developer.apple.com/documentation/agl/agl)*. |
| `AppKit.framework`                  | 10.0            | `NS`                                                         | Contains classes and methods for the Cocoa user-interface layer. In general, link to `Cocoa.framework` instead of this framework. See *[AppKit Framework Reference](https://developer.apple.com/documentation/appkit)*. |
| `AppKitScripting.framework`         | 10.0            | N/A                                                          | Deprecated. Use `AppKit.framework` instead.                  |
| `AppleScriptKit.framework`          | 10.0            | `ASK`                                                        | Contains interfaces for creating AppleScript plug-ins.       |
| `AppleScriptObjC.framework`         | 10.6            | `NS`                                                         | Contains Objective-C extensions for creating AppleScript plug-ins. |
| `ApplicationServices.framework`     | 10.0            | `AE`, `AX`, `ATSU`, `CG`, `CT`, `LS`, `PM`, `QD`, `UT`       | Umbrella framework for several app-level services. See [Application Services Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCFFIEG). |
| `AudioToolbox.framework`            | 10.0            | `AU`, `AUMIDI`                                               | Contains interfaces for getting audio stream data, routing audio signals through audio units, converting between audio formats, and playing back music. See *[Audio Toolbox Framework Reference](https://developer.apple.com/documentation/audiotoolbox)*. |
| `AudioUnit.framework`               | 10.0            | `AU`                                                         | Contains interfaces for defining Core Audio plug-ins. See *[Audio Unit Framework Reference](https://developer.apple.com/documentation/audiounit)*. |
| `AudioVideoBridging.framework`      | 10.8            | `AVB`                                                        | Supports Audio Video Bridging (AVB) and implements the IEEE P1722.1 draft standard. |
| `Automator.framework`               | 10.4            | `AM`                                                         | Umbrella framework for creating Automator plug-ins. See [Automator Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCHCJFJ). |
| `AVFoundation.framework`            | 10.7            | `AV`                                                         | Provides interfaces for playing, recording, inspecting, and editing audiovisual media. See *AVFoundation Audio Functions*. |
| `AVKit.framework`                   | 10.9            | `AV`                                                         | Provides API for media playback including user controls, chapter navigation, subtitles, and closed captioning. See *[AV Kit Framework Reference](https://developer.apple.com/documentation/avkit)* |
| `CalendarStore.framework`           | 10.5            | `Cal`                                                        | Deprecated. Use Event Kit instead. See [Event Kit](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40001067-CH270-SW26). |
| `Carbon.framework`                  | 10.0            | `HI`, `HR`, `ICA`, `ICD`, `Ink`, `Nav`, `OSA`, `PM`, `SFS`,`SR` | Umbrella framework for Carbon-level services. See [Carbon Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCFGHBB). |
| `CFNetwork.framework`               | 10.3            | `CF`                                                         | Contains interfaces for network communication using HTTP, sockets, and Bonjour. See *[CFNetwork Framework Reference](https://developer.apple.com/documentation/cfnetwork)*. |
| `CloudKit.framework`                | 10.10           | `CK`                                                         | Provides a conduit for moving data between your app and iCloud that can be used for all types of data. It also gives you control of when transfers occur. See *[CloudKit Quick Start](https://developer.apple.com/library/archive/documentation/DataManagement/Conceptual/CloudKitQuickStart/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014987)* or *[CloudKit Framework Reference](https://developer.apple.com/documentation/cloudkit)*. |
| `Cocoa.framework`                   | 10.0            | `NS`                                                         | Wrapper for including the Cocoa frameworks `AppKit.framework`, `Foundation.framework`, and `CoreData.framework`. |
| `Collaboration.framework`           | 10.5            | `CB`                                                         | Contains interfaces for managing identity information. See *[Collaboration Framework Reference](https://developer.apple.com/documentation/collaboration)*. |
| `Contacts.framework`                | 10.11           | `CN`                                                         | Provides access to the Contacts store, which is a centralized database of user contact information. See *[Contacts Framework Reference](https://developer.apple.com/documentation/contacts)*. |
| `CoreAudio.framework`               | 10.0            | `Audio`                                                      | Contains the hardware abstraction layer interface for manipulating audio. See *[Core Audio Framework Reference](https://developer.apple.com/documentation/coreaudio)*. |
| `CoreBluetooth.framework`           | 10.10           | `CB`                                                         | Contains the classes used for communicating with Bluetooth Low Energy devices. See *[Core Bluetooth Framework Reference](https://developer.apple.com/documentation/corebluetooth)* |
| `CoreAudioKit.framework`            | 10.4            | `AU`                                                         | Contains Objective-C interfaces for audio unit custom views. See *[CoreAudioKit Framework Reference](https://developer.apple.com/documentation/coreaudiokit)*. |
| `CoreData.framework`                | 10.4            | `NS`                                                         | Contains interfaces for managing your app’s data model. See *[Core Data Framework Reference](https://developer.apple.com/documentation/coredata)*. |
| `CoreFoundation.framework`          | 10.0            | `CF`                                                         | Provides fundamental software services, including abstractions for common data types, string utilities, collection utilities, plug-in support, resource management, preferences, and XML parsing. See *[Core Foundation Framework Reference](https://developer.apple.com/documentation/corefoundation)*. |
| `CoreGraphics.framework`            | 10.0            | `CG`                                                         | Contains the Quartz interfaces for creating graphic content and rendering that content to the screen. See *Core Graphics Framework Reference*. |
| `CoreImage.framework`               | 10.4            | `CI`                                                         | An image processing and analysis technology designed to provide near real-time processing for still and video images. See *[Core Image Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/CoreImaging/ci_intro/ci_intro.html#//apple_ref/doc/uid/TP30001185)*. |
| `CoreLocation.framework`            | 10.6            | `CL`                                                         | Provides interfaces for determining the geographical location of a computer. See *[Core Location Framework Reference](https://developer.apple.com/documentation/corelocation)*. |
| `CoreMedia.framework`               | 10.7            | `CM`                                                         | Contains low-level interfaces for for managing and and playing audio-visual media in an app. See *[Core Media Framework Reference](https://developer.apple.com/documentation/coremedia)*. |
| `CoreMediaIO.framework`             | 10.7            | `CMIO`                                                       | Contains interfaces of the Device Abstraction Layer (DAL) used for creating plug-ins that can access media hardware. |
| `CoreMIDI.framework`                | 10.0            | `MIDI`                                                       | Contains utilities for implementing MIDI client programs. See *[Core MIDI Framework Reference](https://developer.apple.com/documentation/coremidi)*. |
| `CoreMIDIServer.framework`          | 10.0            | `MIDI`                                                       | Deprecated in OS X v10.6. Use `CoreMIDI.framework` instead.  |
| `CoreServices.framework`            | 10.0            | `CF`, `DCS`, `MD`, `SK`, `WS`                                | Umbrella framework for system-level services. See [Core Services Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCHJEBB). |
| `CoreText.framework`                | 10.5            | `CT`                                                         | Contains the interfaces for performing text layout and display. See *[Core Text Reference Collection](https://developer.apple.com/documentation/coretext)*. |
| `CoreVideo.framework`               | 10.5            | `CV`                                                         | Contains interfaces for managing video-based content. See *[Core Video Framework Reference](https://developer.apple.com/documentation/corevideo)*. |
| `CoreWLAN.framework`                | 10.6            | `CW`                                                         | Contains interfaces for managing wireless networks. See *[CoreWLAN Framework Reference](https://developer.apple.com/documentation/corewlan)*. |
| `CryptoTokenKit.framework`          | 10.10           | `TK`                                                         | Contains interface for using smart cards. See *[CryptoTokenKit Framework Reference](https://developer.apple.com/documentation/cryptotokenkit)*. |
| `DirectoryService.framework`        | 10.0            | `ds`                                                         | Deprecated in OS X v10.6. Use `OpenDirectory.framework` instead. |
| `DiscRecording.framework`           | 10.2            | `DR`                                                         | Contains interfaces for burning data to CDs and DVDs. See *Disc Recording Framework Reference*. |
| `DiscRecordingUI.framework`         | 10.2            | `DR`                                                         | Contains the user interface layer for interacting with users during the burning of CDs and DVDs. See *Disc Recording UI Framework Reference*. |
| `DiskArbitration.framework`         | 10.4            | `DA`                                                         | Contains interfaces for getting information related to local and remote volumes. See *[Disk Arbitration Framework Reference](https://developer.apple.com/documentation/diskarbitration)*. |
| `DrawSprocket.framework`            | 10.0            | `DSp`                                                        | Contains the game sprocket component for drawing content to the screen. |
| `DVComponentGlue.framework`         | 10.0            | `IDH`                                                        | Contains interfaces for communicating with digital video devices, such as video cameras. |
| `DVDPlayback.framework`             | 10.3            | `DVD`                                                        | Contains interfaces for embedding DVD playback features into your app. See *DVD Playback Framework Reference*. |
| `EventKit.framework`                | 10.8            | `EK`                                                         | Provides an interface for accessing a user’s calendar events and reminder items. See *[Event Kit Framework Reference](https://developer.apple.com/documentation/eventkit)*. |
| `ExceptionHandling.framework`       | 10.0            | `NS`                                                         | Contains exception-handling classes for Cocoa apps. See *[Exception Handling Framework Reference](https://developer.apple.com/documentation/exceptionhandling)*. |
| `FinderSync.framework`              | 10.10           | `FI`                                                         | Provides API for enhancing the Finder’s user interface by adding badges, shortcut menu items, and toolbar buttons. See *[Finder Sync Framework Reference](https://developer.apple.com/documentation/findersync)* |
| `ForceFeedback.framework`           | 10.2            | `FF`                                                         | Contains interfaces for communicating with force feedback–enabled devices. See *[Force Feedback Framework Reference](https://developer.apple.com/documentation/forcefeedback)*. |
| `Foundation.framework`              | 10.0            | `NS`                                                         | Contains the classes and methods for the Cocoa Foundation layer. If you are creating a Cocoa app, linking to the Cocoa framework is preferable. See *[Foundation Framework Reference](https://developer.apple.com/documentation/foundation)*. |
| `FWAUserLib.framework`              | 10.2            | `FWA`                                                        | Contains interfaces for communicating with FireWire-based audio devices. See *[FWAUserLib.h Reference](https://developer.apple.com/documentation/fwauserlib/fwauserlib.h)*. |
| `GameController.framework`          | 10.9            | `GC`                                                         | A collection of classes for discovering and interacting with connected game controllers. See *[Game Controller Programming Guide](https://developer.apple.com/library/archive/documentation/ServicesDiscovery/Conceptual/GameControllerPG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013276)* |
| `GameKit.framework`                 | 10.8            | `GK`                                                         | Provides APIs that allow your app to participate in Game Center. See *[Game Kit Framework Reference](https://developer.apple.com/documentation/gamekit)*. |
| `GLKit.framework`                   | 10.8            | `GLK`                                                        | Provides functions and classes that reduce the effort required to create new shader-based apps or to port existing apps that rely on fixed-function vertex or fragment processing provided by earlier versions of OpenGL ES or OpenGL. See *[GLKit Framework Reference](https://developer.apple.com/documentation/glkit)*. |
| `GLUT.framework`                    | 10.0            | `glut`, `GLUT`                                               | Contains interfaces for the OpenGL Utility Toolkit, which provides a platform-independent interface for managing windows. |
| `GSS.framework`                     | 10.7            | `gss`                                                        | Contains interfaces for Generic Security Services Application Program Interface (GSSAPI). |
| `Hypervisor.framework`              | 10.10           | `hv`                                                         | Allows virtualization vendors to build virtualization solutions on top of OS X without needing to deploy third-party kernel extensions (KEXTs). See *Hypervisor Framework Reference*. |
| `ICADevices.framework`              | 10.3            | `ICD`                                                        | Contains low-level interfaces for communicating with digital devices such as scanners and cameras. See [Carbon Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCFGHBB). |
| `ImageCaptureCore.framework`        | 10.6            | `IC`                                                         | Contains Objective-C interfaces for communicating with digital devices such as scanners and cameras. |
| `ImageIO.framework`                 | 10.4            | `CGImage`                                                    | Contains interfaces for importing and exporting image data.  |
| `IMServicePlugIn.framework`         | 10.7            | `IM`                                                         | Contains interfaces for building third-party plug-ins for Chat services. Umbrella framework for `IMServicePlugInSupport.framework`. |
| `InputMethodKit.framework`          | 10.5            | `IMK`                                                        | Contains interfaces for developing new input methods, which are modules that handle text entry for complex languages. See *[Input Method Kit Framework Reference](https://developer.apple.com/documentation/inputmethodkit)*. |
| `InstallerPlugins.framework`        | 10.4            | `IFX`                                                        | Contains interfaces for creating plug-ins that run during software installation sessions. See *[Installer JavaScript Reference](https://developer.apple.com/documentation/installerjs)*. |
| `InstantMessage.framework`          | 10.4            | `FZ`, `IM`                                                   | Deprecated in OS X v10.9. Do not use.                        |
| `IOBluetooth.framework`             | 10.2            | `IO`                                                         | Contains interfaces for communicating with Bluetooth devices. |
| `IOBluetoothUI.framework`           | 10.2            | `IO`                                                         | Contains the user interface layer for interacting with users manipulating Bluetooth devices. |
| `IOKit.framework`                   | 10.0            | `IO`, `IOBSD`, `IOCF`                                        | Contains the main interfaces for creating user-space device drivers and for interacting with kernel-resident drivers from user space. See *[IOKitLib.h Reference](https://developer.apple.com/documentation/iokit/iokitlib.h)*. |
| `IOSurface.framework`               | 10.6            | `IO`                                                         | Contains low-level interfaces for sharing graphics surfaces between apps. See *[IOSurface Framework Reference](https://developer.apple.com/documentation/iosurface)*. |
| `JavaFrameEmbedding.framework`      | 10.5            | N/A                                                          | Contains interfaces for embedding Java frames in Objective-C code. |
| `JavaScriptCore.framework`          | 10.5            | `JS`                                                         | Contains the library and resources for executing JavaScript code within an HTML page. (Prior to OS X v10.5, this framework was part of `WebKit.framework`. See *[JavaScriptCore Framework Reference](https://developer.apple.com/documentation/javascriptcore)*. |
| `JavaVM.framework`                  | 10.0            | `JAWT`, `JDWP`, `JMM`, `JNI`, `JVMDI`, `JVMPI`, `JVMTI`      | Deprecated in OS X v10.7. Use Oracle Java instead.           |
| `Kerberos.framework`                | 10.0            | `GSS`, `KL`, `KRB`, `KRB5`                                   | Contains interfaces for using the Kerberos network authentication protocol. |
| `Kernel.framework`                  | 10.0            | *numerous*                                                   | Contains the interfaces for kernel-extension development, including Mach, BSD, `libkern`, I/O Kit, and the various families built on top of I/O Kit. See *[Kernel Framework Reference](https://developer.apple.com/documentation/kernel)*. |
| `LatentSemanticMapping.framework`   | 10.5            | `LSM`                                                        | Contains interfaces for classifying text based on latent semantic information. See *[Latent Semantic Mapping Reference](https://developer.apple.com/documentation/latentsemanticmapping)*. |
| `LDAP.framework`                    | 10.0            | N/A                                                          | Do not use.                                                  |
| `LocalAuthentication.framework`     | 10.10           | `LA`                                                         | Contains API for requesting authentication from users using specified policies. See *[Local Authentication Framework Reference](https://developer.apple.com/documentation/localauthentication)* |
| `MapKit.framework`                  | 10.9            | `MK`                                                         | Provides classes and protocols for embedding maps into the windows and views of your apps. Includes support for annotations, overlays, and reverse-geocoding lookups. See *[Map Kit Framework Reference](https://developer.apple.com/documentation/mapkit)* |
| `MediaAccessibility.framework`      | 10.9            | `MA`                                                         | Provides API to access user preferences for captions that can accompany media, such as closed captioning. See *[Media Accessibility Framework Reference](https://developer.apple.com/documentation/mediaaccessibility)* |
| `MediaLibrary.framework`            | 10.9            | `ML`                                                         | Provides a read-only data model representing a user’s collections of images, audio, and video. See *[Media Library Framework Reference](https://developer.apple.com/documentation/medialibrary)* |
| `Message.framework`                 | 10.0            | `AS`, `MF`, `PO`, `POP`, `RSS`, `TOC`, `UR`, `URL`           | Contains Cocoa extensions for mail delivery.                 |
| `Metal.framework`                   | 10.11           | MTL                                                          | Provides GPU-accelerated 3D graphics rendering and data-parallel computation workloads. See *[Metal Programming Guide](https://developer.apple.com/library/archive/documentation/Miscellaneous/Conceptual/MetalProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40014221)* and related references. |
| `MetalKit.framework`                | 10.11           | MTK                                                          | Contains functions and classes that reduce the effort required to create a Metal application. See *[MetalKit Framework Reference](https://developer.apple.com/documentation/metalkit)* and *[MetalKit Functions Reference](https://developer.apple.com/documentation/metalkit/metalkit_functions)*. |
| `ModelIO.framework`                 | 10.11           | MDL                                                          | Provides classes that support import, export, and editing of 3D model assets and related resources. See *[ModelIO Framework Reference](https://developer.apple.com/documentation/modelio)*. |
| `MultipeerConnectivity.framework`   | 10.10           | `MC`                                                         | Contains API for finding and communicating with services provided by nearby devices using infrastructure Wi-Fi networks, peer-to-peer Wi-Fi, and Bluetooth personal area networks. See *[Multipeer Connectivity Framework Reference](https://developer.apple.com/documentation/multipeerconnectivity)*. |
| `NetFS.framework`                   | 10.6            | `NetFS`                                                      | Contains interfaces for working with network file systems.   |
| `NetworkExtension.framework`        | 10.11           | `NE, NW`                                                     | Provides support for configuring and controlling Virtual Private Network (VPN) tunnels. See *[Network Extension Framework Reference](https://developer.apple.com/documentation/networkextension)*. |
| `NotificationCenter.framework`      | 10.10           | `NC, NS`                                                     | Contains the interfaces for creating and managing extensions in the Today view of the Notification Center. See *[Notification Center Framework Reference](https://developer.apple.com/documentation/notificationcenter)* |
| `OpenAL.framework`                  | 10.4            | `AL`                                                         | Contains the interfaces for OpenAL, a cross-platform 3D audio delivery library. |
| `OpenCL.framework`                  | 10.6            | `CL`, `cl`                                                   | Contains the interfaces for distributing general-purpose computational tasks across the available GPUs and CPUs of a computer. See *[OpenCL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/OpenCL_MacProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008312)*. |
| `OpenDirectory.framework`           | 10.6            | `OD`                                                         | Contains Objective-C interfaces for managing Open Directory information. See *[Open Directory Programming Guide](https://developer.apple.com/library/archive/documentation/Networking/Conceptual/Open_Directory/Introduction/Introduction.html#//apple_ref/doc/uid/TP40000917)*. |
| `OpenGL.framework`                  | 10.0            | `CGL`, `GL`, `glu`, `GLU`                                    | Contains the interfaces for OpenGL, which is a cross-platform 2D and 3D graphics rendering library. See *[OpenGL Programming Guide for Mac](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html#//apple_ref/doc/uid/TP40001987)*. |
| `OSAKit.framework`                  | 10.4            | `OSA`                                                        | Contains Objective-C interfaces for managing and executing OSA-compliant scripts from Cocoa apps. |
| `PCSC.framework`                    | 10.0            | `MSC`, `Scard`, `SCARD`                                      | Contains interfaces for interacting with smart card devices. |
| `PreferencePanes.framework`         | 10.0            | `NS`                                                         | Contains interfaces for implementing custom modules for the System Preferences app. See *Preference Panes Framework Reference*. |
| `PubSub.framework`                  | 10.5            | `PS`                                                         | Contains interfaces for subscribing to RSS and Atom feeds. See *Publication Subscription Framework Reference*. |
| `QTKit.framework`                   | 10.4            | `QT`                                                         | Deprecated in OS X v10.9. Use `AVFoundation.framework` instead. |
| `Quartz.framework`                  | 10.4            | `GF`, `PDF`, `QC`, `QCP`                                     | Umbrella framework for Quartz services. See [Quartz Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCJECHA). |
| `QuartzCore.framework`              | 10.4            | `CA`,`CI`, `CV`                                              | Contains the interfaces for Core Image, Core Animation, and Core Video. See *Quartz Core Framework Reference*. |
| `QuickLook.framework`               | 10.5            | `QL`                                                         | Contains interfaces for generating thumbnail previews of documents. See *Quick Look Framework Reference for Mac*. |
| `QuickTime.framework`               | 10.0            | N/A                                                          | Deprecated in OS X v10.9. Use `AVFoundation.framework` and `AVKit.framework` instead. |
| `Ruby.framework`                    | 10.5            | N/A                                                          | Contains interfaces for the Ruby scripting language.         |
| `SceneKit.framework`                | 10.8            | `SCN`                                                        | Provides a high-level, Objective-C API to efficiently load, manipulate, and render 3D scenes in an app. See *[SceneKit Framework Reference](https://developer.apple.com/documentation/scenekit)*. |
| `ScreenSaver.framework`             | 10.0            | N/A                                                          | Contains interfaces for writing screen savers. See *[Screen Saver Framework Reference](https://developer.apple.com/documentation/screensaver)*. |
| `Scripting.framework`               | 10.0            | `NS`                                                         | Deprecated. Use `Foundation.framework` instead.              |
| `ScriptingBridge.framework`         | 10.5            | `SB`                                                         | Contains interfaces for running scripts from Objective-C code. See *[Scripting Bridge Framework Reference](https://developer.apple.com/documentation/scriptingbridge)*. |
| `Security.framework`                | 10.0            | `CSSM`, `Sec`                                                | Contains interfaces for system-level user authentication and authorization. See *[Security Framework Reference](https://developer.apple.com/documentation/security)*. |
| `SecurityFoundation.framework`      | 10.3            | `Sec`                                                        | Contains Cocoa interfaces for authorizing users. See *[Security Foundation Framework Reference](https://developer.apple.com/documentation/securityfoundation)*. |
| `SecurityInterface.framework`       | 10.3            | `PSA`, `SF`                                                  | Contains the user interface layer for authorizing users in Cocoa apps. See *[Security Interface Framework Reference](https://developer.apple.com/documentation/securityinterface)*. |
| `ServiceManagement.framework`       | 10.6            | `SM`                                                         | Contains interfaces for loading, unloading and managing `launchd` services. See *[Service Management Framework Reference](https://developer.apple.com/documentation/servicemanagement)*. |
| `Social.framework`                  | 10.8            | `SL`                                                         | Provides an API for sending requests to supported social networking services that can perform operations on behalf of users. See *[Social Framework Reference](https://developer.apple.com/documentation/social)*. |
| `SpriteKit.framework`               | 10.9            | `SK`                                                         | Provides API for animating arbitrary textured images, or sprites. It includes sound playback, a physics engine, and a rendering loop. See *[SpriteKit Programming Guide](https://developer.apple.com/library/archive/documentation/GraphicsAnimation/Conceptual/SpriteKit_PG/Introduction/Introduction.html#//apple_ref/doc/uid/TP40013043)* |
| `StoreKit.framework`                | 10.7            | `SK`                                                         | Supports requesting payment from a user to purchase additional functionality or content from the Mac App Store. See *[Store Kit Framework Reference](https://developer.apple.com/documentation/storekit)*. |
| `SyncServices.framework`            | 10.4            | `ISync`                                                      | Deprecated in OS X v10.7. Use `Contacts.framework` or `Calendar.framework` instead. |
| `System.framework`                  | 10.0            | N/A                                                          | Do not use.                                                  |
| `SystemConfiguration.framework`     | 10.0            | `SC`                                                         | Contains interfaces for accessing network configuration and reachability information. See *[System Configuration Framework Reference](https://developer.apple.com/documentation/systemconfiguration)*. |
| `Tcl.framework`                     | 10.3            | `Tcl`                                                        | Contains interfaces for accessing the system’s Tcl interpreter from an app. |
| `Tk.framework`                      | 10.4            | `Tk`                                                         | Contains interfaces for accessing the system’s Tk toolbox from an app. |
| `TWAIN.framework`                   | 10.2            | `TW`                                                         | Contains interfaces for accessing TWAIN-compliant image-scanning hardware. |
| `vecLib.framework`                  | 10.0            | N/A                                                          | Deprecated. Use `Accelerate.framework` instead. See [Accelerate Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCGHCCJ). |
| `VideoDecodeAcceleration.framework` | 10.7            | `VDA`                                                        | Deprecated in OS X v10.11. Use `VideoToolbox.framework` instead. |
| `VideoToolbox.framework`            | 10.8            | `VT`                                                         | Comprises the 64-bit replacement for the QuickTime Image Compression Manager. |
| `WebKit.framework`                  | 10.2            | `DOM`, `Web`                                                 | Umbrella framework for rendering HTML content. See [WebKit Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCEIBGF). |
| `XgridFoundation.framework`         | 10.4            | `XG`                                                         | Deprecated in OS X v10.8.Contains interfaces for connecting to and managing computing cluster software. |





***

##  二、umbrella frameworks

OS X contains several umbrella frameworks for major areas of functionality. Umbrella frameworks group several related frameworks into a larger framework that can be included in your project. When writing software, link your project against the umbrella framework; do not try to link directly to any of its subframeworks. The following sections describe the contents of the umbrella frameworks in OS X. 

OS X包含几个主要功能领域的总体框架。总体框架将几个相关的框架组合到一个大的框架中，可以被引入你的项目。编写软件时，将您的项目与伞式框架链接；不要直接使用它的子框架。下面部分描述了OSX 中的总体框架。



***

### 1、Accelerate Framework

Table A-2 lists the subframeworks of the Accelerate framework (`Accelerate.framework`). If you are developing apps for earlier versions of OS X, `vecLib.framework` is available as a standalone framework. 

下表列出了 Accelerate 框架包含的框架。当你在开发早起版本的 OSX 时，`vecLib.framework` 可以作为独立的框架使用。

| Subframework       | Description                                                  |
| :----------------- | :----------------------------------------------------------- |
| `vecLib.framework` | Contains vector-optimized interfaces for performing math, big-number, and DSP calculations, among others. |
| `vImage.framework` | Contains vector-optimized interfaces for manipulating image data. |



***

### 2、Application Services Framework

Table A-3 lists the subframeworks of the Application Services framework (`ApplicationServices.framework`) that are not links to top level frameworks. These frameworks provide C-based interfaces and are intended primarily for Carbon apps, although other programs can use them. The listed frameworks are available in all versions of OS X unless otherwise noted.

下表列出了未链接到顶层框架的 Application Services 的子框架。这些框架提供了基于C 的接口，主要用于Carbon 应用；虽然其他程序可以使用他们。除非另有说明，这些框架可以在所有 OSX 版本中使用。



| Subframework                | Description                                                  |
| :-------------------------- | :----------------------------------------------------------- |
| `ATS.framework`             | Deprecated in OS X v10.8. Use `CoreText.framework` instead.  |
| `ColorSync.framework`       | Contains interfaces for color matching using ColorSync.      |
| `HIServices.framework`      | Contains interfaces for accessibility, Internet Config, the pasteboard, the Process Manager, and the Translation Manager. Available in OS X v10.2 and later. |
| `LangAnalysis.framework`    | Contains the Language Analysis Manager interfaces.           |
| `PrintCore.framework`       | Contains the Core Printing Manager interfaces.               |
| `QD.framework`              | Contains the QuickDraw interfaces.                           |
| `SpeechSynthesis.framework` | Contains the Speech Manager interfaces.                      |



***

### 3、Automator Framework

Table A-4 lists the subframeworks of the Automator framework (`Automator.framework`). 



| Subframework             | Description                                                  |
| :----------------------- | :----------------------------------------------------------- |
| `MediaBrowser.framework` | Contains private interfaces for managing Automator plug-ins. |



***

### 4、Carbon Framework

Table A-5 lists the subframeworks of the Carbon framework (`Carbon.framework`). The listed frameworks are available in all versions of OS X unless otherwise noted.



| Subframework                   | Description                                                  |
| :----------------------------- | :----------------------------------------------------------- |
| `CarbonSound.framework`        | Deprecated in OS X v10.5. Use `CoreAudio.framework` instead. |
| `CommonPanels.framework`       | Contains interfaces for displaying the Font window, Color window, and some network-related dialogs. |
| `Help.framework`               | Contains interfaces for launching and searching Apple Help.  |
| `HIToolbox.framework`          | Deprecated in OS X v10.7. Use `Cocoa.framework` instead.     |
| `HTMLRendering.framework`      | Contains interfaces for rendering HTML content. The WebKit framework is the preferred framework for HTML rendering. See [WebKit Framework](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/OSX_Technology_Overview/SystemFrameworks/SystemFrameworks.html#//apple_ref/doc/uid/TP40001067-CH210-BBCEIBGF). |
| `ImageCapture.framework`       | Contains interfaces for capturing images from digital cameras. This framework works in conjunction with the Image Capture Devices framework (`ICADevices.framework`). |
| `Ink.framework`                | Contains interfaces for managing pen-based input. (Ink events are defined with the Carbon Event Manager.) |
| `NavigationServices.framework` | Contains interfaces for displaying file navigation dialogs.  |
| `OpenScripting.framework`      | Contains interfaces for writing scripting components and interacting with those components to manipulate and execute scripts. |
| `Print.framework`              | Contains the Carbon Printing Manager interfaces for displaying printing dialogs and extensions. |
| `SecurityHI.framework`         | Deprecated in OS X v10.9. Use `Security.framework` instead.  |
| `SpeechRecognition.framework`  | Contains the Speech Recognition Manager interfaces.          |



***

### 5、Core Services Framework

Table A-6 lists the subframeworks of the Core Services framework (`CoreServices.framework`). These frameworks provide C-based interfaces and are intended primarily for Carbon apps, although other programs can use them. The listed frameworks are available in all versions of OS X unless otherwise noted.



| Subframework                   | Description                                                  |
| :----------------------------- | :----------------------------------------------------------- |
| `AE.framework`                 | Contains interfaces for creating and manipulating Apple events and making apps scriptable. |
| `CarbonCore.framework`         | Contains interfaces for many legacy Carbon Managers. Most of the APIs in this framework are deprecated in OS X v10.8 (for more information, see *[Carbon Core Deprecations](https://developer.apple.com/library/archive/releasenotes/General/CarbonCoreDeprecations/index.html#//apple_ref/doc/uid/TP40012224)*). |
| `DictionaryServices.framework` | Provides dictionary lookup capabilities.                     |
| `FSEvents.framework`           | Provides a mechanism to notify clients about directories to re-scan to keep internal data structures up-to-date with the true state of the file system. |
| `LaunchServices.framework`     | Contains interfaces for launching apps.                      |
| `Metadata.framework`           | Contains interfaces for managing Spotlight metadata.         |
| `OSServices.framework`         | Contains interfaces for Open Transport and many hardware-related legacy Carbon managers. |
| `SearchKit.framework`          | Contains interfaces for the Search Kit.                      |



***
### 6、Quartz Framework

Table A-7 lists the subframeworks of the Quartz framework (`Quartz.framework`). 



| Subframework               | Description                                                  |
| :------------------------- | :----------------------------------------------------------- |
| `ImageKit.framework`       | Contains Objective-C interfaces for finding, browsing, and displaying images. |
| `PDFKit.framework`         | Contains Objective-C interfaces for displaying and managing PDF content. |
| `QuartzComposer.framework` | Contains Objective-C interfaces for playing Quartz Composer compositions in an app. |
| `QuartzFilters.framework`  | Contains Objective-C interfaces for managing and applying filter effects to a graphics context. |
| `QuickLookUI.framework`    | Contains Objective-C interfaces for creating and managing a Quick Look preview panel, which is a UI object that displays preview items. |



***
### 7、WebKit Framework

Table A-8 lists the subframeworks of the WebKit framework (`WebKit.framework`). 



| Subframework        | Description                                                  |
| :------------------ | :----------------------------------------------------------- |
| `WebCore.framework` | Contains the library and resources for rendering HTML content in an HTMLView control. |



***
## 二、Xcode Frameworks

Xcode and all of its supporting tools and libraries reside in a portable directory structure. This directory structure makes it possible to have multiple versions of Xcode installed on a single system or to have Xcode installed on a portable hard drive that you plug in to your computer when you need to do development. This portability means that the frameworks required by the developer tools are installed in the `/Library/Frameworks` directory, where `` is the path to the Xcode installation directory. Table A-9 lists the frameworks that are located in this directory.



| Framework          | First available | Prefixes | Description                                            |
| :----------------- | :-------------- | :------- | :----------------------------------------------------- |
| `XCTest.framework` | Xcode 5         | `XC`     | Interfaces for implementing unit tests in Objective-C. |

***

## 三、System Libraries

Some specialty libraries at the BSD level are not packaged as frameworks. Instead, OS X includes many dynamic libraries in the `/usr/lib` directory and its subdirectories. Dynamic shared libraries are identified by their `.dylib` extension. Header files for the libraries are located in the `/usr/include` directory. 

OS X uses symbolic links to point to the most current version of most libraries. When linking to a dynamic shared library, use the symbolic link instead of a link to a specific version of the library. Library versions may change in future versions of OS X. If your software is linked to a specific version, that version might not always be available on the user’s system.







***