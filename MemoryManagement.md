# Memory Management

## Java

Java objects are placed into a heap, which is created when the Java Virtual Machine starts and may grow or shrink in size.  If the heap becomes
full, the garbage is collected. What this means is that if an object is no longer being used, then it is cleared from the heap, allowing
new objects space to be created. Java does not support automatic reference counting in its garbage collection process.

It should be noted that not all memory is allocated to the heap. Processes such as thread stacks and native handles are seperate from the heap.

The heap itself is divided into two areas: the young space and the old space. The young space is where new objects are allocated. Given that an
object has existed in the young space for enough time, it is promoted into the old space, so that more new objects can be placed into the young
space. This division of the two spaces is due to the fact that objects are typically short lived and temporary, and garbage collection on the
young space frees up memory faster than on the old space.

## Swift

Swift, unlike Java, does use automatic reference counting in its memory management routine. It works by automatically freeing up the memory used
by class instances when those instances are no longer needed. It also allocates chunks of memory to store information about instances of classes
that the user has created. It should be noted that this only applies to instances of classes. Values types like structs and enumerations are not 
considered.

When a class instance is assigned to a property, constant, or variable, a strong reference is made with the instance. A strong reference refers
to the fact that the reference has a "strong" or firm hold on the instance, and does not allow it to be deallocated so long as the reference
remains intact. You may however initialize you would like a weaker reference onto the instance, in which case you would place the `weak` keyword
before a variable or property declaration. This type of reference works by having the automatic reference counting routine set the reference to
`nil` when it is deallocated. Weak references need to be declared as optional variables.

An example of strong referencing in Swift:
```swift
    class Person {
        let name: String
        init(name: String) { self.name = name }
        var apartment: Apartment?
        deinit { print("\(name) is being deinitialized") }
    }
     
    class Apartment {
        let unit: String
        init(unit: String) { self.unit = unit }
        var tenant: Person?
        deinit { print("Apartment \(unit) is being deinitialized") }
    }
```
This code above is simply to create our classes. Below we will create variables by which to make our references:
```swift
    var john: Person?
    var unit4A: Apartment?
```
We will now assign the variable, with `john` having a strong reference to the new `Person` instance, and `unit4A` having a strong reference to the new `Apartment` instance:
```swift
    john = Person(name: "John Appleseed")
    unit4A = Apartment(unit: "4A")
```

To create a an example of a `weak` refence type, we will simply change the line `var tenant: Person?` in our Apartment class to `weak var tenant: Person?`

Swift does not support garbage collection, unlike Java.
