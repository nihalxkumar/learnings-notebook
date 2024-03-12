# Logical
Logical operators are used to combine two or more conditions to determine the logic between values

- Not
    - exclamation !
- AND
    - Double ampersand &&
- OR
    - Double piped ||
    - Short-circuiting
  > Short-circuiting refers to a feature of logical operators in programming languages that prevents unnecessary computation when the result of an expression becomes determinable based on earlier parts of the expression. Specifically, for the `OR` operator (`||`), short-circuiting means that once a true value is found among the operands, the entire expression returns true without evaluating subsequent operands. Conversely, for the `AND` operator (`&&`), short-circuiting means that once a false value is found among the operands, the entire expression returns false without evaluating subsequent operands

Any non-zero value in case of C is considered as True

Order of precedence NOT -> AND -> OR