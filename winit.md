
- elwt stands for event loop window target
- Rename EventLoopWindowTarget to ActiveEventLoop.
- [see details here](https://rust-windowing.github.io/winit/winit/changelog/v0_30/index.html)

---

- https://medium.com/@aleksej.gudkov/rust-winit-example-creating-a-windowed-application-0eaaf395d776

### What is winit

Winit is a popular Rust library for handling window creation and input events. It serves as the foundation for many graphics and game development frameworks, making it an essential tool for creating cross-platform applications. In this article, we’ll explore how to use Winit to create a basic window and handle events like user input.

- Winit is a cross-platform Rust library designed for:
- Window Creation: Create native application windows on desktop and mobile platforms.
- Input Handling: Capture keyboard, mouse, and other input events.
- Event Management: Manage and respond to application lifecycle events.

---

So blitz, floem, and viewskater all get kicked off by

```rust
event_loop.run_app
```

which takes as a paramter an

```rust
ApplicationHandler
```

This is what gets passed to

https://docs.rs/winit/latest/winit/event_loop/struct.EventLoop.html#method.run_app

Each one of the above repos implements this trait.

https://docs.rs/winit/latest/winit/application/trait.ApplicationHandler.html
