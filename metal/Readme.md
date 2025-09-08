
### Filenames ending in WGSL

WGSL File Meaning

A WGSL file on Blade refers to a file containing code written in the WebGPU Shading Language (WGSL), which is the primary and first-class shader language used by the Blade graphics library.

 Blade is designed to be cross-platform and supports Vulkan, Metal, and OpenGL ES, with WGSL serving as the single source of truth for shaders.

 This approach allows for a consistent and portable way to write shaders that can be compiled into the appropriate backend language (like SPIR-V for Vulkan or MSL for Metal) using the Naga library.

In the context of Blade, WGSL files are used to define the logic for vertex and fragment shaders, which are essential components of the rendering pipeline. For example, a WGSL file might contain a vertex shader function (vs_main) that transforms 3D vertices into screen coordinates and a fragment shader function (fs_main) that determines the color of each pixel.

 The use of WGSL in Blade enables advanced features like ray tracing, where shader code is written directly in WGSL, ensuring compatibility and performance across different platforms.

The .wgsl file extension is standardized by IANA for text-based WGSL content, and these files are typically imported and compiled into shader modules within the application code.

 While Blade supports WGSL as its primary language, it also allows for the use of other formats like GLSL or SPIR-V during the transition period, though WGSL is the recommended and future-focused approach.



### Filename shaders.metal

The filename shaders.metal is used for a Metal Shading Language (MSL) source code file, which is the standard format for writing shaders in Apple's Metal framework.

 The .metal file extension is required for Xcode and the GPU frame debugger to recognize the source files during development, debugging, and profiling.

 This file typically contains shader functions written in MSL, such as vertex and fragment functions, which are essential for rendering graphics.

 For instance, a shaders.metal file might include a vertex function to transform geometry and a fragment function to determine pixel color.

 The file can be compiled into an intermediate representation (.ir) using the xcrun -sdk macosx metal -c shaders.metal -o shaders.ir command, which can then be disassembled into a human-readable LLVM assembly format using llvm-dis.

 This compiled code is later packaged into a .metallib file, which is included in the application bundle and contains the compiled shader code and metadata.

### References

- https://stackoverflow.com/questions/36110247/format-of-metal-compiled-metallib-shader-file
- https://www.reddit.com/r/rust_gamedev/comments/u9vjc2/any_guidesdocumentation_on_the_wgsl_shading/
- https://www.w3.org/TR/WGSL/
