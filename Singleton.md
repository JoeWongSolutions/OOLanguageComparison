[Back to Main](README.md/#singleton)
# Singletons in Java and Swift
Singletons are classes that allow only 1 instance of itself to ever be created. Both Java and Swift support singletons. Although this practice is discouraged, there are some cases in which singletons can be a good implementation. We discuss the differences in implementing singletons in this section starting with Java:
```Java
// Code credit goes to Pankaj from www.journaldev.com
public class BillPughSingleton {

    private BillPughSingleton(){}
    
    private static class SingletonHelper{
        private static final BillPughSingleton INSTANCE = new BillPughSingleton();
    }
    
    public static BillPughSingleton getInstance(){
        return SingletonHelper.INSTANCE;
    }
}
```
In case you are wondering, Bill Pugh invented this style of singleton to address lazy instantiation as well as thread safety when creating singleton classes. The magic happens in the nested static class (SingletonHelper) that creates the new instance. Nested static classes are by default lazily instantiated so no instance of our singleton exists until getInstance() is called. Also, since the instantiation is being conducted through the use of a nested class, only 1 thread can ever instantiate the object. Here is the code in Swift:
```Swift
final class Singleton{

  static let sharedInstance = new Singleton()
  
  private init(){}
}
```
In Swift, static fields are automatically lazily instantiated only once. It is also by default thread safe. So singletons in Swift require much less code to write. We included a private empty init() in order to prevent others from instantiating the singleton elsewhere because by default, all classes have a public initializer. Making the class final also prevents subclassing the singleton which can lead to problems. 

[Back to Main](README.md/#singleton)
