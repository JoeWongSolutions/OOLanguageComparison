[Back to Main](README.md/#null/nil-references)

# Null and Nil References

## Java
In Java, the keyword used is `null`. Java does support features that help handle null references. There are two annotations that may be used:
@Nullable and @NotNull. These annotations allow you to check nullability of a variable, parameter, or return value.

Here is an example of @NotNull being used in the parameters of a method call:
```java
public void foo (@NotNull Object param){
  int i = param.hashCode();
}
```

The @NotNull annotation is, actually, an explicit contract declaring that a method should not return null and that variables (fields, local 
variables, and parameters) cannot hold a null value.

The @Nullable annotation is placed above a method call:
```java
@Nullable
public void foo (Object param){
}
```

## Swift
In Swift, the keyword used is `nil`. In Swift, to help curb `nil` values being passed around, we have the notion of optionals. These optional 
types handle the absence of a value. An optional represents two possibilities: either there is a value and you can unwrap it, or there is no
value. To create an optional, create a variable with `?` at the end:

```swift
var testVariable: String?
```

In order to use the value of an optional, the optional must be unwrapped. This process of unwrapping is a way for us to check that the optional
is not null and therefore we can use its value. We may choose to force unwrap the optional using `!` at the end of the optional's name:

```swift
print("testNumber has an integer value of \(testNumber!).")
```
While this is an option available to us, its basically a way of saying "We know this won't be nil, let us use the value." If used incorrectly, 
it is possible to unwrap a nil variable and end up with a nil error.

The other way in which we attempt to unwrap optionals is by optional chaining. Whereas forced unwrapping may fail and break a program, optional
chaining fails gracefully and doesn't lead to as many issues:
```swift
    class Person {
        var residence: Residence?
    }
     
    class Residence {
        var numberOfRooms = 1
    }
```
Here we create two new classes, with the `Person` class containing an optional variable `residence`. Now we'll assign a variable to a Person
instance:

```swift
let john = Person()
```
If we attempt to find the value of this person's numberOfRooms property via forced unwrap, we will end up with a runtime error due to the optional
value being `nil`:
```swift
let roomCount = john.residence!.numberOfRooms
// Results in runtime error
```

Now let us attempt to unwrap the value via optional chaining:
```swift
if let roomCount = john.residence?.numberOfRooms {
    print("John's residence has \(roomCount) room(s).")
} else {
    print("Unable to retrieve the number of rooms.")
}
```
This will print "Unable to retrieve the number of rooms." until the value is specified, but the point is that with this implementation, our
code will not lead to a runtime error crashing our program.

[Back to Main](README.md/#null/nil-references)
