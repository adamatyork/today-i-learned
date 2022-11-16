# Wednesday 16th November 2022

**Today I Learned**
<br>

`Guard` clauses are useful in Swift for soft unwrapping Optionals *but* what happens if you want to call a function in your guard clause, and that function takes a trailing closure parameter? <br><br>

Take the function `.first` on an Array, which returns the first instance in the Array that matches some given conditions. <br>
`.first` takes a trailing closure parameter called `where:` that allows you to specify the comparison logic. 
<br>

For example: <br>
```swift
let users = [
    "Adam",
    "Joe"
]

var match = users.first { user in 
    user == "Joe"
}
```
<br> 

This pointless example just finds Joe and returns it. <br>
But the return type of `.first` here is `Optional<String>` because we can't guarantee a match will be found. <br>
So we should safely unwrap `match` by using a `guard`.

<br>

```swift 
guard let match = users.first { user in 
    user == "Joe"
} else { return }
```
<br>

Uh-oh, XCode isn't happy with me.

<br>

`Expected 'else' after 'guard' condition.`<br>
`Expected expression` 

<br>

It's because I used a trailing closure. <br>
If we want XCode to be be happy, we need to pass in the closure as we would a regular parameter.

<br>

```swift
guard let match = users.first(where: { user in
    user == "Joe" 
}) else { return }
```

<br>
That's sorted it right out!
<br>

----
<br>
Not only is XCode happy with this, but it's actually smart enough to suggest it to you. 

<br>

If you go to write a statement like `guard let match = users.fir` , autocomplete will suggest `.first` in the above syntax, and hitting enter will create it correctly for you. <br>
If you use `.first` outwith a guard clause, autocomplete will write the trailing closure syntax for you by default. 

<br> <br>

## Ref. Links. Etc.
[StackOverflow](https://stackoverflow.com/questions/65933463/guard-with-trailing-closure-swift-syntax) <br>
[Array.first](https://developer.apple.com/documentation/swift/array/first(where:)) <br>
[GuardStatements](https://www.programiz.com/swift-programming/guard-statement)
