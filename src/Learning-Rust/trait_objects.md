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

### Using trait objects with functions

#### Borrow

```rust, ignore
fn borrow_clicky(obj : &dyn Clicky){
    obj.click();
}

let kb = Keyboard;
borrow_clicky(&kb);
```

#### To move trait objects we use Box

```rust, ignore
fn move_clicky(obj : Box<dyn Clicky>){
    obj.click();
}

let kb = Box::new(Keyboard);
move_clicky(kb);
```

### Heterogenous Vector

```rust, ignore
struct Mouse;
impl Clicky for Mouse {
  fn click(&self) {
    println!("Mouse Clicked");
  }
}


fn make_clicks(clickeys: Vec<Box<dyn Clicky>>){
    for clicker in clickeys{
        clicker.click();
    }
}

// one way to create a vector of trait objects
// let kb = Box<dyn Clicky> = Box::new(Keyboard);
// let mouse = Box<dyn Clicky> = Box::new(Mouse);
// let clickers = vec![kb, mouse];

let kb = Box::new(Keyboard);
let mouse = Box::new(Mouse);
let clickers: Vec<Box<dyn Clicky>> = vec![kb, mouse];

make_clicks(clickers);
```