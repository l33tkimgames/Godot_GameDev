

### Custom Type
+ [Discord Link](https://discord.com/channels/723850269347283004/940237853999386654/1153736697352306749)
```rust
#[derive(Debug)]
struct SomeNewtype(i64);

impl GodotCompatible for SomeNewtype {
    type Via = i64;
}

impl ToGodot for SomeNewtype {
    fn to_godot(&self) -> Self::Via {
        self.0
    }
}

impl FromGodot for SomeNewtype {
    fn try_from_godot(via: Self::Via) -> Option<Self> {
        Some(Self(via))
    }
}

#[derive(GodotClass)]
#[class(init, base = Node)]
pub struct Foo {}

#[godot_api]
impl Foo {
    #[func]
    fn foo(&self, my_new_type: SomeNewtype) {
        godot_print!("i got {my_new_type:?}");
    }
}
```