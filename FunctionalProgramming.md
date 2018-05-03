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
func incrementByOne(_ a: Int) -> Int { a + 1 }
var six = incrementByOne(5)
print(six) //yields 6
```
Since functions are already first class citizens in Swift, we have no problems using the function directly after declaring it.
### Higher Order Functions

### Immutable Data


