
```rust
rg "impl Widget"
```

- button
- label
- slider
- picture_widget
- help_screen

---

- So there are five widgets in total in the emulsion app.
- button, label, and slider are part of gelatin
- picture_widget and help_screen are part of emulsion

---

Each one of the widgets has these characteristics

```rust
struct ButtonData {}

impl WidgetData for ButtonData {}

pub struct Button {}

impl Button {}

impl Default for Button {}

impl Widget for Button {}
```
