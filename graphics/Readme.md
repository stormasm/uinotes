
---

### winit uses the raw window handle crate

- [raw window handle](https://github.com/rust-windowing/raw-window-handle)
- [raw window handle api](https://docs.rs/raw-window-handle)
- [zed discord gpui](https://discord.com/channels/869392257814519848/1199799855007158352/1399510465507360819)

---

- [Video 0 Start of the Series](https://www.youtube.com/watch?v=zizinGhwrPM)
- [Event Loop](https://www.youtube.com/watch?v=P0VcE9D-3Ow)
- [Great explanation of the comparison of immediate mode vs retained mode graphics](https://www.youtube.com/watch?v=9h6OJvKUV7c)
- [Events](https://www.youtube.com/watch?v=Kno65SRBSVE)
- [Display Pipeline](https://www.youtube.com/watch?v=8nMelCJzXm4)

---

- [How Real Time Computer Graphics and Rasterization work](https://www.youtube.com/watch?v=brDJVEPOeY8)
- [Episode 4 Theory The Programmable Graphics Pipeline](https://www.youtube.com/watch?v=kpA5X6eI6fM)
- [How Rendering Graphics Works in Games](https://www.youtube.com/watch?v=cvcAjgMUPUA)
- [Why video games are made of tiny triangles](https://www.youtube.com/watch?v=U93RImC-by4)

---

### in computer windows what is a render surface

In computer graphics on Windows, a render surface is essentially a memory buffer that the system (or a program) can draw or "render" graphics onto.

Here's a breakdown:

Location for Drawing: It's the designated area where all the pixels and graphical information will be placed during the rendering process.

Memory Buffer: Think of it as a specialized area in memory (often on the graphics card or GPU) that stores the image data, like colors and depths of pixels.

Target for Rendering Operations: When you instruct the graphics card to draw a shape, apply a texture, or generate a shadow, the results of those operations are directed to the render surface.

Types and uses

Window Surface: One common type is the surface associated with a visible window on your screen. The graphics rendered to this surface are then displayed in that window.

Offscreen Surface (or Render Target): Graphics can also be rendered to a surface that isn't directly visible on the screen. This is called offscreen rendering or rendering to a texture/bitmap. This is useful for various purposes like:

- Post-processing effects: Applying blurs, color correction, or other visual effects after the initial scene has been rendered.
- Saving to a file: Creating an image that can be saved as a file, according to Microsoft Learn.
- Using as a texture: Generating an image to be used as a texture on another object in the scene.

DirectX and OpenGL: In graphics APIs like DirectX, these surfaces are managed through specific interfaces like IDirect3DSurface9 or ID2D1RenderTarget.

In simpler terms, a render surface is the digital canvas onto which your computer paints the images and animations you see on your screen.
