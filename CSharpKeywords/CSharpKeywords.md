# C# Keywords

In this chapter, You will learn about the below C# Keywords:

- [C# Keywords](#c-keywords)
    - [Access Modifiers](#access-modifiers)


### Access Modifiers

Below are the C# access Modifier keywords:

* `private`
* `public`
* `protected`
* `internal`
* `file`
* `private protected`
* `protected internal`

**Private**

* `private` access is the least permissive access level.
* Private members are accessible only within the body of the class or the struct in which they are declared

In the below example, you cannot access the `employeeId` and `employeeName` fields directly with employee object because they are declared `private`

```cs
internal class Program
{
    static void Main(string[] args)
    {
        Employee employee = new Employee();
        Console.WriteLine(employee.EmployeeId);
        Console.WriteLine(employee.GetEmployeeName());
        Console.ReadLine();
    }
}
public class Employee
{
    private readonly int employeeId = 100;
    private readonly string employeeName = "Test";
    public string GetEmployeeName()
    {
        return employeeName;
    }
    public int EmployeeId { get { return employeeId; } }
}
```

**Public**

* The `public` keyword is an access modifier for types and type members.
* Public access is the most permissive access level.
* There are no restrictions on accessing `public` members

In the below example, you will be able to access `employeeId` and `employeeName` with employee object since they marked as `public`

```cs
internal class Program
{
    static void Main(string[] args)
    {
        Employee employee = new Employee();
        employee.employeeId = 1;
        employee.employeeName = "Anitha";
        Console.WriteLine(employee.employeeId);
        Console.WriteLine(employee.employeeName);
        Console.ReadLine();
    }
}
public class Employee
{
    public int employeeId;
    public string employeeName;
}
```

**Protected**

* A `protected` member is accessible within its class and by derived class instances
* A `protected` member of a base class is accessible in a derived class only if the access occurs through the derived class type

In the below example, `program` object can acess the members of `Employee` because it is derived from `Employee` Class

```cs
internal class Program : Employee
{
    static void Main(string[] args)
    {
        // Error - Because you cannot access protected members directly
        // Employee employee= new Employee();
        // employee.employeeId = 1;
        // employee.employeeName = "Rahul";

        // OK - Because Program class is derived from Employee class
        Program program = new Program();
        program.employeeId = 10;
        program.employeeName = "Rahul";
        Console.WriteLine(program.employeeId);
        Console.WriteLine(program.employeeName);
        Console.ReadLine();
    }
}
class Employee
{
    protected int employeeId;
    protected string employeeName;
}
```

**Internal**

Internal types or members are accessible only within files in the same assembly.


**Example 1:**
* This example contains two files, `Assembly1.cs` and `Assembly2.cs`. 
* The first file contains an internal base class, `BaseClass`. 
* In the second file, an attempt to instantiate BaseClass will produce an error.

```cs
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass
{  
   public static int intM = 0;  
} 
```
```cs
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
} 
```
**Example 2:**
* In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`. 
* Also change the accessibility level of the member `intM` to `internal`. 
* In this case, you can instantiate the class, but you cannot access the internal member.

```cs
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass
{  
   internal static int intM = 0;  
}  
```
```cs
// Assembly1.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```

**File**

* The `file` modifier restricts a top-level type's scope and visibility to the file in which it's declared.
* The `file` modifier will generally be applied to types written by a source generator.
* File-local types provide source generators with a convenient way to avoid name collisions among generated types.
* The file modifier declares a file-local type

```cs
file class Widget
{
// implementation
}
```

**Protected Internal**

* The `protected internal` keyword combination is a member access modifier.
* A `protected internal` member is accessible from the current assembly or from types that are derived from the containing class

```cs
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
    protected internal int myValue = 0;
}
class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```cs
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();
        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

**Private Protected**

* The `private protected` keyword combination is a member access modifier.
* A `private protected` member is accessible by types derived from the containing class, but only within its containing assembly

```cs
public class BaseClass
{
    private protected int myValue = 0;
}
public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();
        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;
        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```
```cs
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
    // Error CS0122, because myValue can only be
    // accessed by types in Assembly1
    // myValue = 10;
    }
}
```