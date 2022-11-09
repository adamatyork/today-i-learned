# Wednesday 9th November 2022
## Today I Learned
<br>

`Self` in Swift refers to the `Type` itself. <br>
It can be used to refer to static properties of the type. <br>
```
struct MyType {
    static let myProp: String = "MyStaticProp"

    ...
    var myProp = Self.myProp
}
```
If a type conforms to a `Protocol`, the protocol could use `Self` in its code to refer to the `Type` that is implementing the protocol at runtime.

---

`self` in Swift refers to the instance of the given type. <br>
It is used to access instance properties and methods. <br>
```
struct MyType {

    var myProp: String = "MyInstanceProp"

    ...
    var myProp = self.myProp
    self.myProp = "NewPropValue"
}
```

<br>

## Ref. Links. Etc.

[Swift Documentation]("https://docs.swift.org/swift-book/ReferenceManual/Declarations.html#//apple_ref/doc/uid/TP40014097-CH34-XID_543") <br>
[Hacking With Swift Article]("https://www.hackingwithswift.com/example-code/language/self-vs-self-whats-the-difference") <br>
[Stack Overflow Question]("https://stackoverflow.com/questions/27863810/distinction-in-swift-between-uppercase-self-and-lowercase-self")

