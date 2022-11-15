# Wednesday 9th November 2022

**Today I Learned**
<br>

A `Task` in Swift can be given a priority. <br>
There are 6 priorities available. These are: <br>
<br>
1) High = 25
2) UserInitiated = 25
3) Medium = 21
4) Low = 17
5) Utility = 17
6) Background = 9
<br>

You can assign a priority to a Task like so. <br>
```Swift
Task(priority: .high) {
    // Do something
    ...
}
```

<br>

Tasks with higher priority are not guaranteed to finish first. <br>
Priority dictates what order Tasks will be initiated. <br>
If a `.high` priority task makes an API call that takes 4 seconds, and a `.low` priority Task takes 2 seconds, the `.low` priority Task will still finish first. <br>

You can see a Task's priority by using `Task.currentPriority`. <br>
Tasks within a Task will inherit the parent's priority. <br>

```swift
Task(priority: .utility) {

    print(Task.currentPriority)
    ...

    Task {
        print(Task.currentPriority)
        ...
    }
}
```

Both Tasks will print out a priority of 17.
<br><br>

## Ref. Links. Etc.
[PlaygroundDemo](https://github.com/adamatyork/swift-learning/blob/main/Playgrounds/Concurrency/Tasks/TasksDemo/TaskBootcamp.swift) <br>
[TutorialVideo](https://www.youtube.com/watch?v=fTtaEYo14jI) <br>
[SwiftDocs](https://developer.apple.com/documentation/swift/taskpriority) <br>
