# Traits

Traits define similar functionality for different types.

It can be used to standardize functionality across multiple different types.

Standardization permits functions to operate on multiple different types. [ Code deduplication ]

```rust, ignore
trait Move {
    fn move_to(&self, x: i32, y: i32);
}

struct Snake;
impl Move for Snake {
    fn move_to(&self, x: i32, y: i32) {
        println!("slither to ({}, {})", x, y);
    }
}

struct Horse;
impl Move for Horse {
    fn move_to(&self, x: i32, y: i32) {
        println!("gallop to ({}, {})", x, y);
    }
}
```

# Generics

## Generic Functions

Generic functions are functions that can operate on multiple different types.

A function that can have a single parameter to operate on multiple different types.

Trait is used as function parameter instead of data type. Function depends on existence of functions declared by trait.

Efficient code. Automatically deduces the type of the parameter when new data type is used.

### 3 types of Generic Syntaxes

1. First Way

   * Any type that implements a trait. 
   
   * Go with this when you have small number of traits and small number of parameters.
    
    ```rust, ignore
    fn function(param1: impl Trait1, param2: impl Trait2) {
    // code
    }
    ```
        
    ```rust, ignore
    fn make_move(thing: impl Move, x: i32, y: i32)
    {
        thing.move_to(x, y);
    }
    ```

2. Second Way

   * A generic type `T` is constrained to implement a specific Trait `Trait1` and `U` is contrained to implement `Trait2`.
   The function parameter must be of Type `T` and `U` and the function will only work if the parameters implement the traits.

   * Used only with small number of traits and parameters.

   ```rust,ignore
   fn function<T: Trait1, U: Trait2>(param1: T, param2: U){
       // code
   }
   ```
   * Generic type `T` (used to define the type of the parameter) then the trait that the type must implement.
     In the function parameters we set `thing` to be of type `T`
     and then we call the `move_to` method on `thing`.

   ```rust, ignore
    fn make_move<T: Move>(thing: T, x: i32, y: i32) {
    thing.move_to(x, y);
    }
    ```

    ```rust, ignore
    fn make_move<T: Move>(thing: T, x: i32, y: i32)
    {
        thing.move_to(x, y);
    }
    ```

3. Third Way

   * A generic type `T` and `U` are used as parameters and then we use the `where` keyword to specify the constraints.
       
   ```rust, ignore
   fn function<T, U>(param1: T, param2: U)
       where
           T: Trait1 + Trait2,
           U: Trait3 + Trait4
           // type 1 and type 2 must implement Trait1 and Trait2
           // type 3 and type 4 must implement Trait3 and Trait4
   {
   // code
   }
   ```

    ```rust, ignore
    fn make_move<T>(thing: T, x: i32, y: i32)
        where T: Move
    {
        thing.move_to(x, y);
    }
    ```  

## Generic Structures

Store data of any type within the structure
 - may be any type or constrained by traits

Useful when making own data collections

```rust, ignore
struct Name<T: Trait1 + Trait2, U: Trait3 + Trait4> {
    field1: T,
    field2: U
}

struct Name<T, U>
where
    T: Trait1 + Trait2,
    U: Trait3
{
    field1: T,
    field2: U
}
```

#### Example usage with single type

```rust, ignore
trait Seat {
    fn show(&self);
}

struct Ticket<T: Seat> {
    location: T,
}

fn tickect_info(ticket: Ticket<AirlineSeat>) {
    ticket.location.show();
    // regular non generic fn that accepts a ticket structure as a function parameter.
    // we always need to specify the type of the ticket. Here, we are using AirlineSeat.
    // This AirlineSeat is a type that implements the Seat trait.
}

let airline = Ticket {location: AirlineSeat :: FirstClass};
tickect_info(airline);
```

In the above example, `Ticket` struct is <u>generic over any Seat type</u> and the fn `ticket_info` only accepts a `Ticket` struct with a `AirlineSeat` type.

To maximize our usage of this function we can use generics.

```rust, ignore
trait Seat {
    fn show(&self);
}

struct Ticket<T: Seat> {
    location: T,
}

fn tickect_info<T: Seat>(ticket: Ticket<T>) {
    ticket.location.show();
}

let airline = Ticket {location: AirlineSeat :: FirstClass};
let concert = Ticket {location: ConcertSeat :: FrontRow};
tickect_info(airline);
tickect_info(concert);
```

- cannot mix generic structures in a single collection
  - Generic Structures expand to structures of a specific type

### Implementing Traits for Generic Structures

- Generic Implementation
  - Implements functionality for any type that can be used with the structure
    - applies to all types that alo implement in the indicated trait.

- Concretee Implementation
  - Implements functionality for a specific type
    - only apply to the type indicated in the angle braces

```rust, ignore
struct Name<T: Trait1 + Trait2, U: Trait3 + Trait4> {
    field1: T,
    field2: U
}

impl<T: Trait1 + Trait2, U: Trait3 + Trait4> Name <T, U> {
    fn function(&self, arg1: T, arg2: U) {}
}
```

or

```rust, ignore
struct Name<T, U>
where
    T: Trait1 + Trait2,
    U: Trait3
{
    field1: T,
    field2: U
}
impl <T, U> Name <T, U>
where
    T: Trait1 + Trait2,
    U: Trait3
{
    fn function(&self, arg1: T, arg2: U) {}
}
```



