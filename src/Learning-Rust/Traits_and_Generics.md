# Traits

Traits define similar functionality for different types

It can be used to standardize functionality across multiple different types.

Standardization permits functions to operate on multiple different types. [ Code deduplication ]

## Generic Functions

Generic functions are functions that can operate on multiple different types.

A function that can have a single parameter to operate on multiple different types.

Trait is used as function parameter instead of data type. Function depends on existence of functions declared by trait.

Efficient code. Automatically deduces the type of the parameter when new data type is used.

3 types of Generic Syntaxes

1. Using impl Trait. 
   * Any type that implements a trait. Go with this when you have small number of traits and small number of parameters.
    ```rust, ignore
    fn function(param1: impl Trait1, param2: impl Trait2) {
    // code
    }
    ```

2. Usual
   * A generic type `T` is constrained to implement a specific Trait `Trait1` and `U` is contrained to implement `Trait2`.
   The function parameter must be of Type `T` and `U` and the function will only work if the parameters implement the traits.
    
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

3. Usual using Where keyword [most preferred]
   * A generic type `T` and `U` are used as parameters and then we use the `where` keyword to specify the constraints.
       
   ```rust, ignore
   fn function<T, U>(param1: T, param2: U)
       where
           T: Trait1 + Trait2,
           U: Trait3 + Trait4
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
