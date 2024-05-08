# Lifetimes

```admonish summary title = "Ownership Review"
- All data in Rust is owned by an owner. 
- The owner is responsible for cleaning up data.
  - Functions, closures, structs, enums, and scopes
- Ownership can be transferred and borrowed
  - Function calls, variable reassignment and closures
```

Lifetimes are a way to inform the compiler that the borrowed data will be valid at a specific point in time. This is important because the compiler needs to know when the borrowed data will be valid and when it will be invalid.

It is needed for storing references in structs, enums & function signatures and returning borrowed data from functions.

All data has a lifetime, most of the time it is implicit and inferred by the compiler.
 
```rust, ignore
struct Person<'a> {
    name: &'a str,
}
```

In the above example, the lifetime of the reference is `'a`. The lifetime of the reference is the same as the lifetime of the struct.

`'a`, `'b`, `'c` are lifetime parameters. They are used to specify the lifetime of the reference.

`'static` is a resever keyword. static lifetimes lasts for the entire duration of the program. It is used for string literals.




