# Errors and Exception Handling

## Java

There are two kinds of Exception Handling in Java:
* Default Exception Handling *
Whenever inside a method, if an exception has occurred, the method creates an Object known as Exception Object and hands it off to
the run-time system(JVM). The exception object contains name and description of the exception, and current state of the program 
where exception has occurred. Creating the Exception Object and handling it to the run-time system is called throwing an Exception.

Here is an example of this in action:
'''java
// Java program to demonstrate how exception is thrown.
class ThrowsExecp{
     
    public static void main(String args[]){
         
        String str = null;
        System.out.println(str.length());
         
    }
}
'''

Output:
'''java
Exception in thread "main" java.lang.NullPointerException
    at ThrowsExecp.main(File.java:8)
'''

* Customized Exception Handling *
This is how we as programmers in Java do Exception Handling. There are five keywords we use when handling exceptions: try, catch,
throw, throws, and finally. Statements believed possible to fail are placed within a try block. If an exception occurs, it is thrown.
Code may also be caught within a catch block, and then handled accordingly. If we wish to manually throw an exception, we use the throw
keyword. Exceptions thrown out of a method are specified by throws. Finally will run any code that must be ran.

An example of a try catch clause:
'''java
try {
// block of code to monitor for errors
// the code you think can raise an exception
}
catch (ExceptionType1 exOb) {
// exception handler for ExceptionType1
}
catch (ExceptionType2 exOb) {
// exception handler for ExceptionType2
}
// optional
finally {
// block of code to be executed after try block ends
}
'''

Examples of "throw" and "throws":
'void aMethod() throws Exception1, Exception2 {
 
    // statements...
    if (an exception occurs) {
        throw new Exception1();
    }
 
    // statements...
    if (another exception occurs) {
        throw new Exception2();
    }
}'

## Swift

In Swift, errors are represented by values of types that conform to the Error protocol. This empty protocol indicates that a
type can be used for error handling.

Here is an example of handling errors using enumerations:
'
    enum VendingMachineError: Error {
        case invalidSelection
        case insufficientFunds(coinsNeeded: Int)
        case outOfStock
    }'
    
The "throw" keyword can be used to throw an error, and you may also include necessary parameters that must be met for proper 
execution.

Here is an example of the "throw" keyword being used: 
'throw VendingMachineError.insufficientFunds(coinsNeeded: 5)'

There are four ways for programmers to handle errors within Swift: 
  * Handle using a 'do-catch'
  * Handle the error as an optional value
  * Assert the error won't occur
  * Propogate the error from a function to the code that calls that function
  
For an error in a 'do-catch', the errors are ran in a code block. For an error found in a 'do' clause, its corresponding 'catch'
is ran:
'do {
    try buyFavoriteSnack(person: "Alice", vendingMachine: vendingMachine)
    print("Success! Yum.")
} catch VendingMachineError.invalidSelection {
    print("Invalid Selection.")
} catch VendingMachineError.outOfStock {
    print("Out of Stock.")
} catch VendingMachineError.insufficientFunds(let coinsNeeded) {
    print("Insufficient funds. Please insert an additional \(coinsNeeded) coins.")
} catch {
    print("Unexpected error: \(error).")
}'

To convert errors to optional values, use the keyword 'try?'. If an error is thrown while evaluating the expression, its return 
is 'nil':
'
    func fetchData() -> Data? {
        if let data = try? fetchDataFromDisk() { return data }
        if let data = try? fetchDataFromServer() { return data }
        return nil
    }
'

If you know a throwing function or method won't throw an error at runtime, you may write the 'try!' keyword before the expression
to disable error propagation. This wraps the call in a runtime assertion, which, if an error does occur, will result in a 
runtime error.
'let photo = try! loadImage(atPath: "./Resources/John Appleseed.jpg")'

To indicate that a method or initializer can throw errors, use the keyword 'throws' after its parameters. This marks the function/
initializer as a throwing function. A throwing function propagates errors that are thrown inside of it to the scope from which it’s
called. 

'
    let favoriteSnacks = [
        "Alice": "Chips",
        "Bob": "Licorice",
        "Eve": "Pretzels",
    ]
    func buyFavoriteSnack(person: String, vendingMachine: VendingMachine) throws {
        let snackName = favoriteSnacks[person] ?? "Candy Bar"
        try vendingMachine.vend(itemNamed: snackName)
    }
'


