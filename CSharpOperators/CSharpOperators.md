
# C# Operators

In this chapter, You will learn about the below C# Operators: 

- [C# Operators](#c-operators)
  - [Operators](#operators)
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

## Operators

* Arithmetic Operators 
* Comparison Operators
* Boolean Logical Operators
* Bitwise and Shift Operators
* Equality Operators

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