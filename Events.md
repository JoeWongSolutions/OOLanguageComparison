[Back to Main](README.md/#implementation-of-listeners-and-event-handlers)
# Events in Java and Swift
Both Java and Swift support the notion of event listeners and event handlers. This comes as no surprise since both languages are developed with graphical user interfaces in mind. We will focus on creating custom event listeners in this section and the difference betweeen the two languages.
### Event Listener in Java
In Java, event listeners must implement a Listener interface. Take for example the popular ActionListener interface which is an interface with a single method called actionPerformed(). We can override this method to tell our Listener what to do when the action is performed. See the code below:
```Java
class Eavesdropper implements ActionListener {
    ...
    public void actionPerformed(ActionEvent e) {
        myTextArea.append(e.getActionCommand() + newline);
    }
}
```
As we can see from the example, actionPerformed takes one parameter, an ActionEvent. Every event-listener method must take a parameter that inherits from EventObject. Objects such as buttons have methods to add event listeners and will fire an event when appropriate thereby calling the respective listeners to do some actions.
### Event Listener in Swift
Events in Swift can get a bit complicated so in order to reduce the complexity of this subject, we will ignore aspects that are beyond the scope of events and just look at the basics.
```Swift
// Code credit goes to blog.scottlogic.com
class Event<T> {

  typealias EventHandler = T -> ()

  private var eventHandlers = [EventHandler]()

  func addHandler(handler: EventHandler) {
    eventHandlers.append(handler)
  }

  func raise(data: T) {
    for handler in eventHandlers {
      handler(data)
    }
  }
}
```
Note that we use the typealias to define a function that will accept the same type as the generic found in Event. An array of event handlers is held in a var called eventHandlers and we define a method called addHandler to add event handlers to our array. The raise function will call each handler's handler() method and pass in the data. Finally we can use closures to handle the events being raised.
```Swift
let event = Event<Void>()
event.addHandler { println("Hello") }
event.addHandler { println("World") }
event.raise()
```

[Back to Main](README.md/#implementation-of-listeners-and-event-handlers)
