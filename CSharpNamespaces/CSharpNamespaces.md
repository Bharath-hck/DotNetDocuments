# C# Namespaces

In this chapter, You will learn about the below C# Namespaces: 

C# programs are organized using `namespaces`. Namespaces are used both as an “internal” organization system for a program, and as an “external” organization system—a way of presenting program elements that are exposed to other programs.

Namespaces are used in two ways in C# programming:
* .NET uses it to organize many of its classes
* Declaring your own namespaces can help you control the scope of class and method names in larger programming projects.

### Declaring a namespace
Use the `namespace` keyword to declare a namespace, as in the following example:

```cs
namespace SampleNamespace
{
    class SampleClass
    {
        public void SampleMethod()
        {
            System.Console.WriteLine(
                "SampleMethod inside SampleNamespace");
        }
    }
}
```

Beginning with **C# 10**, you can declare a namespace for all types defined in that file, as shown in the following example:

The advantage of this new syntax is that:
* It's simpler
* Saving horizontal space and braces
* Makes your code easier to read.

```cs
namespace SampleNamespace;

class AnotherSampleClass
{
    public void AnotherSampleMethod()
    {
        System.Console.WriteLine(
            "SampleMethod inside SampleNamespace");
    }
}
```

### Namespaces overview
Namespaces have the following properties:

* They organize large code projects.
* They're delimited by using the `.` operator.
* The `using` directive obviates the requirement to specify the name of the namespace for every class.
* The global namespace is the "root" namespace: `global::System` will always refer to the .NET System namespace.

### The using Keyword

The `using` keyword states that the program is using the names in the given namespace. For example, we are using the `System` namespace in our programs.

The class `Console` is defined there. We just write:
```cs
Console.WriteLine ("Hello there");
```

We could have written the fully qualified name as:
```cs
System.Console.WriteLine("Hello there");
```

### Nested Namespaces
You can define one namespace inside another namespace as follows:

```cs
namespace namespace_name1 {
   
   // code declarations
   namespace namespace_name2 {
      // code declarations
   }
}
```

