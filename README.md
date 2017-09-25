SwiftTryCatch
=============

Adds try/catch for Objective C exceptions in Swift 2.x as a Carthage module. It is a simple wrapper built around Objective-C `@try`/`@catch`/`@finally`.

*Why is this needed?* 

TL;DR: If, like Egghead Games, you like your app to never crash, even for rare events like "out of disk space", you need to add this in critical places in your Swift code (e.g. disk & network access, Obj-C calls like the NSJSON apis).

If you call Objective-C functions from Swift code, e.g. NSJSONSerialization, and that code has an error, then you _cannot_ catch that error using the new Swift 2.x Try/Catch statements. This is counter-intuitive, but look at Stack Overflow for many supporting examples and the fine print. You might also hit this with low-likelihood events like "out of disk space". Include this tiny wrapper library and you'll be good to go. (Be sure to write tests to prove this, we did!)

_Forked from https://github.com/ravero/SwiftTryCatch and updated to work with Carthage (from CocoaPods). That version was a Swift 2.0 updated version of the original https://github.com/williamFalcon/SwiftTryCatch._

## Usage

### Install via Carthage

Add this repo to your Cartfile per usual and `carthage update` drag to include, etc.
(see https://github.com/Carthage/Carthage).

### Use

    SwiftTryCatch.tryBlock({
             // try something
         }, catchBlock: { (error) in
             println("\(error.description)")
         }, finallyBlock: {
             // close resources
    })

