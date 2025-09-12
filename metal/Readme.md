
- [AppKit Toplevel Doc](https://developer.apple.com/documentation/appkit)
- [NSApplication](https://developer.apple.com/documentation/appkit/nsapplication)
- [msg_send! appkit](https://www.google.com/search?q=msg_send!+appkit&rlz=1C5OZZY_enUS1141US1141&oq=msg_send!+appkit&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIHCAEQIRigATIHCAIQIRigATIHCAMQIRigATIHCAQQIRiPAjIHCAUQIRiPAtIBCDUzODRqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8)

---

#### NSApp cocoa

In the macOS and iOS Cocoa development environments, NSApp is a global pointer to the single, shared instance of the NSApplication class, which manages an application's main event loop and resources. It provides a convenient way for any part of an application to access the central application object and its functionalities, such as handling user events, managing windows, and interacting with the operating system.

Key Aspects of NSApp:

Global Access:

NSApp acts as a convenient handle to the application's main object, allowing easy access from anywhere within the application's code.

NSApplication Instance:
It always points to an instance of NSApplication, which is the core object for controlling the application's lifecycle and behavior.

Main Event Loop:

NSApp is involved in running the application's main event loop, which handles events like user input, window updates, and other system messages.

Central Management:

It serves as the manager for all application-level resources and provides the interface for interacting with the operating system.

Accessibility:

Developers use NSApp to perform operations such as getting or setting the key window, creating and configuring menus, and controlling the application's overall execution flow

---

#### mac cocoa how does the NSWindow get tied to the NSApp

In macOS Cocoa applications, the NSWindow objects are managed and coordinated by the shared NSApplication instance. This relationship is not a direct "ownership" in the traditional sense, but rather a central management role for NSApp.

Here's how NSWindow objects are tied to NSApp:

Event Handling and Distribution:

NSApplication is the central hub for receiving events from the window server. It translates these raw events into NSEvent objects and then dispatches them to the appropriate NSWindow object. For example, mouse and keyboard events are routed to the NSWindow that is currently the target of those actions.

Window Management:

NSApplication maintains a list of open windows, and as of macOS 10.13 and later, it strongly references these windows by default. This ensures that windows remain in memory as long as they are open. Earlier versions of macOS required developers to manage window memory more explicitly, often through NSWindowController instances.

Key and Main Window Tracking:

NSApplication keeps track of the "key window" (the window that receives keyboard input) and the "main window" (the primary window of the application). It provides methods like keyWindow and mainWindow to access these specific NSWindow instances.

Application Delegate Interaction:

The NSApplicationDelegate protocol, implemented by your application's delegate class, provides methods that allow you to respond to application-level events, including those related to window management, such as applicationDidFinishLaunching:, applicationWillTerminate:, and applicationShouldTerminateAfterLastWindowClosed:. These delegate methods often involve interacting with NSWindow objects.

Nib/Storyboard Loading:

When an application launches, NSApplication is responsible for loading the main nib file (or storyboard). This process instantiates NSWindow objects (and their associated views) defined within the nib/storyboard and establishes the connections between them and other objects, including potential NSWindowController instances.

In essence, NSApp acts as the central coordinator and dispatcher for all NSWindow instances within a Cocoa application, facilitating their interaction with the user, the operating system, and other application components.

---

### Filenames ending in WGSL

WGSL File Meaning

A WGSL file on Blade refers to a file containing code written in the WebGPU Shading Language (WGSL), which is the primary and first-class shader language used by the Blade graphics library.

 Blade is designed to be cross-platform and supports Vulkan, Metal, and OpenGL ES, with WGSL serving as the single source of truth for shaders.

 This approach allows for a consistent and portable way to write shaders that can be compiled into the appropriate backend language (like SPIR-V for Vulkan or MSL for Metal) using the Naga library.

In the context of Blade, WGSL files are used to define the logic for vertex and fragment shaders, which are essential components of the rendering pipeline. For example, a WGSL file might contain a vertex shader function (vs_main) that transforms 3D vertices into screen coordinates and a fragment shader function (fs_main) that determines the color of each pixel.

 The use of WGSL in Blade enables advanced features like ray tracing, where shader code is written directly in WGSL, ensuring compatibility and performance across different platforms.

The .wgsl file extension is standardized by IANA for text-based WGSL content, and these files are typically imported and compiled into shader modules within the application code.

 While Blade supports WGSL as its primary language, it also allows for the use of other formats like GLSL or SPIR-V during the transition period, though WGSL is the recommended and future-focused approach.

---

### Filename shaders.metal

The filename shaders.metal is used for a Metal Shading Language (MSL) source code file, which is the standard format for writing shaders in Apple's Metal framework.

 The .metal file extension is required for Xcode and the GPU frame debugger to recognize the source files during development, debugging, and profiling.

 This file typically contains shader functions written in MSL, such as vertex and fragment functions, which are essential for rendering graphics.

 For instance, a shaders.metal file might include a vertex function to transform geometry and a fragment function to determine pixel color.

 The file can be compiled into an intermediate representation (.ir) using the xcrun -sdk macosx metal -c shaders.metal -o shaders.ir command, which can then be disassembled into a human-readable LLVM assembly format using llvm-dis.

 This compiled code is later packaged into a .metallib file, which is included in the application bundle and contains the compiled shader code and metadata.

---

### References

- https://stackoverflow.com/questions/36110247/format-of-metal-compiled-metallib-shader-file
- https://www.reddit.com/r/rust_gamedev/comments/u9vjc2/any_guidesdocumentation_on_the_wgsl_shading/
- https://www.w3.org/TR/WGSL/
