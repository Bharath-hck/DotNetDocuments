
# C# Operators

In this chapter, You will learn about the below C# Operators: 

- [C# Operators](#c-operators)
    - [Arithmetic Operators](#arithmetic-operators)
      - [Increment Operator](#increment-operator)
        - [Postfix Increment Operator](#postfix-increment-operator)
        - [Prefix Increment Operator](#prefix-increment-operator)
      - [Decrement Operator](#decrement-operator)
        - [Postfix Decrement Operator](#postfix-decrement-operator)
        - [Prefix Decrement Operator](#prefix-decrement-operator)
      - [Unary Plus and Minus Operators](#unary-plus-and-minus-operators)
      - [Multiplication Operator](#multiplication-operator)
      - [Division Operator](#division-operator)
      - [Remainder operator](#remainder-operator)
      - [Addition Operator](#addition-operator)
      - [Subtraction Operator](#subtraction-operator)
    - [Comparison operators](#comparison-operators)
      - [Less than operator](#less-than-operator)
      - [Greater than operator](#greater-than-operator)
      - [Less than or equal operator](#less-than-or-equal-operator)
      - [Greater than or equal operator](#greater-than-or-equal-operator)
    - [Boolean Logical Operators](#boolean-logical-operators)
      - [Logical Negation Operator](#logical-negation-operator)
      - [Logical AND Operator](#logical-and-operator)
      - [Logical OR Operator](#logical-or-operator)
      - [Logical Exclusive OR Operator](#logical-exclusive-or-operator)
      - [Conditional Logical AND Operator](#conditional-logical-and-operator)
      - [Conditional Logical OR Operator](#conditional-logical-or-operator)

### Arithmetic Operators 

Operators that perform arithmetic operations with numeric operands

* Unary:
	* `++` increment
	* `--` decrement
	* `+` plus)
	* `-` minus)

* Binary:
	*  `*` multiplication
	*  `/` division
	*  `%` remainder
	*  `+` addition
	*  `-` subtraction

#### Increment Operator

* The unary increment operator `++` increments its operand by `1`. 
* The operand must be a variable, a property access, or an indexer access.
* The increment operator is supported in two forms: 
    * the postfix increment operator, `x++` 
    * the prefix increment operator, `++x`


##### Postfix Increment Operator

The result of `x++` is the value of `x` before the operation, as the following example shows:

```cs
int i = 3;
Console.WriteLine(i);   // output: 3
Console.WriteLine(i++); // output: 3
Console.WriteLine(i);   // output: 4
```

##### Prefix Increment Operator

The result of `++x` is the value of `x` after the operation, as the following example shows:

```cs
int i = 3;
Console.WriteLine(i);   // output: 3
Console.WriteLine(++i); // output: 4
Console.WriteLine(i);   // output: 4
```

#### Decrement Operator

* The unary decrement operator `--` decrements its operand by `1`. 
* The operand must be a variable, a property access, or an indexer access.
* The decrement operator is supported in two forms: 
    * the postfix decrement operator, `x--`
    * the prefix decrement operator, `--x`

##### Postfix Decrement Operator

The result of `x--` is the value of `x` before the operation, as the following example shows:

```cs
int i = 3;
Console.WriteLine(i);   // output: 3
Console.WriteLine(i--); // output: 3
Console.WriteLine(i);   // output: 2
```
##### Prefix Decrement Operator

The result of `--x` is the value of `x` after the operation, as the following example shows:

```cs
int i = 3;
Console.WriteLine(i);   // output: 3
Console.WriteLine(--i); // output: 2
Console.WriteLine(i);   // output: 2

```
#### Unary Plus and Minus Operators

* The unary `+` operator returns the value of its operand. 
* The unary `-` operator computes the numeric negation of its operand.

```cs
Console.WriteLine(+4);     // output: 4
Console.WriteLine(-4);     // output: -4
Console.WriteLine(-(-4));  // output: 4
```

#### Multiplication Operator

The multiplication operator `*` computes the product of its operands:

```cs
Console.WriteLine(5 * 2);         // output: 10
Console.WriteLine(0.5 * 2.5);     // output: 1.25
Console.WriteLine(0.1m * 23.4m);  // output: 2.34
```
#### Division Operator

The division operator `/` divides its left-hand operand by its right-hand operand.

```cs
Console.WriteLine(13 / 5);          // output: 2

// To obtain the quotient of the two operands as a floating - point number
// use the float, double, or decimal type:
Console.WriteLine((double) 13 / 5); // output: 2.6

Console.WriteLine(16.8f / 4.1f);   // output: 4.097561
Console.WriteLine(16.8d / 4.1d);   // output: 4.09756097560976
Console.WriteLine(16.8m / 4.1m);   // output: 4.0975609756097560975609756098
```

#### Remainder operator

The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.

```cs
Console.WriteLine(5 % 4);        // output: 1
Console.WriteLine(-5.2f % 2.0f); // output: -1.2
Console.WriteLine(5.9m % 3.1m);  // output: 2.8
```

#### Addition Operator

The addition operator `+` computes the sum of its operands:

``` cs
Console.WriteLine(5 + 4);       // output: 9
Console.WriteLine(5 + 4.3);     // output: 9.3
Console.WriteLine(5.1m + 4.2m); // output: 9.3
```

#### Subtraction Operator

The subtraction operator - subtracts its right-hand operand from its left-hand operand:

```cs
Console.WriteLine(47 - 3);      // output: 44
Console.WriteLine(5 - 4.3);     // output: 0.7
Console.WriteLine(7.5m - 2.3m); // output: 5.2
```

### Comparison operators

Comparison operators are also called as relational operators. Below are the comparison operators.

* `<` less than
* `>` greater than
* `<=` less than or equal
* `>=` greater than or equal

#### Less than operator

The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:

```cs
Console.WriteLine(7.0 < 5.1);   // output: False
Console.WriteLine(5.1 < 5.1);   // output: False
Console.WriteLine(0.0 < 5.1);   // output: True
```
#### Greater than operator

The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:

```cs
Console.WriteLine(7.0 > 5.1);   // output: True
Console.WriteLine(5.1 > 5.1);   // output: False
Console.WriteLine(0.0 > 5.1);   // output: False
```
#### Less than or equal operator

The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:

```cs
Console.WriteLine(7.0 <= 5.1);   // output: False
Console.WriteLine(5.1 <= 5.1);   // output: True
Console.WriteLine(0.0 <= 5.1);   // output: True
```

#### Greater than or equal operator

The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:

```cs
Console.WriteLine(7.0 >= 5.1);   // output: True
Console.WriteLine(5.1 >= 5.1);   // output: True
Console.WriteLine(0.0 >= 5.1);   // output: False
```
### Boolean Logical Operators

The logical Boolean operators perform logical operations with bool operands. Below are the boolean logical operators:

* Unary
  * `!` Logical Negation Operator
* Binary
  * `&` Logical AND, `|` Logical OR, `^` Logical exclusive OR
  * `&&` Conditional Logical AND, `||` Conditional Logical OR 

#### Logical Negation Operator

The unary prefix `!` operator computes logical negation of its operand. That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:

```cs
bool passed = false;
Console.WriteLine(!passed);  // output: True
Console.WriteLine(!true);    // output: False
```
#### Logical AND Operator

The `&`operator computes the logical AND of its operands. The result of `x & y` is `true` if both `x` and `y` evaluate to `true`. Otherwise, the result is `false`.

The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.

In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:

```cs
bool SecondOperand()
{
    Console.WriteLine("Second operand is evaluated.");
    return true;
}

bool a = false & SecondOperand();
Console.WriteLine(a);
// Output:
// Second operand is evaluated.
// False

bool b = true & SecondOperand();
Console.WriteLine(b);
// Output:
// Second operand is evaluated.
// True
```

#### Logical OR Operator

The `|` operator computes the logical OR of its operands. The result of `x | y` is true if either `x` or `y` evaluates to `true`. Otherwise, the result is `false`.

The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.

In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:

```cs
bool SecondOperand()
{
    Console.WriteLine("Second operand is evaluated.");
    return true;
}

bool a = true | SecondOperand();
Console.WriteLine(a);
// Output:
// Second operand is evaluated.
// True

bool b = false | SecondOperand();
Console.WriteLine(b);
// Output:
// Second operand is evaluated.
// True
```

#### Logical Exclusive OR Operator

The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands. The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`. Otherwise, the result is `false`. That is, for the bool operands, the `^` operator computes the same result as the inequality operator `!=`

```cs
Console.WriteLine(true ^ true);    // output: False
Console.WriteLine(true ^ false);   // output: True
Console.WriteLine(false ^ true);   // output: True
Console.WriteLine(false ^ false);  // output: False
```

#### Conditional Logical AND Operator

The conditional logical AND operator `&&`, also known as the **short-circuiting** logical AND operator, computes the logical AND of its operands. The result of `x && y` is `true` if both `x` and `y` evaluate to `true`. Otherwise, the result is `false`. If x evaluates to `false`, `y` isn't evaluated.

In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:

```cs
bool SecondOperand()
{
    Console.WriteLine("Second operand is evaluated.");
    return true;
}

bool a = false && SecondOperand();
Console.WriteLine(a);
// Output:
// False

bool b = true && SecondOperand();
Console.WriteLine(b);
// Output:
// Second operand is evaluated.
// True
```

The logical AND operator `&` also computes the logical AND of its operands, but *always evaluates both operands*.

#### Conditional Logical OR Operator 

The conditional logical OR operator `||`, also known as the **short-circuiting** logical OR operator, computes the logical OR of its operands. The result of `x || y` is `true` if either `x` or `y` evaluates to `true`. Otherwise, the result is `false`. If `x` evaluates to `true`, `y` isn't evaluated.

In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:

```cs
bool SecondOperand()
{
    Console.WriteLine("Second operand is evaluated.");
    return true;
}

bool a = true || SecondOperand();
Console.WriteLine(a);
// Output:
// True

bool b = false || SecondOperand();
Console.WriteLine(b);
// Output:
// Second operand is evaluated.
// True
```

