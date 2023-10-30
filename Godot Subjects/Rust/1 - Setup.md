[YouTube - Setting Up Rust in Godot 4.1! Advanced Godot 4!](https://www.youtube.com/watch?v=z14cfTc40uQ&ab_channel=FinePointCGI)


1. Create a new crate library
```bash
cargo new [CRATE_NAME] --lib
```

2. `Cargo.toml` godot dependency
```toml
[dependencies]
godot = { git = "https://github.com/godot-rust/gdext", branch = "master"}

[lib]
crate-type = ["cdylib"]
```

3. `lib.rs` is the library


