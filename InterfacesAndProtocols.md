[Back to Main](README.md/#interfaces)

# Interfaces and Protocols

## Java
Java supports the use of Interfaces. An interface, when implemented by a class, describes the methods that the class must use, but not how to
do them. It sets a default behavior that the class must adhere to.

```java
public class TestClass implements TestInterface {
  //...
}
```
The above code specifies that our Class `TestClass` must implement the methods defined in the `TestInterface` interface.
```java
public interface TestInterface {
void doMethod();
}

public class TestClass implements TestInterface {
  //...
  
  public void doMethod(){
  //...
  }
```

If the class does not provide a method body, the class must be created as abstract.

By default, Java does not support the use of multiple inheritance in case of class, so we must interfaces to achieve it. We can also use them
to achieve total abstraction. A major benefit of Interfaces is that they help facilitate the implementation of Object Oriented Designs, like the
Prototype Patter or Decorator Pattern

## Swift
Swift supports the use of Protocols. A protocol defines a blueprint of methods, properties, and other requirements that suit a particular task 
or piece of functionality. The protocol can then be adopted by a class, structure, or enumeration to provide an actual implementation of those 
requirements.  Any type that satisfies the requirements of a protocol is said to conform to that protocol. 

```swift
    protocol SomeProtocol {
        // protocol definition goes here
    }
```

A key feature of protocols is that we may extend them with other protocols. Assume we have a protocol:
```swift
protocol Fireable {
    var magazineSize: Int { get }
}
```
and we wish to extend its functionality with another protocol. Let's do so, adding a maxDistance property:
```swift
protocol Bombable: Fireable {
    var maxDistance: Double { get }
}
```
We now have two interfaces, with `Bombable` containing both properties and `Fireable` containing only its `magazineSize` property. We can
do this type of extension to any protocols we create.

To implement a protocol onto a class or struct, for example, the implementation is as such:
```swift
struct myStruct: myProtocol, anotherProtocol {
  //...
}
```
As in Java, classes or structs in Swift with protocols must provide the properties located with the protocols. Also as in Java, protocols
help us facilitate multiple inheritance and extend similar functionality across multiple related classes or structs. For example, we may have
a `gameProtocol` protocol and two classes, `chessClass` and `checkersClass`. The tho classes will have different methods, but for similar
properties and methods we may provide them in the `gameProtocol` protocol.


[Back to Main](README.md/#interfaces)
