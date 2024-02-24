# Match

Match expressions are similar to if else if

It matches only on same type and accounts every possibility.
Making code more robust

It works on expressions instead of statements. Therefore, at the end of statement instead of `;` we will use `,`.

```rust
fn main() {
    let some_int = 3;
    match some_int {
        1 => println!("its 1"),
        2 => println!("its 2"),
        3 => println!("its 3"),
        _ => println!("its something else")
    }
}
```

Match will be checked by the compiler, so if a new possibility is added, you will be notified when this occurs

In contrast, else..if is not checked by the compiler. If a new possibility is added, your code may contain a bug

Prefer using match over else..if when working with a single variable
