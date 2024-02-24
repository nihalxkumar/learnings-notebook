# Operators

Operators are symbols used to manipulate data.

In the expression `z = x + y`, `z`, `x`, and `y` are operands, while `=` and `+` are operators.

## Operators Based on the Number of Operands

1. **Unary**
   - 1 operand
   - Examples: `x++`, `++x`, `+x`, `-x`

2. **Binary**
   - 2 operands
   - Examples: `x + y`, `x - y`, `x! = y`, `x==y`

3. **Ternary**
   - 3 operands
   - Only one operator: `?:`

## Operators on basis of functions

1. Arithmetic

   `+`, `-`, `*`, `/` (quotient operator), `%` (remainder operator or modulus)

   > in $n/d$ if $n< d$ then output is $0$
   > 
   > in $n \% d$ if $n<d$ then output is $n$

   Rules for arithmetic operators:-
    - int/int is always int
    - Modulus operator cannot be used with floating point numbers as by default every float is treated as double. C is an expanding language.  `5.2%2` => Error

   If more than 1 operator is present in an expression then precedence rule will be applied. 

   PEMDAS stands for Parentheses, Exponents, Multiplication and Division (left to right), and Addition and Subtraction (left to right
   
   - Operations inside parentheses are performed first.
   
   - Multiplication and division have higher precedence than addition and subtraction.

   - If multiple operations with the same precedence appear, they are typically performed from left to right.

2. Assignment
    - `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `<<=`, `>>=`, `&=`, `^=`, `|=`
    - 2 types of assignment
        - Simple
        - Compound
   
   Rules for assignment operators
     1. Single variable is allowed in LHS of assignment operator
     2. Cascading of assignment operator
         - `int x=y=z=2;`
             - Associativity of assignment operator is from Right to Left
         - `x = 5` `y = 2` Swap values without introducing a third variable
        ```C
          x = x + y; // x = 5 + 2 => 7
          y = x - y; // y = 7 - 2 => 5
          x = x - y; // x = 7 - 5 => 2
        ```
        There are many ways
        ```C
        x = x * y; // x = 10
        y = x / y; // y = 10/2 => 5
        x = x / y; // x = 10/5 => 2
        ```

3. Relational

- `>`, `<`, `>=`, `<=`, `==`, `!=`
- for True comparisons the output will be 1.
- associativity of relation is Left to Right
- Precedence of arithmetic is more than of Relational
```C
int a = 5, b = 2, c = 1, d;
d = c + a > b;
// (c + a) > b
// (1 + 5) > b
// 6 > 2
// True hence 1
```

 > here is the general order from high to low:

    1. Postfix operators (all have the same precedence, so sequences of operators will be evaluated left-to-right)
            - array subscript operator `[]`
            - function call operator `()`
            - component selection operators `.` and `->`
            - postfix `++` and `--`
    2. Unary operators (all have the same precedence, so sequences of operators will be evaluated left-to-right)
      - prefix `++` and `--`
      - `sizeof`
      - bitwise negation operator `~`
      - logical negation operator `!`
      - unary sign operators `-` and `+`
      - address-of operator `&`
      - dereference operator `*`
    3. Cast expressions `(` _type name_ `)`
    4. Multiplicative operators `*`, `/`, `%`
    5. Additive operators `+` and `-`
    6. Shift operators `<<` and `>>`
    7. Relational operators `<`, `>`, `<=`, `>=`
    8. Equality operators `==` and `!=`
    9. Bitwise AND `&`
    10. Bitwise XOR `^`
    11. Bitwise OR `|`
    12. Logical AND `&&`
    13. Logical OR `||`
    14. Conditional operator `?:`
    15. Assignment operators `=`, `+=`. `-=`, `*=`, `/=`, `%=`, `<<=`, `>>=`, `&=`, `^=`, `|=`
    16. Sequential (comma) operator `,`
      
    So, expressions like `*x++` are parsed as `*(x++)`, since the postfix `++` has higher precedence than the unary `*`. 
    Similarly, `sizeof x + 1` is parsed as `(sizeof x) + 1`, since `sizeof` has higher precedence than addition.
    An expression like `p++->x` is parsed as `(p++)->x`; both postfix `++` and `->` operators have the same precedence, so they're parsed from left to right.
     
    This is about as short as shortcuts get; when in doubt, use parentheses.

4. Logical
 - Not
     - exclamation !
 - AND
     - Double ampersand &&
 - OR
   - Double piped ||
   - Short-circuiting
   > Short-circuiting refers to a feature of logical operators in programming languages that prevents unnecessary computation when the result of an expression becomes determinable based on earlier parts of the expression. Specifically, for the `OR` operator (`||`), short-circuiting means that once a true value is found among the operands, the entire expression returns true without evaluating subsequent operands. Conversely, for the `AND` operator (`&&`), short-circuiting means that once a false value is found among the operands, the entire expression returns false without evaluating subsequent operands
 - Any non-zero value in case of C is considered as True
 - Order of precedence NOT -> AND -> OR
5. Increment
   * Pre `++x` first increment then assign. 
   * Post `x++` first assign then increment. 
       
   Pre and post work same if you are using it as a single statement. But if you are using it as a part of a bigger expression then it will make a difference.
   
   Example 1:
   
      ```C
          int a = 5, b;
          b = a++ + a++;
          printf("%d %d", a, b);
          // 7 10
    ```
   
   
   Example 2:
   
   ```C
      int a = 5, b;
       b = ++a + ++a;
       printf("%d %d", a, b);
       // 7 13
 ```
      
   
#### Explanation
   
   1. We declare two integer variables a and b. Initially, a is assigned the value of 5, while we haven't yet set any initial value for b.
   
   2. The line b = a++ + a++; performs several operations at once. Firstly, it adds the current values of a (which is still 5) with itself (again, currently 5). This results in 10. Secondly, after adding these values together, it increments a twice – first from its original value of 5 to 6, then again to 7.
   
   3. Note that ++ before a variable means incrementing it by one immediately after the operation. So when used within an expression like here, it will be applied only once, not twice as you might expect based on the order of appearance.
   
   Use pen and paper. make a table of values of a and b at each step.
   
   | x     | y  |
   |-------|----|
   | ~~5~~ | 10 |
   | ~~6~~ |    |
   | 7     |    |
   

Example 3:

   ```C
    x = 1;
    y = x++ * ++x * x++ * ++x * x++ * x++;
   ```
| x     |
|-------|
| ~~1~~ |
| ~~2~~ |
| 3     |

y = $3^6$ (6 times we are mulitplying 3 with itself)
x = 7 (x = 1 and there are 6 elemts [ 6 increments] )

6. Decrement
7. Shortcut
8. Ternary
9. Type Casting
10. Size of operator
