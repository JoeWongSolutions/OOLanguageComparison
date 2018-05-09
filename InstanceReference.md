[Back to Main](README.md/#classes)
# Instance Reference Name

## Java

In Java the instance is referred to in its self as **this**. Reference to instance fields can be achieved using the this keyword followed by the field name. This is especially useful when variables inside of some sub-scope to the class have the same name as the instance variables. This often occurs in the object's constructor. Below is an example of the this keyword being used.

```
public class Puppy {
    public String name;
    public Int age;
    public String breed;

    public Puppy(String name, Int age, String Breed) {
        this.name = name;
        this.age = age;
    }
}
```

## Swift

In Swift the instance is referred to in its self as **self**. Reference to instance properties can be achieved using the self keyword followed by the field name. Below is an example of the self keyword being used.

```
class GameScene: SKScene {
    var selectedBlock: Block?
    
    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        if let touch = touches.first {
            let positionInScene = touch.location(in: self)
            
            if let block = level.block(atPosition: positionInScene){
                selectedBlock = block
            } 
        }
    }
}

```

[Back to Main](README.md/#classes)
