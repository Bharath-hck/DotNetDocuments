## C# Operators

In this chapter, You will learn about the below C# Operators: 

### Operators

* Arithmetic Operators 
* Comparison Operators
* Boolean Logical Operators
* Bitwise and Shift Operators
* Equality Operators

### Arithmetic Operators 

Operators that perform arithmetic operations with numeric operands

* Unary:
 	* (++) increment
	* (--) decrement
	* (+) plus)
	* (-) minus)

* Binary:
    * (*) multiplication
    * (/) division
    * (%) remainder
    * (+) addition
    * (-) subtraction

#### Increment Operator (++)
* The unary increment operator `++` increments its operand by `1`. 
* The operand must be a variable, a property access, or an indexer access.
* The increment operator is supported in two forms: 
    * the postfix increment operator, `x++` 
    * the prefix increment operator, `++x`


##### Postfix Increment Operator

The result of `x++` is the value of `x` before the operation, as the following example shows:


```csharp
int i = 3;
Console.WriteLine(i);   // output: 3
Console.WriteLine(i++); // output: 3
Console.WriteLine(i);   // output: 4
```











#### Addition Operator `+`

The addition operator `+` computes the sum of its operands:

``` cs
// Some comments
    internal class Program
    {
        static void Main()
        {
            Console.WriteLine(5 + 4);       // output: 9
            Console.WriteLine(5 + 4.3);     // output: 9.3
            Console.WriteLine(5.1m + 4.2m); // output: 9.3
        }
    }
```
    
