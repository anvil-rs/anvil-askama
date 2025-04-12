# anvil-askama

An [Anvil](https://github.com/anvil-rs/anvil) integration for [Askama](https://github.com/askama-rs/askama) templates.

## Installation

```toml
[dependencies]
anvil-askama = "0.2.1"
anvil = "0.3.0"
askama = "0.13.0"
```

## Usage

```rust
use anvil::Forge;
use anvil_askama::prelude::*;  // Import extension traits and functions
use askama::Template;

// Define an Askama template
#[derive(Template)]
#[template(source = "Hello, {{ name }}!", ext = "txt")]
struct MyTemplate {
    name: String,
}

fn main() -> Result<(), Box<dyn std::error::Error>> {
    let template = MyTemplate { name: "World".to_string() };
    
    // Generate a new file
    generate(&template).forge("hello.txt")?;
    
    // Append to an existing file
    append(&template).forge("log.txt")?;
    
    Ok(())
}
```
