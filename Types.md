//What types does the language support?
//Are both reference and value types supported?
//Can new value types be created?
# Types

## Java

Java supports primitive types, class types, and interface types. The 8 primitive types in Java are:
* boolean
* char
* byte
* short
* int
* long
* float
* double

These 8 primitives are value types, and they are the only value types in Java. All the other types are reference types, meaning they reference objects. New value types cannot be created. Class types are identical to the name of the class (blueprint) for that type. An illustration of Java types is shown below.

```

int myInt = 5;
boolean myBool = false;
float myFloat = 3.14159
char myChar = 'a';

class Dog {}
Dog myDog = new Dog()

```

## Swift

Swift supports Both Reference and value types.  As opposed to Java, Swift supports many value types from basic primitives, to C equivalent types, and even custom value types. 

The Swift standard library supports 5 basic value types:
* Strings
* Arrays
* Dictionarys
* Sets
* Numeric Types
    * Bool
    * Int
    * Double
    * Float
    * Range/ClosedRange
    
One of the biggest differences between Swift and Java is that Swift supports the creation of new value types. Structs, for instance, can be created using the **struct** keyword. An example of Swift types is shown below.

```
let name: String = "Adam"
var age: Int = 25

struct Car {}

let car = Car()

class Dog {}

let dog: Dog = Dog()
```

As opposed to Java, in Swift a member's type can be inferred from initial value,, and does not need to be stated explicitly. An example is shown below. 

```

let school = "Mizzou"
var id = 435
let pi = 3.14159

class Dog {}

let dog = Dog()

```
In this example, school's type is being inferred as a String, id as an Int, pi as Double, and dog as a Dog.

The biggest of all the differences between Java & Swift, in my opinion, is the *optional* type. Unlike Java regular types in Swift are **NOT** allowed to be set to nil (null in Java). Instead Swift has what are called optionals, which can be thought of as a box that that contains one of two things; a value of a specific type, or nil. Optional types must be 'unwrapped' to access this value before using them. An example of swift optionals is shown below.

```

var university: String?
var ID: Int? = 5

if let school = university {
    print(school)
}

if let id = ID {
    print(id)
}

```

in this example both university and ID are optionals. university is not given an initial value but ID is, therefore university will be set to nil. When attempting to print the variables, we must first unwrap the optional into a temporary variable that will be of the same type as what the optional contained.


[Back to Main](README.md/#Types)

