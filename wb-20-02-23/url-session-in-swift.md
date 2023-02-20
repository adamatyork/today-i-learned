# Monday 20th February 2023

**Today I Learned**

Swift provides a simple API for making basic web requests, called `URLSession`. </br>

URLSession offers a singleton called `shared` which offers basic configuration for simple web requests that don't need any custom caching or config. </br>
</br>

```swift
let task = URLSession.shared.dataTask(with: url) { data, response, error in
    if let data = data {
        print("Success! Data: \(data)")
    } else if let error = error {
        print("Failed \(error)")
    }
}

task.resume()
```

### URLSessionConfiguration
For more complex requests, you can instantiate a new URLSession object and pass in one of three types of `URLSessionConfiguration`.

- `default` which provides the same fucntionality as `shared` but offers more configuration. It stores credentials in the user's keychain on disk. </br>
- `ephemeral` which provides the same functionality as `shared`, however things like caches, cookies and credentials are not written to disk. They are instead written to RAM! </br>
- `background` which makes requests in the background, even when the app is not running. Requests are handled by the system in a separate process, anmd can be assigned an identifier to handle termination mid request. </br>

</br>

### URLSessionDelegate
URLSession also takes a `delegate` (unless you're using `.shared`) which defines how the session handles events during the request and session life cycle. </br>
You can create your own delegate class that inherits `URLSessionDelegate` and override the base functions. </br>
You can also inherit `URLSessionDataDelegate`, `URLSessionTaskDelegate` and `URLSessionDownloadDelegate` if you want to customise task level events like incrmental downloads or uploads and caching.

</br>






## Ref. Links. Etc.
[URLSession Apple Docs](https://developer.apple.com/documentation/foundation/urlsession) <br>
[URLSessionDelegate Apple Docs](https://developer.apple.com/documentation/foundation/urlsessiondelegate) <br>
[Making HTTP Requests](https://cocoacasts.com/networking-fundamentals-how-to-make-an-http-request-in-swift)
