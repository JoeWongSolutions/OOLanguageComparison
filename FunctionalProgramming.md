[Back to Main](README.md/#functional-programming)
# Functional Programming in Java and Swift
Java, born as a pure object oriented language, lacked functional programming abilities until recently. Java 8 has joined in on the functional programming craze but it still has some kinks to work out. Swift was born a multi-paradigm language and has a rich set of functional programming abilities right out of the box. To really get a feel for how these languages differ, we will look at a few core concepts of functional programming, namely:
1. First class functions (functions that can exist as data)
2. Higher Order Functions (functions that can take other functions as input or return functions as output)
3. Immutable data (data that cannot be changed)
### First Class Functions
In Java, this is as awkward as it gets when trying to talk about functional programming abilities. Inherently, Java does not support first class functions. Functions can only exist inside a class. However, Java has made the syntax for lambdas appear as though functions can exist independently. If you need a refresher on Java lambdas, you can go back and read it [here](#). Remember a lambda function looks like:
```Java
x -> x + 1;
```
If we wanted to bind this function to a variable, we could do something like:
```Java
Function<Integer,Integer> incrementByOne = x -> x + 1;
```
Now we can use incrementByOne on other variables to add 1 to the variable:
```Java
Integer six = incrementByOne.apply(5);
System.out.println(six); //yields 6
```
Let's do the same thing but with Swift:
```Swift
func incrementByOne(_ a: Int) -> Int { return a + 1 }
var six = incrementByOne(5)
print(six) //yields 6
```
Since functions are already first class citizens in Swift, we have no problems using the function directly after declaring it.
### Higher Order Functions
In Java, we can assign lambdas to the parameter list of other functions through the use of functional interfaces. In reality, we aren't passing the function per se, but instead pass an anonymous inner class which implements the functional interface and the function happens to exist within this class. Take a look at the following example:
```Java
public static Class Util {
  public int doMath(Integer x, Function<Integer, Integer> y) {
    return y.apply(x);  
}

Integer six = Util.doMath(5, x -> x + 1);
System.out.println(six); // yields 6
```
We created a static class called Util and inside Util is a method called doMath that takes an Integer as a first argument and an object of type Function as the second argument. We then used the same code from above to assign a lambda to the second parameter of doMath. Here is the same code but in Swift:
```Swift
func doMath(_ x: Int, _ theFunction: (Int) -> (Int)){
  return theFunction(x)
}

var six = doMath(5, { (number) -> (Int) in
  return number + 1
})

print(six) //yields 6
```
### Immutable Data
In Java, we can make immutable objects by defining all fields as private and const and also by not providing a setter for all fields. Since there is no way to set the fields, objects are considered Immutable. Primitive types in Java simply require a const definition to become immutable. 
```Java
public class ImmutableThing {
  private const String name;
  private const int age;
  
  public ImmutableThing(String name, int age) {
    this.name = name;
    this.age = age;
  }
  
  public String getName() {
    return name;
  }
  
  public int getAge() {
    return age;
  }
}
```
In Swift, there is the notion of using "let" to define an immutable type or object. Objects can also be made immutable in the same fashion as in Java by removing setters from all fields.
```Swift
public class ImmutableThing {
  let name: String;
  let age: Int;
  
  init(name: String, age: Int) {
    self.name = name;
    self.age = age;
  }
}
```
[Back to Main](README.md/#functional-programming)
