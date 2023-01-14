# C# Records

In this chapter, we are going to discuss a new feature added in C#9, called `records`. Records offer an alternative to classes and structs and offer a number of advantages over those types.

### What Are Records?

Records are reference types, just like classes. The main way they differ from classes is when it comes to equality.

Two records are equal if:
* Definitions are equal (e.g same number/name of properties)
* Values in each of those definitions are equal

On the other hand, two classes are equal if:
* The two objects are of the same class type
* Variables refer to the same object

In other words, records use **value-based** equality, whilst classes use **memory-based** equality.

### Basic Syntax
Now that we understand what records are at a high level, let’s dig into how we can actually use them.

To declare a `record`, we use the records yntax, in place of where we would use `class` or `struct`:

```cs
public record Person
```

Using the above syntax, we are implicitly using record **classes**. We can be explicit by using the `class` keyword:

```cs
public record class Person
```
Alternatively, we can use a record struct:

```cs
public record struct Person
```

### Equality

As we mentioned earlier, two records are equal if the definitions and the values are equal.

Let’s look at an example, by creating a simple record:

```cs
public record Person
{
    public Person(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }
    public string LastName { get; set; }
    public string FirstName { get; set; }
}
```

Now let’s create a few records and then see if they are equal:

```cs
public class Program
{
    public static void Main(string[] args)
    {
        var person1 = new Person("Joe", "Bloggs");
        var person2 = new Person("Joe", "Bloggs");
        var person3 = new Person("Jane", "Bloggs");
        Console.WriteLine($"Person1 == Person2? {person1 == person2}");
        Console.WriteLine($"Person1 == Person3? {person1 == person3}");
        Console.ReadKey();
    }
}
```

The output is:.

```cs
Person1 == Person2? True
Person1 == Person3? False
```

As we expected, because person 1 and person 2 share the same definition and values, they are equal, whilst person 3 has a different `FirstName`, so it is not equal.

This behavior can be extremely useful to check if two records have changed, for example, if you’re passing a `record` to a different thread/process and want to see if the values have changed. This ties nicely to the next feature and benefit of records that we will discuss, being `immutability`.

### Immutability of Records

Records are designed to be used for scenarios where immutability is key. For example, if we design a multi-threaded application where we pass objects around. They are also designed to hold data structures and not states.

#### Init-only Properties

We are now using the init operator to specify that the properties of the Person record can only be set during initialization.

```cs
public record Person
{
    public string FirstName { get; init; }
    public string LastName { get; init; }    
}
```

Let’s modify our console app to now use the object initializer to set the properties:
```cs
var person1 = new Person { FirstName = "Joe", LastName = "Bloggs" };
var person2 = new Person { FirstName = "Joe", LastName = "Bloggs" };
var person3 = new Person { FirstName = "Jane", LastName = "Bloggs" };
```

If we then try to modify the FirstName property of person1, we get the following error:

```
CS8852: Init-only property or indexer 'Person.FirstName' can only be assigned in an object initializer, or on 'this' or 'base' in an instance constructor or an 'init' accessor.
```

#### Positional Records

The more concise way of presenting this behavior is by using “**positional records**”.

Let’s modify our Person class again:
```cs
public record class Person(string FirstName, string LastName);
```

Now we can modify our code again to go back to the constructor method:
```cs
var person1 = new Person("Joe", "Bloggs");
var person2 = new Person("Joe", "Bloggs");
var person3 = new Person("Jane", "Bloggs");
```

This is probably the key feature to call out. We want to capture the initial state of the data and pass it around our app, but we do not want anything modifying it in any way.

### Cloning Records

Built into records, there is a special `with` operator we can use:

```cs
var person4 = person3 with { LastName = "Doe" };
Console.WriteLine(person4);
```
In the above example, we are saying that we would like a copy of the `person3` object, but with the `LastName` property set to “Doe”, and all other properties the same. This syntax can come in very handy when we want to create copies of records with only minimal differences.

Behind the scenes, the compiler is doing what is called “**non-destructive mutation**”, where the properties of the original record are copied to the new record, but the original record is not mutated in any way, keeping with the goal of immutability. 

Let’s check the output:

```
Person1 == Person2? True
Person1 == Person3? False
Person { FirstName = Jane, LastName = Doe }
```

The result is what we expect: the `LastName` has been set to what we specified, but the `FirstName` has been based off the `person3` record. One other thing you might notice is the **built-in formatting display**. We didn’t have to create a custom .ToString() method to make it nice and readable, records do this for us! This is a very handy feature that will save us lots of time (and code).

### Inheritance
Just like with normal classes, records support inheritance. Let’s create a derived `Employee` record:

```cs
public record Employee(string FirstName, string LastName, string Job) : Person(FirstName, LastName);
```
The syntax is very similar to regular class inheritance. The properties we inherit from the base record pass to the constructor, and the derived class has its own properties as well.

Next, let’s modify our class to now instantiate our derived class:

```cs
var person1 = new Employee("Joe", "Bloggs" , "Firefigher");
var person2 = new Employee("Joe", "Bloggs", "Teacher");
var person3 = new Employee("Jane", "Bloggs", "Programmer");
```

If we run our app, we’ll see the ToString() built-in formatted we mentioned earlier automatically picks up the new property, without us changing any code:

**Output**

```
Employee { FirstName = Jane, LastName = Doe, Job = Programmer }
```