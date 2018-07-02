---
title: Objective-C For Swifty People
description: My journey learning Objective-c as a Swift developer.
slug: objective-c
date: 2018-06-17T21:06:06.196Z
tags:
  - ios
image: /images/uploads/objectivec.png
bgOverlayOpacity: '0.25'
comments: 'true'
---

So for those of you who don't know how I got into iOS development, it was not all that long ago when I decided I wanted to switch things up. After about 5 years of writing Javascript for the web, I had an opportunity to jump into the world of iOS, something I had been wanting to try out ever since the original iPhone was announced by Mr. Jobs. When Swift was announced, I was even more anxious as I could learn the language with everyone else and not be years behind all those Objective-c experts. While that was all fine and good, there came a time I started thinking about how much I really ought to learn Objective-C. Sure, I could probably get by knowing just Swift, but there's a world I feel like I'd be missing out on... especially when it comes to understanding iOS engineering at a deeper level. Plus, since I don't come from a CS background, I really don't have all that much experience with C. So, learning this Objective-C is going to be good for me, no matter how painful the syntax is in comparison to my beautiful Swift code! 😭

## What to Expect From This Post

I basically wanted to write about my recent learnings so I have a place to look back on. I likely won't be writing a _ton_ of Objective-C in the near future, so cementing my understanding and having something to reference is key. Additionally, I found there aren't a lot of Objective-C learning resources geared at experienced iOS developers (with Swift knowledge only), probably because there aren't too many, but there is at least one (me 👋), and there are likely others, too. If you're one of those people, hopefully this will help! Also, if you see something in the post that isn't entirely accurate, it means I didn't learn something correctly, and would love for you to correct me in the comments! 🙏

One of the strategies for making sure I hit on everything I learned is by creating my own simple app, a list of US Presidents. Most of what's about to follow is included in that app. Skip down to the bottom of this article for a link.

## The Basics

First, let's start with some of the basic differences between Swift and Objective-C. I've found once I jump that hurdle of the minor syntactical differences, all is once again good in the world.

### Basic Syntax

Ok, so you're probably aware Objective-C loves these 👉 `[]`. Take a minute now to introduce your fingers to these keys that you rarely use anywhere else in life. So let's call some methods in Objective-C and Swift to see the differences.

##### Swift
```
var someClass = SomeClass()
someClass.someStringProperty = "🤺"
someClass.doSomething(with: "🏇")
```

##### Objective-C
```
// note: alternatively can by initialized with [SomeClass new]
SomeClass *someClass = [[SomeClass alloc] init];
someClass.someStringProperty = @"🤺";
[someClass doSomethingWith:@"🏇"]
```

Alright, so there's a few more things going on here beyond the brackets.

