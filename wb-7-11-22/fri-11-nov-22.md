# Friday 11th November 2022

**Today I Learned**
<br>

`Delegates` are used in Swift to communicate between classes on a 1-1 basis. <br>
A delegate is simply a `Protocol`, implemented by a class, often a ViewController. <br>
<br>

**Test It Out** <br>

Define a delegate protocol with a method to handle a button click. <br>

```swift
protocol ButtonClickDelegate {
    func clickHandler(message: String) -> Void
}
```


We also create a view controller with a property of type `ButtonClickDelegate`. <br>
This view controller will contain the button to be clicked. <br>
`IBAction func...` defines a function that runs when the button in this view is tapped. <br>
This function calls the `clickHandler` method of our delegate. <br>
It doesn't know what our delegate is, or what the clickHandler method will do. It just knows it accepts a `String` parameter and returns `Void`

```swift
class PageWithButtonViewController: UIViewController {
    public var clickDelegate: ButtonClickDelegate!

    @IBAction func buttonWasClicked(_ sender: UIButton) {
        clickDelegate.clickHandler(message: "YOU CLICKED IT OMG")
    }

    ...
}
```

Now we can define another ViewController that will contain a text label. <br>
When the button in PageWithButtonViewController is tapped, this label will be given a value. <br>
In `init`, we need to assign ourself to be the value of the delegate property in PageWithButtonViewController. <br>
*"I see you have a delegate property. I conform to the delegate protocol, use me as your delegate!"*

```swift
class ViewController: UIViewController {
    @IBOutlet weak var myTextLabel: UILabel!

    init() {
        PageWithButtonViewController.clickDelegate = self
    }
    ...
}
```

We can then extend our ViewController to conform to the ButtonClickDelegate protocol. <br>
This could be done in the original class definition but it's nice to split extensions out. <br>
Implement the `clickHandler` function, and in it, set the label's value to the message received from PageWithButtonViewController. <br>

```swift
extension ViewController: ButtonClickDelegate {
    public func clickHandler(message: String) {
        self.myTextLabel.text = message
    }
}
```

<br>

## Ref. Links. Etc.
[StackOverflow Question](https://stackoverflow.com/questions/24099230/delegates-in-swift) <br>
[Useful Video on Delegates](https://www.youtube.com/watch?v=DBWu6TnhLeY) <br>
[More Detailed Article](https://www.advancedswift.com/how-to-create-a-custom-delegate-in-swift/)