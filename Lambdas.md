[Back to Main](README.md/#lambda-expressions-closures-or-functions-as-types)
# Lambdas, Closures, or Function Types in Java and Swift
Sometimes, we need to specify a function or action to take when an event is received. We use Lambda expressions in Java and Closures in Swift to deal with this situation. Lets take a look at the general form for both of these expressions:
```Java
// Lambda Expression for Java
(parameters) -> {
  // statements
}
```
```Swift
// Closure in Swift
{(parameters) -> (returnType) in 
  // statements
}
```
Both use the -> but they are actually being used for different purposes. In Java, the -> signifies the use of a lambda expression but for Swift, the -> actually specifies the return type. The use of the keyword 'in' is the start of the actual body of the closure. So why do we not specify a return type for Java? This gets into our next topic which is how Lambdas are actually implemented in Java.

### Lambdas in Java
Since Java started out as a purely Object Oriented Language, having functions being passed around was quite a hassle. Functions must exist inside of a class so in order to pass a function, you had to create or assign a class for every function you passed. Even today, Java still struggles with this issue but they have made the illusion that functions can exist independently through a clever use of functional interfaces and anonymous classes. Consider the Function Interface:
```Java
@FunctionalInterface
public interface Function<T,R> {
   public R apply(T t);
}
```
This interface takes one generic of type T and returns a generic of type R. The @FunctionalInterface annotation prevents users of the interface from adding more abstract methods to the interface and allows the compiler to throw an exception if more than one method exists. The presence of one and only one method is crucial to how lambda expression work. If we wanted to use the interface, we could write something like:
```Java
Function<Integer, Integer> add1 = (x) -> {
  x+1;
};
```
Wait, did we just assign a function to a variable? It certainly does look like it, but under the hood we are actually overriding the apply() function present in the Function interface. Since Java can determine exactly which function to override (there's only one function) we don't need to specify which function it is. From the interface, the Java compiler can also determine the number of and type of parameters apply() can take and if there is something to be returned. This is why we don't have to specify any extra information in the lambda expression. So what about anonymous inner classes? We didn't instantiate anything with the 'new' keyword so why do we even need them? Technically we are instantiating a class, even if we don't see the 'new' keyword because of how Java8 works. The equivalent anonymous class we created would look like this:
```Java
public class MathApplier implements Function<Integer, Integer> {
  public Integer apply(Integer x) {
    return x;
  }
}
Function<Integer, Integer> add1 = new MathApplier() {
  @Override
  public Integer apply(Integer x) {
    return x + 1;
  }
};
```
First, we needed to create a class called MathApplier that implements the correct interface. Then we instantiate an new instance of the MathApplier class and override the apply() method. This is all explicitly written in the code but with lambdas, we could infer all of this information from the interface. What about closures? Are they similarly implemented in Swift?
### Closures in Swift
In Swift, functions are considered "first class" which means functions can exist on their own as data. We can pass functions around as parameters and also return functions. See the [function programming](FunctionalProgramming.md) section for more details. This is how the above examples would have been writtin in Swift:
```Swift
function add1(_ x: Int) -> Int {
  return x + 1
}
```
Thats it! We can now pass add1 to any other variable or function and use it. Then why do we need closures? Closures allow us to specify a behavior (function) without explicitly naming the function. Consider if we had a function like the following:
```Swift
function doMath(_ x: Int, _ mathFunction: (Int) -> Int) -> {
  return mathFunction(x)
}
// Now we can pass add1 to this function
print(doMath(1, add1) // Outputs 2

//We can also avoid creating add1 altogether and just pass a closure
print(doMath(1, {(_ x: Int) -> Int in
  return x + 1
}) //outputs 2 as well
```
Sometimes we need a function but it will only be used once in the program. Closures are a nice way to avoid creating functions and still get the behavior we need. 
### Function types
In Java we used the interface type to determine the function type of the lambda expression. In Swift, the function type is a bit more generic. In the doMath function, we specified mathFunction (the parameter taken by doMath) to be of type: (Int) -> Int. That is, we needed a type of function that took an Int and returned an Int. The underlying logic did not matter so any function with this type can be used. This flexibility is not inherent in Java. If two interfaces have the same method with the same method signature, we cannot substitute one for the other. 

[Back to Main](README.md/#lambda-expressions-closures-or-functions-as-types)
