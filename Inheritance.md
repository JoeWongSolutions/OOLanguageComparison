[Back to Main](README.md/#inheritance)
# Inheritance / Extension

## Java

Inheritance in Java is the process by which a sub-class acquires the fields and methods of a super-class. This provides reusable code for creating a sub-class, which only needs to include the features unique to it. In Java, this is performed using the **extends** keyword following the subclass and preceeding the superclass. An example of inheritance in Java is shown below. In The example, the sub-class Truman is inheriting from the super-class Faculty & the sub-class Teacher is inheriting from the super-class Faculty and Human.

```
class Faculty {}
class Human {}

class Truman extend Faculty {}
}

class Teacher extends Faculty, Human {
}
```

Unlike Swift, Java supports abstract classes which can (must) be inherited from. A Java abstract class is a class with atleast one abstract method, meaning it is defined without an implementation. Any class that inherits from an abstract class must either provide an implementation for all abstract methods, or be abstract itself. A benefit of subclassing from an abstract versus concrete class is that it allows us to define a unique implementation for required functionality. An example of abstract inheritance is shown below. In the example the classes Woof and Meow both extend the abstract class Speak.

```

public abstract class Speak {
    public void speak(){}
}

public class Woof extends Speak {
    public void speak {
        System.out.println("Woof!")
    }
}
    
public class Meow extends Speak {
    public void speak {
        System.out.println("Meow!")
    }
}


```

## Swift

Inheritance in Swift follows the same basic priciples as in Java. However, instead of the **extends** keyword, Swift uses a colon **:** placed after the sub-class name and before the super-class name(s). An example of class inheritance in swift is shown below. In the example, the sub-class Circle is inheriting from the super-class Symmetrical and the sub-class Square is inheriting from the super-classes Symmetrical and Rectangle.
```

class Rectangle {}
class Symmetrical {}

class Circle: Symmetrical {}
class Square: Symmetrical, Rectangle {}

```

Unlike Java, Swift supports class *extensions*. Where new functionality is added to an existing class, structure, enumeration, or protocol type. The beauty in extensions is that it allows us to add new functionality to existing types without modifying the source code. This allows one to to alter types for which they do not the source code and prevents possible conflicts with other clients that rely on it. An extension can even be used to extend an existing generic type. An example is shown below.

```

extension Double {
    var km: Double { return self * 1_000.0 }
    var m: Double { return self }
    var cm: Double { return self / 100.0 }
    var mm: Double { return self / 1_000.0 }
    var ft: Double { return self / 3.28084 }
}

let oneInch = 25.4.mm
print("One inch is \(oneInch) meters")
// Prints "One inch is 0.0254 meters"

```

In this example we are adding to functionality to the generic Double type. When we assign 25.4.mm to oneInch, the computed property in the extension returns the value of its **self** (25.4) divided by 1000.

Swift extensions can add properties, methods, and even initializers to existing types, but they also 
    can even extend a protocol to add functionality or provide implementations of its requirements. This allows the definition of behavior on protocols themselves, rather than in each conforming type’s.
    
    ```
    protocol Configurable {
        func configurationFileName() -> String
    }
    
    extension Configurable {
        func configurationFileName() -> String {
            return "default.config"
        }
    }
    
    class ConfigurableClass: Configurable {}
    
    ConfigurableClass.configurationFileName() //"default.config"
    CustomConfigurableClas.configurationFileName() //"custom.config"
    
    ```
    
[Back to Main](README.md/#inheritance)

