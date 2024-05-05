# Trait Objects

Trait Objects offer a way to dynamically change program behaviour at runtime.

- Dynamically Allocated Objects
  - Can be understood as Runtime Generics.
    - Dynamic Dispatch in contrast to Static Dispatch of Generics.
   - Trait Objects are also more flexible than Generics.
- Allows mixed types in a collection.
  - Can be used to implement Polymorphism.

```rust, ignore
trait Clicky{
    fn click(&self);
}

struct Keyboard;

impl Clicky for Keyboard{
    fn click(&self){
        println!("Keyboard Clicked");
    }
}

let kb = Keyboard;

let kb: &dyn Clicky = &Keyboard; // Reference(&) to Struct implementing Trait object (dyn Clicky) pointing to an instance of a struct (Keyboard) that implements the Clicky trait.

// or

let kb_obj: &dyn Clicky = &kb; // Reference to Trait Object

// or

let kb: Box<dyn Clicky> = Box::new(Keyboard); // Boxed Trait Object
// `Box::new` function is used to allocate memory on the heap for the Keyboard struct and to create the trait object.

```


