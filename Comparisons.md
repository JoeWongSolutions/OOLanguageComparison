# Comparisons of References and Values

## Java
In Java, we can compare reference types two ways: using the `==` operator and using the `.equals()` method. The equality operator == is used
to check the memory location of two objects. This means that given the memory addresses of two objects are the same, the operation will 
evaluate to `true`:

```java
Guest guest1 = new Guest("name");
Guest guest2 = guest1;
if (guest1 == guest2)
  System.out.println("They are equal")
  //This will print out "They are equal"
```

To compare the contents of two object classes, we can use the `.equals()` method to compare the two objects. By default, the `.equals()` method
uses the same logic as the `==` operator, meaning that only memory location is checked between the two objects. To fix this, we must override
the method and provide it logical operations that will compare the values of the objects we wish to check.

Here is an example using the overridden `.equals()` function of Class `String`:

```java
class MyComparisons {

	  String first = "chairs";
	  String second = "chairs";
	  String third = new String ("chairs");
    
    void myMethod( ) {
	  // This evaluates to true
	  if (first.equals(second)) {
	    System.out.println("first equals second");
	  }
	  // This evaluates to false
	  if (first == third) {
	    System.out.println("first == third");
	  }
	  // This evaluates to true
	  if (first.equals(third)) {
	    System.out.println("first equals third");
	  }
```

Note that both comparisons will work correctly (will check value, not address) given that the items being compared are primitive data types.

## Swift

There are two operators we may use in Swift when we wish to do comparisons: the `==` operator is used to compare values, and the `===` operator
is used to compare references. 

The `==` will return `true` given that both items being compared contain the same values:
```swift
let a = 10
let b = 10
let c = 11
a == b        // true; 10 == 10
a == c        // false; 10 != 11
```

Note that arrays are also considered as value types in Swift:
```swift
let d = [1, 2, 3]
let e = [4, 5, 6]
let f = [1, 2, 3]
d == e        // false
d == f        // true
```

The `===` operator will check if two references refer to the same object. 
```swift
class MyObject : Equatable {
  let a : Int, b : String
  init(a: Int, b: String) { self.a = a; self.b = b }
}

let a = MyObject(a: 10, b: "foo")
let b = a
let c = MyObject(a: 10, b: "foo")

a == b    // true; 'a' and 'b' are equal in value
a === b   // true; 'a' and 'b' point to the same instance

a == c    // true; 'a' and 'b' are equal in value
a === c   // false; 'a' and 'c' are different instances
```
