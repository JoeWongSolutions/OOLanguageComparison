# Classes

## Java
In Java, EVERYTHING is in a class.  Defining a class in Java usually begins in a new file, however classes within a class (Inner class) are also possible. Below is an example of a class definition in Java

```
public class Dog {
    String breed;
    int age;
    String color;

    void barking() {
    }

    void hungry() {
    }

    void sleeping() {
    }
}
```

Below is an example of an Inner Class being defined within an existing class.

```
class Outer_Demo {
    int num;

    // inner class
    private class Inner_Demo {
        public void print() {
            System.out.println("This is an inner class");
        }
    }
}
```
Creating new Instances of a class in Java, also known as 'instantiation' requires the use of the **new** keyword. An example of class instantiation is shown below.

```
public class Puppy {
    public Puppy(String name) {
        // This constructor has one parameter, name.
        System.out.println("Passed Name is :" + name );
    }

    public static void main(String []args) {
        // Following statement would create an object myPuppy
        Puppy myPuppy = new Puppy( "tommy" );
    }
}
```
Initialization of a new instance in Java is achieved via the objects **constructor**. Every class in Java has a constructor. If we do not explicitly write a constructor for a class, the Java compiler builds a default constructor for that class. In Java, the constructor is a method with the same name as the class. Each time a new object is created, at least one constructor will be invoked.  An example of a Java constructor is shown below.

```
public class Puppy {
    public String name;
    public Int age;
    public String breed;

    public Puppy(String name, Int age, String Breed) {
        this.name = name;
        this.age = age;
    }
}
```
The Java language does not support **de**structors. Java has implemented a 'garbage collector' that destroys objects that no longer have any reference to them. This process happens behind the scenes automatically by the JVM.


## Swift

The definition of a class in swift is similar to that of Java, below is an example of a swift class definition.

```
class VideoMode {
    var resolution = Resolution()
    var interlaced = false
    var frameRate = 0.0
    var name: String?
}

```

Creating a new instance of a class in Swift  is similar to Java in that the objects constructor instructor is called via the name of the class followed by parentheses **( )**. However in swift the **new** keyword is not required. An example of class instantiation is shown below.

```
class GameViewController: {

    var level: Level!

    override func viewDidLoad() {
        level = Level()
    }
}

```
In Swift, the initialization of a class performed during instantiation is performed by the class' **Initializer**. As opposed to a Java constructor, a  swift initializer does not share the name of the class, but is instead named **init()**. Although, as shown above, the initializer is invoked using the name of the class. The biggest deiiference in initialization between Seift and Java is that in Swift, classes **must** set all of their stored properties to an appropriate initial value by the time an instance of that class or structure is created. Stored properties cannot be left in an indeterminate state unless they are made optional. Below is an example of a Swift Initializer that will not compile because it fails to set all instance variables.

```
class Temperature {
    var celcius: Double
    var farenheit: Double
    init() {
        celcius = 25.0
    }
}

```
In order to get this code working, we must either make farenheit optional...

```
class Temperature {
    var celcius: Double
    var farenheit: Double?
    init() {
        celcius = 25.0
    }
}

```
or set its value in the initializer...

```
class Temperature {
    var celcius: Double
    var farenheit: Double
    init() {
        celcius = 25.0
        farenheit = celcius * (9/5) + 32
    }
}

```

Unlike Java, Swift supports the implementation of **de**initializers. Swift automatically deletes objects when they are no longer needed, to free up resources, through automatic reference counting.  When you might need to perform some additional cleanup yourself, You may write deinitializers with the **deinit** keyword which can access and modify instance properties .You are not allowed to call a deinitializer yourself, it is called automatically just before the object is deleted. Below is an example of a class deinitializer.

```

deinit {
    NotificationCenter.default.removeObserver(self, name: 
    NSNotification.Name(rawValue: "gotoLogin"), object: nil)
    
    NotificationCenter.default.removeObserver(self, name: 
    NSNotification.Name(rawValue: "gotoMain"), object: nil)
}

```











