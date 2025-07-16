

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
