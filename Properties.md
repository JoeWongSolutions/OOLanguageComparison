# Properties

## Java
In Java, properties are actually referred to as 'fields'. A Java field is a variable inside of a class.

The Java field access modifier determines whether the field can be accessed by classes other than the the class owning the field. There are four possible access modifiers for Java fields:

* private
* default
* protected
* public

Fields with a private access modifier can only  be accessed from inside the class itself.

Fields with a default access modifier can only be accessed from inside the class itself, or other classes in the same package. You don't actually write the package modifier. By leaving out any access modifier, the access modifier defaults to package scope.

Fields with the protected access modifier can be accessed from inside the class itself, other classes in the same package, or any subclasses of the class even if the subclass is not located in the same package.

Fields with a public access modifier can be accessed by all classes in the application.

Here is an example of fields being declared with access modifiers.

```
public class Dog {

    private   String Sex;
              String name;
    protected String breed;
    public    String age;

}
```

In Java, getters and setters for fields must be created explicitly by the developer. Depending upon the field's access modifier, direct access to it may be limited throughout the application, making it unusable without creating getters & setters. Below is an example of creating a getter and setter for a Java Field.

```
public class Dog {

    String name;

    public void getName() {
        return name;
    }
    
    public void setName(Sting name) {
        this.name = name
    }
}
```


## Swift
With Swift, the properties are actually referred to as properties. Swift properties associate values with a particular class, structure, or enumeration. In addition to simple stored properties, which store constant and variable values as part of an instance, Swift implemented a new type of property not seen in Java known as a computed property. Computed properties are calculate a value every time the property is asked for & do not actually store a value. Instead, they provide a getter and an optional setter to retrieve and set other properties and values indirectly. An example of stored and computed properties, with getters and setters, is shown below.

```
class Block {
    var size: Int = 10.0

    var origin: Point {
        var x = 0.0, y = 0.0
    }
    
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
    }
}
```
The current center position of a Block may be determined at any moment from its origin and size, and so it isnt necessary to store the center point as an explicit Point value. Instead, we define a custom getter and setter for a computed property called center, to enable you to work with the center as if it were a real stored property.

Swift provides five different access levels for entities within your code. These access levels are relative to the source file in which an entity is defined, and also relative to the module that source file belongs to.

* Open access 
    * Open classes can be subclassed within the module where they’re defined, and within any module that imports the module where they’re defined.
    * Open class members can be overridden by subclasses within the module where they’re defined, and within any module that imports the module where they’re defined.
* Public access 
    * Classes with public access, or any more restrictive access level, can be subclassed only within the module where they’re defined.
    * Class members with public access, or any more restrictive access level, can be overridden by subclasses only within the module where they’re defined.

* Internal access
    * Enables entities to be used within any source file from their defining module, but not in any source file outside of that module. This is the default access level that will be set to any entity not explicitly defining one.

* File-private access 
    * Restricts the use of an entity to its own defining source file. 
    
* Private access
    * Restricts the use of an entity to the enclosing declaration, and to extensions of that declaration that are in the same file.
    
    An example of properties being declared with explicit access modifiers and no access modifiers is shown below.
    
```
public class SomePublicClass {}
internal class SomeInternalClass {}
fileprivate class SomeFilePrivateClass {}
private class SomePrivateClass {}

public var somePublicVariable = 0
internal let someInternalConstant = 0
fileprivate func someFilePrivateFunction() {}
private func somePrivateFunction() {}

class SomeOtherInternalClass {}
let someOtherInternalConstant = 0  
```
Since SomeOtherInternalClass and someOtherInternalConstant were declared without an explicit access modifier, they were defaulted to internal.

   





