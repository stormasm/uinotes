
- [iced book fork](https://github.com/stormrust/book)

```rust
use magic::{display, interact};

// Initialize the state
let mut counter = Counter::default();

// Be interactive. All the time!
loop {
    // Run our view logic to obtain our interface
    let interface = counter.view();

    // Display the interface to the user
    display(&interface);

    // Process the user interactions and obtain our messages
    let messages = interact(&interface);

    // Update our state by processing each message
    for message in messages {
        counter.update(message);
    }
}
```

- [Looping Around](https://book.iced.rs/the-runtime.html#looping-around)
