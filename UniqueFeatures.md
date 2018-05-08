# Unique Features

## Java

What truly sets Java apart from the other languages out there is its platform independence. Whenever, a program is written in JAVA, the Java compiler compiles it.
The Java compiler results noti n native machine code, but a .class file or the bytecode. The bytecode created is not executable by the machine and must executed by the JVM.  This is possible because the JVM depends on the host OS. When trying to download Java, you must navigate a list of JVM’s corresponding to various OS's. So we can conclude that JVM is platform dependent and it is the reason why Java is able to become “Platform Independent”

## Swift

The most unique feature available in the Swift language is the *optional* type. Unlike Java regular types in Swift are **NOT** allowed to be set to nil (null in Java). Instead Swift has what are called optionals, which can be thought of as a box that that contains one of two things; a value of a specific type, or nil. Optional types must be 'unwrapped' to access this value before using them. An example of swift optionals is shown below.

```

var university: String?
var ID: Int? = 5

if let school = university {
print(school)
}

if let id = ID {
print(id)
}

```

In this example both university and ID are optionals. university is not given an initial value but ID is, therefore university will be set to nil. When attempting to print the variables, we must first unwrap the optional into a temporary variable that will be of the same type as what the optional contained.

[Back to Main](README.md/#UniqueFeatures.md)


