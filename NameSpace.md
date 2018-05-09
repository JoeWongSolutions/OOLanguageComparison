[Back to Main](README.md/#name-spaces)
# Namespaces

## Java
In Java, packages group related classes together and define a namespace for those classes. Every class has a simple name, and a fully qualified name. The simple name is the name provided in its definition, the fully qualified name also includes the name of the package that it is in. For example, the String class, is part of the java.lang package, so java.lang.String is its fully qualified name. Sun suggests a package-naming scheme where the prefix for all your package names is your reversed Internet domain name. For example my web site is adamoaked.com, so all my Java packages begin with com.adamoakes


## Swift
Swift’s namespace concept is based on modules. A module is a single unit of code distribution; an application or framework built and shipped as a single unit and may be imported by other modules. With Swift, each build target (such as a framework or app bundle) in Xcode is treated as a distinct module. With Swift namespacing is implicit, all classes (etc) are implicitly scoped by the module (XCode target) they are in. no class prefixes are needed. All Swift declarations are considered to be part of some module.


[Back to Main](README.md/#name-spaces)





