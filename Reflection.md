# Reflection

## Java
Java supports the ability to find the methods of a class, obtain information about the constructors of a class, find information about class
fields, invoke methods by name, create new objects, changing the values of fields, and manipulating arrays, all through the use of Reflection.

Here is an example of Reflection being used to find out information about the constructors of a class:
```java
 import java.lang.reflect.*;
        
   public class constructor1 {
      public constructor1()
      {
      }
        
      protected constructor1(int i, double d)
      {
      }
        
      public static void main(String args[])
      {
         try {
           Class cls = Class.forName("constructor1");
        
           Constructor ctorlist[]
               = cls.getDeclaredConstructors();
         for (int i = 0; i < ctorlist.length; i++) {
               Constructor ct = ctorlist[i];
               System.out.println("name 
                 = " + ct.getName());
               System.out.println("decl class = " +
                            ct.getDeclaringClass());
               Class pvec[] = ct.getParameterTypes();
               for (int j = 0; j < pvec.length; j++)
                  System.out.println("param #" 
                     + j + " " + pvec[j]);
               Class evec[] = ct.getExceptionTypes();
               for (int j = 0; j < evec.length; j++)
                  System.out.println(
                    "exc #" + j + " " + evec[j]);
               System.out.println("-----");
            }
          }
          catch (Throwable e) {
             System.err.println(e);
          }
      }
   }
```
The output of the program:
```
name = constructor1
   decl class = class constructor1
   -----
   name = constructor1
   decl class = class constructor1
   param #0 int
   param #1 double
   -----
```

## Swift
Swift has some basic Reflection abilities, but not to the extent that Java does. There is the notion of a "mirror" in Swift that describes the 
parts that make up a particular instance, such as the instance’s stored properties, collection or tuple elements, or its active enumeration case.

```swift
struct Point {
    let x: Int, y: Int
}

let p = Point(x: 21, y: 30)
print(String(reflecting: p))
// Prints "▿ Point
//           - x: 21
//           - y: 30"
```
