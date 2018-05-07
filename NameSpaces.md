# Name Spaces

## Java

Namespaces are named program regions used to limit the scope of variables inside the program. They are used to create a separate region for a group of variables, functions, classes, etc.

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

[Back to Main](README.md/#properties)