* **What's the `@` before quotes?** There is a simple answer for this, it has to do with identifying differences between Objective-C and C/C++ (more information [here](https://stackoverflow.com/questions/25749/what-does-the-symbol-represent-in-objective-c) for those who are curious), but you always use it when defining a string or array literal.
* **Why `alloc` and `init`?** This goes back to initializing classes in C. First the class needs memory allocation, then you call its initializer. The shorthand for this is just calling `new` (more reading on differences [here](https://stackoverflow.com/questions/719877/use-of-alloc-init-instead-of-new)).
* **Semicolons...** Oh, forgot to mention. Use them. You have to. 😕
* **Why an asterisk when defining a property?** This is also around from C. It means we're storing a reference to an object and not the object itself (also known as a pointer). This syntax is used for all non-primitive types, so strings, custom classes, arrays, etc. (e.g. a string would be initialized as `NSString *someString = "hi 👋"`).
* **But... dot syntax for `someStringProperty`? 😫** Yeah, that was confusing for me when first looking at Objective-C. The easy answer is you should use dot syntax when getting or setting a property on an instance of a class. It _actually_ has to do with using a property accessor vs an instance variable, details on that below in the classes section.

### Classes

#### Header files

One of the biggest differences between Swift and Objective-C, and likely one you've already seen if you've seen any Objective-C code, is multiple files for each class, a header file (.h) and an implementation file (.m). As much as I prefer Swift in almost every way, header files are one thing in Objective-C that I find to be quite nice. It gives you an easy way to see all public methods at a quick glance. It also removes some of the keyword confusing (e.g. `private`, `fileprivate`, ... 😵). So how do they work? Let's take a look at a simple class in both Objective-C and Swift.

##### Swift (Car.swift)
```
class Car {
    let numberOfWheels = 4
    var color: String?

    func changeColor(to color: String) {
        self.color = color
    }
}

```

##### Objective-C (DSCar.h)
```
@interface DSCar : NSObject

@property NSString *color;

- (void)changeColorTo:(NSString *)color;

@end

```

##### Objective-C (DSCar.m)
```

@interface DSCar ()

@property int numberOfWheels;

@end

@implementation DSCar

- (instancetype)init {
    // Don't worry about this syntax, it's just the standard way to setup initializers.
    // We're just setting a default value for `numberOfWheels`, which needs to be done
    // in an initializer.
    if (self = [super init]) {
        self.numberOfWheels = 4;
    }

    return self;
}

- (void)changeColorTo:(NSString *)color {
    self.color = color;
}

@end

```

Few things to note about all of this:

* **`DSCar` vs `Car`... huh?** Objective-C doesn't allow namespacing so it's good practice to namespace your classes to avoid collisions. This is why you have things like `NSNotificationCenter` and `UIButton`. 😃
* **What's private and what's not? 😵** At first glance it may seem a bit confusing with `@interface`s and `@implementation`s scattered all over the place (at least it did for me). We'll talk about those keywords a bit later, but for now the easiest way to know what's public is _only_ what's defined in the header file. So, this class only allows you to see its `color` property and `changeColorTo(_:)` method. See the categories section further down for details on how `numberOfWheels` is private (via a class extension).
* **Why is there an initializer in the Objective-C version?** This is necessary to set the default value for `numberOfWheels`. Don't worry too much about the weird syntax around it, this is generally how all initializers look in Objective-C. If you're curious as to why, read [this](https://stackoverflow.com/questions/2956943/why-should-i-call-self-super-init).

So much more code to define a simple class! I know. 😔

#### Methods

The syntax for methods is a bit tricky and took me a bit to get used to. No, I lie, I'm still not used to it. Let me try to break it down a bit. Let's look at a simple method in both Swift and Objective-C.

##### Swift
```
func doSomethingCool(with thisThing: String, numberOfTimes: Int) -> Bool {
    return true;
}
```

##### Objective-C
```
- (bool)doSomethingCoolWith:(NSString *)thisThing
              numberOfTimes:(int)numberOfTimes {
    return YES;
}
```

First, the `-` identifier. This just means we have an instance method. For class methods, it changes to a `+`. Next, the method name itself includes the name of the first parameter. All other parameters follow (usually on newlines, auto indentation will take care of this for you) with the internal and external parameter names. The return type is at the beginning of the method. If there isn't a return, this becomes `void`. Calling this method would then look something like...

##### Swift
```
something.doSomething(with: "SomeString", numberOfTimes: 5)
```

##### Objective-C
```
[something doSomethingCoolWith:"SomeString" numberOfTimes:5];
```

<p></p>
#### Compiler Directives

 Compiler directives are all the keywords with an `@` at the beginning. This one threw me for a bit of a loop when first looking at Objective-C code. Why does `@interface` go in both the header and implementation file? Why are there no curly braces and what's with `@end`? 😵 (hmm... lots of dizzy faces in this post... 🤔). So here's a list of them all and what they do.

* `@interface`...`@end`: This is what surrounds the properties and methods you define in your header (.h) file. It can also be used for categories (Swift extensions, see below) or class extensions (also more below under categories section), which is the only time you'll see it in an implementation (.m) file.
* `@implementation`...`@end`: This is what surrounds most of your code in your implementation file, which the only exception being `@interface` mentioned above. This is basically what you would put in your swift file when defining a class.
* `@property`: Instructs the compiler to write accessor methods (get and set) for a property. More about this under the property accessors section below, but just know this is how you define properties. Public properties are defined in the header file, and private properties in the implementation file (using `@interface`...`@end`). One important part of Objective-C syntax with property definitions are a list of parenthetical options which instruct the compiler how to auto-generate these accessor methods. You have probably seen this, it looks something like `@property (readonly nonatomic weak)`. Here are some examples:
    * `readonly`/`rewrite` (default: `rewrite`): Use a getter, no setter.
    * `nonatomic`/`atomic` (default: `atomic`): Nonatomic removes lock which prevents access from multiple threads. Should always be removed because of cost and checked at a higher level in program.
    * `weak`/`strong` (default: `strong`): Adds weak reference.
    * `copy`/`assign` (default: `assign`): Used to prevent mutating a value (e.g. `NSMutableString` passed as an immutable `NSString`). Good habit to use when mutable subclass exists.
* `@synthesize`: Tells the compiler that an instance variable is backing an accessor (e.g. `_numberOfWheels` backs `numberOfWheels`).
* `@class`: Tells the complier there’s a class, used as a promise in the header file. Can also be used for compiler efficiency so header file does not need to be recompiled when dependent class is modified. Note: Class still needs to imported in the implementation file.

Check out [this NSHipster post](https://nshipster.com/at-compiler-directives/) for even more on compiler directives.

#### Inheritance and Protocols

Inheritance and conforming to protocols are pretty straightforward and similar to Swift. Conforming to a protocol is maybe even a bit more clear in Objective-C than it is in Swift. Here's an example of a protocol and conforming class in Swift and Objective-C.

##### Swift
```
protocol SomeProtocol {
    func someMethod(with someParameter: String)
}

class SomeClass: BaseClass, SomeProtocol {
    ...
}
```

##### Objective-C (.h)
```
@protocol SomeProtocol

- (void)someMethodWithSomeParameter:(NSString *)someParameter;

@end

@interface SomeClass : BaseClass <SomeProtocol>

...

@end
```

<p></p>
#### Property Accessors/Instance Variables

As we discussed before (under Compiler Directives), `@property` gives us property accessors for instance variables. Instance variables is where the value/reference is _actually_ being stored and `@property` just gives us setters and getters. We could instead write these methods ourselves, which would look something like this:

```
- (void)setNumberOfWheels:(int)numberOfWheels {
    _numberOfWheels = numberOfWheels;
}

- (int)numberOfWheels {
    return _numberOfWheels;
}
```

### Categories

Categories are pretty much the same as extensions in Swift, it's basically just a difference in syntax.

##### Swift
```
extension Array {
    func someNewArrayMethod {
        ...
    }
}
```

##### Objective-C
```
@interface NSArray (SomeCategoryName)

- (void)someNewArrayMethod;

@end
```

Class extensions (generated by Xcode with all new view controllers) are categories used to define private properties in your implementation file. This is often use for private view properties.

```
@interface ViewController ()

@property UITableView *tableView;
@property NSArray<DataType *> *data;

@end
```

### Blocks

Last but not least, blocks. These are pretty much the exact same as closures in Swift, but with much weirder and confusing syntax (cue dizzy face: 😵). The best way to keep track of this is probably not memorization and instead bookmarking this website: [http://fuckingblocksyntax.com](fuckingblocksyntax.com). Let's look at an example:

##### Swift
```
let someClosure = { (param1, param2) in
    ...
}

someClosure("hello", "world")
```

##### Objective-C
```
void (^someBlock)(NSString *, NSString *) = ^void(NSString *param1, NSString *param2) {
    ...
};

someBlock(@"hello", @"world");
```

At least with blocks, the syntax is pretty much the same once you get around the weird `^`s all over the place. Honestly, Swift's closure syntax isn't all that intuitive either, though... 😕

Last few things to note about blocks:

* Use `typedef` (like `typealias`) to name blocks and make them less confusing to the reader.
* Variables captured by a block are constant within the block, using `__block` keyword when declaring the external variable (yeah, annoying 😡).
* Like in Swift, use weak references to prevent strong reference cycles. This is done using the `__weak` keyword prior to the block definition (looks something like: `__weak UIViewController *weakSelf = self`).

## Swift/Objective-C Interoperability

There's quite a bit to talk about here, especially when talking about how to write Swift code compatible for Objective-C. Maybe I'll follow-up with another post specific to this topic. For now, though, one thing I want to mention when writing Objective-C code to be used in Swift. Remember the list of options used when defining a property? Well here's a new one to account for Swift's optionals: `nullable`/`nonnull`.
    * Property annotation used to indicate whether property should be an optional in Swift.
    * Use `NS_ASSUME_NONNULL_BEGIN/END` to wrap a bunch of properties as `nonnull` at a time (reverse not possible).

## Example Project

I tried to create an [extremely simple Objective-C project](https://github.com/help-debug-examples/presidents) to help understand the concepts when starting a new project from scratch. All it does is reads a JSON file of US presidents and displays them in a table view. Take a look and play around with it to help better your understanding of some of these concepts.

_Most of this knowledge was gained from an exceptional Big Nerd Ranch training I received recently from Mikey Ward ([@wookiee](https://twitter.com/wookiee)). Thank you!_
