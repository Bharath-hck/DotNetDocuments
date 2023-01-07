
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
    - [Bitwise and Shift Operators](#bitwise-and-shift-operators)
      - [Bitwise Complement Operator](#bitwise-complement-operator)
      - [Left-Shit Operator](#left-shit-operator)
      - [Right-Shit Operator](#right-shit-operator)
      - [Unsigned Right-Shift Operator](#unsigned-right-shift-operator)
      - [Logical AND Operator](#logical-and-operator-1)
      - [Logical OR Operator](#logical-or-operator-1)
      - [Logical Exclusive OR Operator](#logical-exclusive-or-operator-1)
    - [Equality Operators](#equality-operators)
      - [Equality Operator](#equality-operator)
        - [Value types equality](#value-types-equality)
        - [Reference types equality](#reference-types-equality)
      - [Inequality Operator](#inequality-operator)

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

### Bitwise and Shift Operators 

Bitwise and shift operators includes the below:

* Unary
  * `~` Bitwise Complement Operator
* Binary
  * `<<` Left Shift, `>>` Right Shift, `>>>` Unsigned Right Shift
  * `&` Logical AND, `|` Logical OR, `^` Logical Exclusive OR

#### Bitwise Complement Operator

Bitwise Complement operator is represented by `~`. It is a unary operator, i.e. operates on only one operand. The `~` operator *inverts* each bits i.e. changes `1` to `0` and `0` to `1`.

```cs
uint a = 0b_0000_1111_0000_1111_0000_1111_0000_1100;
uint b = ~a;
Console.WriteLine(Convert.ToString(b, toBase: 2));
// Output:
// 11110000111100001111000011110011
```
#### Left-Shit Operator

The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand. The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero.

```cs
uint x = 0b_1100_1001_0000_0000_0000_0000_0001_0001;
Console.WriteLine($"Before: {Convert.ToString(x, toBase: 2)}");

uint y = x << 4;
Console.WriteLine($"After:  {Convert.ToString(y, toBase: 2)}");
// Output:
// Before: 11001001000000000000000000010001
// After:  10010000000000000000000100010000
```

#### Right-Shit Operator

The >> operator shifts its left-hand operand right by the number of bits defined by its right-hand operand. The right-shift operation discards the low-order bits.

```cs
uint x = 0b_1001;
Console.WriteLine($"Before: {Convert.ToString(x, toBase: 2), 4}");

uint y = x >> 2;
Console.WriteLine($"After:  {Convert.ToString(y, toBase: 2).PadLeft(4, '0'), 4}");
// Output:
// Before: 1001
// After:  0010
```

#### Unsigned Right-Shift Operator

Available in C# 11 and later, the `>>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand. 

The `>>>` operator always performs a *logical shift*. That is, the high-order empty bit positions are always set to zero, regardless of the type of the left-hand operand. 

The `>>` operator performs an *arithmetic shift* (that is, the value of the most significant bit is propagated to the high-order empty bit positions) if the left-hand operand is of a signed type. 

```cs
int x = -8;
Console.WriteLine($"Before     {":",14} {Convert.ToString(x, toBase: 2),32}");

int y = x >> 2;
Console.WriteLine($"After x>>2 {":",14} {Convert.ToString(y, toBase: 2),32}");

int z = x >>> 2;
Console.WriteLine($"After x>>>2{":",14} {Convert.ToString(z, toBase: 2).PadLeft(32, '0'),32}");

// Output:
// Before                   : 11111111111111111111111111111000
// After x>> 2              : 11111111111111111111111111111110
// After x>>> 2             : 00111111111111111111111111111110
```

#### Logical AND Operator

The `&` operator computes the bitwise logical AND of its integral operands:

```cs
uint a = 0b_1111_1000;
uint b = 0b_1001_1101;
uint c = a & b;
Console.WriteLine(Convert.ToString(c, toBase: 2));
// Output:
// 10011000
```

#### Logical OR Operator

The `|` operator computes the bitwise logical OR of its integral operands:

```cs
uint a = 0b_1010_0000;
uint b = 0b_1001_0001;
uint c = a | b;
Console.WriteLine(Convert.ToString(c, toBase: 2));
// Output:
// 10110001
```

#### Logical Exclusive OR Operator

The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its integral operands:

```cs
uint a = 0b_1111_1000;
uint b = 0b_0001_1100;
uint c = a ^ b;
Console.WriteLine(Convert.ToString(c, toBase: 2));
// Output:
// 11100100
```

### Equality Operators

The `==` (equality) and `!=` (inequality) operators check if their operands are equal or not. Value types are equal when their contents are equal. Reference types are equal when the two variables refer to the same storage.

#### Equality Operator

The equality operator `==` returns `true` if its operands are equal, `false` otherwise.

##### Value types equality

Operands of the built-in value types are equal if their values are equal:

```cs
int a = 1 + 2 + 3;
int b = 6;
Console.WriteLine(a == b);  // output: True

char c1 = 'a';
char c2 = 'A';
Console.WriteLine(c1 == c2);  // output: False
Console.WriteLine(c1 == char.ToLower(c2));  // output: True
```
##### Reference types equality

By default, two non-record reference-type operands are equal if they refer to the same object:

```cs
public class Program
{
    public class MyClass
    {
        private int id;
        public MyClass(int id) => this.id = id;
    }

    static void Main()
    {
        var a = new MyClass(1);
        var b = new MyClass(1);
        var c = a;
        Console.WriteLine(a == b);  // output: False
        Console.WriteLine(a == c);  // output: True
    }
}
```

#### Inequality Operator

The inequality operator `!=` returns `true` if its operands aren't equal, `false` otherwise. For the operands of the built-in types, the expression `x != y` produces the same result as the expression `!(x == y)`

The following example demonstrates the usage of the `!=` operator:

```cs
int a = 1 + 1 + 2 + 3;
int b = 6;
Console.WriteLine(a != b);  // output: True

string s1 = "Hello";
string s2 = "Hello";
Console.WriteLine(s1 != s2);  // output: False

object o1 = 1;
object o2 = 1;
Console.WriteLine(o1 != o2);  // output: True
```