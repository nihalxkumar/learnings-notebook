# Relational

Relational operators are fundamental for comparing two values. These operators evaluate the relationship between operands and return a Boolean value (1 for true or 0 for false).

- `>` Greater Than
- `<` Less Than
- `>=` Greater Than or Equal To
- `<=` Less Than or Equal To
- `==` Equal To
- `!=` Not Equal To

## Key Points

- Associativity of relational operators is Left to Right

- Precedence of Arithmetic Operators is more than of Relational Operators

```C
int a = 5, b = 2, c = 1, d;
d = c + a > b;
// (c + a) > b
// (1 + 5) > b
// 6 > 2
// Since the comparison is true, the output will be 1.
```

## Additional Point

- Character Comparison:
  - Relational operators can also be used to compare characters in C. Characters are compared based on their ASCII values. For example, `'a' < 'b'` would evaluate to true because the ASCII value of `'a'` (97) is less than that of `'b'` (98).

