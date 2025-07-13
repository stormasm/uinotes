
- [discord: start of Floem 2/3/2023](https://discord.com/channels/946858761413328946/1071098441289179267/1071099167058956399)

---

*context.rs is mission critical to the floem story*

```rust
rg context::
```
---

#### Interface to Winit

```rust
rg run_app
```

##### src/app.rs

```rust
pub fn run(mut self) {
    let event_loop = self.event_loop.take().unwrap();
    let _ = event_loop.run_app(self);
}
```
