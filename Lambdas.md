[Back to Main](README.md/#lambda-expressions-closures-or-functions-as-types)
# Lambdas, Closures, or Function Types in Java and Swift
Sometimes, we need to specify a function or action to take when an event is received. We use Lambda expressions in Java and Closures in Swift to deal with this situation. Lets take a look at the general form for both of these expressions:
```Java
// Lambda Expression for Java
(parameters) -> {
  // Statements
}
```
```Swift
// Closure in Swift
{(Parameters) -> (ReturnType) in 
  // Statements
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
}
```
Wait, did we just assign a function to a variable? It certainly does look like it, but under the hood we are actually overriding the apply() function present in the Function interface. Since Java can determine exactly which function to override (there's only one function) we don't need to specify which function it is. From the interface, the Java compiler can also determine the number of and type of parameters apply() can take and if there is something to be returned. This is why we don't have to specify any extra information in the lambda expression. 
