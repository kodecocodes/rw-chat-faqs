# iOS

## Learning Paths

**Question** I'm new to iOS development. Where should I start?

**Answer** You can start with [iOS and SwiftUI for Beginners](https://www.raywenderlich.com/ios/paths/learn) learning path.

**Question** Is there a learning path for unit testing?

**Answer** subscribers to raywenderlich Pro have access to a full video course on testing: [Testing in iOS](https://www.raywenderlich.com/8458722-testing-in-ios) [Discord Link](https://discord.com/channels/512920737028374529/703294846596808738/844583068878897172)

**Question** I am new to iOS programming and for the current time I want to only focus on UIKit and not SwiftUI.

I am following the learning path but can I skip all the swift UI tutorials and just follow the UIKit ones.

Or will it be a problem?

**Answer** I’d still suggest going through the SwiftUI part since that’d be useful knowledge. Most of tutorials and samples are going to be SwiftUI everywhere so even if you want to learn about a new API in a framework, the app is written in SwiftUI. [Discord Link](https://discord.com/channels/512920737028374529/703294846596808738/786676529031020584)

**Question** I don't know how threads and dispatch queue work exactly in iOS. can I straight away jump in to understanding it through the videos provided in the learning path, what are the prerequisites.

**Answer** Start with the 2 part tutorial: [Grand Central Dispatch Tutorial for Swift 4: Part 1/2](https://www.raywenderlich.com/5370-grand-central-dispatch-tutorial-for-swift-4-part-1-2) [Discrod Link](https://discord.com/channels/512920737028374529/703294846596808738/786300020021919756)

**Question** Could I skip the UIKit thing on the learning path?

**Asnwer** You can if you're going to work on SwiftUI only app. However, learning UIKit basics and having general idea about it helps to understand the SDK better. At some point, you may need to drop down to UIKit to supplement some SwiftUI stuff. [Discrod Link](https://discord.com/channels/512920737028374529/703294846596808738/780866083845439509)

## Swift / Objective-C

**Question** Whats an `autorelease` pool?

**Answer** Objective-C objects (and things like Swift class instances) use automatic reference counting (ARC) as a memory management strategy. While your program is running, ARC keeps track of the number of references each object has. If nobody has a reference to an object, it's reference count goes to 0, and the object is deallocated.

`autorelease` pool are a feature of the Objective-C runtime which lets you manually influence when and how ARC deallocates an object. In Objc this is useful in cases where you instantiate heavy objects inside a for loop. You can force objc to deallocate an object at the end of each iteration by adding the object to an `autorelease` pool, which deallocates all objects when it exits
all that aside, basically in Swift you don't need autorelease pools, unless
(1) you're working with Objc objects and
(2) you notice issues where your peak memory consumption is too high.
[Discord Link](https://discord.com/channels/512920737028374529/703294846596808738/818016935680802816)

**Question** Class vs. struct in Swift.

**Answer** You'd probably interested in [Protocol-Oriented Programming in Swift](https://developer.apple.com/videos/play/wwdc2015/408/) and regarding class vs. struct, Swift uses ARC which is automatic reference counting compare to JS (which I believe it uses garbage collector). The difference is structs are value based which are stored in stack portion of the memory and when passed around are copied entirely which is kinda a cheap operation and helps with multithreading when used properly. On the other hand, classes are reference types which means when you pass a class to a method, that method gets a reference to the memory that class is stored and can change the content of that class. Also, ARC itself has some overhead since it adds checks for increase and decrease ref count to each class memory. [Discord Link](https://discord.com/channels/512920737028374529/703294846596808738/783699094182559815)

**Question** How to debug memory leaks and cycle dependencies?

**Answer** you may find these guides helpful for debugging & memory: [ARC and Memory Management in Swift](https://www.raywenderlich.com/966538-arc-and-memory-management-in-swift#toc-anchor-021),
[Debugging in Xcode 11](https://developer.apple.com/videos/play/wwdc2019/412/), [Gathering Information About Memory Use](https://developer.apple.com/documentation/xcode/improving_your_app_s_performance/reducing_your_app_s_memory_use/gathering_information_about_memory_use) [Discord Link](https://discord.com/channels/512920737028374529/703294846596808738/712001013673885840)

## SwiftUI

**Question** I am very curious to start learning SwiftUI, but I would like to do learn the "reactive" app architecture. So I'm not looking for just how to do certain UIs with SwiftUI, but also how to architect an app as well. Are there any references you recommend? Is the SwiftUI apprentice a good book for this, or is there another resource you recommend?
I guess it's also learning Combine

**Answer** Those are different topics, especially app architecture and SwiftUI / Combine. Let me try to break it:

- Combine is Apple's framework for solving reactive programming and make it easier for developers to use first party framework. This also helped with adding the support to existing classes and adopt this new approach of streaming data
- SwiftUI is a new framework from Apple aiming to help with solving issues with UIKit and making it easier to write applications. It's using MVVM pattern to handle updating UIs and underneath is taking advantage of Combine framework to achieve this goal.
- App architecture is kinda independent of the technology that you use. In iOS world, there are several common architectures that you can use, MVC, MVVM, VIPER, RIBS, MVVMC, and coordinator pattern with MVC. You can use reactive pattern to implement these architectures in different layers. It's good to know different architecture patterns and use them according to the scale of your project.
  Hence, I doubt there'd be a book to cover all of these topics. Usually books try to narrow down to a specific audience. So a book about teaching SwiftUI, tries to keep the architecture and usage of Combine simple and focus more on SwiftUI features and advance features there. Similar for the other books. Following books are good reads for learning these topics:

- Combine: [Combine: Asynchronous Programming with Swift](https://www.raywenderlich.com/books/combine-asynchronous-programming-with-swift/v2.0)
- SwiftUI: [SwiftUI by Tutorials](https://www.raywenderlich.com/books/swiftui-by-tutorials/v3.0), [Thinking in SwiftUI](https://www.objc.io/books/thinking-in-swiftui/)
- App Architecture: [Advanced iOS App Architecture](https://www.raywenderlich.com/books/advanced-ios-app-architecture/v3.0), [objc App Architecture](https://www.objc.io/books/app-architecture/) [Discord Link](https://discord.com/channels/512920737028374529/789937281401487370/832666993014341673)

## UIKit

## Architecture

- **Question** does anyone know a good book/article about best practices for create a scalable and easy to maintain iOS project?
I'm looking for something more in the project management side to deal with things like release cycle, code review, QA and automated tests, etc

**Answer** when it comes to development best practices, there are many ways to do it - and all are correct. In general, I would recommend you look at Clean Arquitectore for a general purpose way of project managing a product, starting from scratch is a huge plus. When you inherit a project, the task is not as straight forward. Especifically for iOS, I recommend you take a look at the Composable Arquitecture, this will help you build and maintain a project for the long run: [Composable Architecture](https://www.pointfree.co/collections/composable-architecture)

as for the process of automating builds, deployment etc. There are also many solutions out there that are all good - everyone has a favorite. A tried and tested solution is Fastlane, this is based on Ruby scripts (easy to understand and customize). It helps automate from development to code sign and release at the AppStore. [fastlane](https://fastlane.tools/), [Fastlane Tutorial Getting Started](https://www.raywenderlich.com/778-fastlane-tutorial-getting-started), and full video course [Fastlane for iOS](https://www.raywenderlich.com/1259223-fastlane-for-ios)

[Discord Link](https://discord.com/channels/512920737028374529/703294846596808738/857657619463405588)
