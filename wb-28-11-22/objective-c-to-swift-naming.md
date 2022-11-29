# Tuesday 29th November 2022

**Today I Learned**

`Objective-C` code can be used in a `Swift` project and vice versa.  </br>
This is done by using a *bridging header* file. </br>
When you add an Objective-C file to a Swift project, XCode will prompt you to add a bridging header file. </br>

In the header file, you can import any Objective-C header files you want. </br>

For example:
```swift
/* MyProject-bridging-header.h */

#import MyObjectiveCClass.h
#import AnotherClass.h
```

 </br>

 The interop library will also use its word-splitting algorithm to transcribe names from Objective-C to Swift. </br>

 As part of this, function names are built using the named parameters provided. </br>
 For example:

 ```objectivec
+ (instancetype _Nonnull)myClassWithController:(id<Controller>_Nullable)controller;
 ```

 Could become something like this in Swift:
 ```swift
myClass(withController: Controller)
 ```

 ## Ref. Links. Etc.
 [Apple Documentation](https://developer.apple.com/documentation/swift/importing-objective-c-into-swift) </br>
 [Swift Name Transcription Docs](https://github.com/apple/swift/blob/main/docs/CToSwiftNameTranslation.md) </br>
 
