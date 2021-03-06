# Learning Flutter

App Brewery recently provided a free 10-hour course on Flutter: https://medium.com/flutter/learn-flutter-for-free-c9bc3b898c4d

It is easy to follow and very educational. I'll be using this repository to push and post everything I have learned by watching and reading tutorial videos about Flutter.


## A Quick Guide

You can check out the Get Started document here: https://flutter.dev/docs/get-started/install

It might be daunting to start at first because of all the setup and system requirements needed so I have prepared a brief guide on how you can get started:

1. Install flutter SDK:
As long as you follow the steps in the get started docu (link posted above) on how to install flutter and to put in your path, you're good to go. Just make sure that flutter is really added in your path. Check your Mac OS Version if it is using `zsh` or `bash`. If you are still lost at this point, app Brewery's step-by-step guide is also a beginner friendly tutorial on setting up flutter sdk to your path.

2. Install an IDE: I still prefer Android Studio but you can also use IntelliJ or Visual Studio

3. Install XCode: This will require a MacBook and some rules on OS Versioning. If you have enough disk space, just always keep things updated

4. Install CocoaPads by running the ff in your Terminal:
```
 sudo gem install cocoapods
 pod setup
```

## Note

When you create a new flutter app, make sure that your package name is unique

## Running the App

There are several options to run your app

#### Run your app via emulator

If you have Android Studio and XCode installed in your app, they pretty much provide everything including the simulators that you need, just a friendly advice this really requires disk space so make sure that you have enough disk space

#### Run your app on a physical Android device

There is nothing much needed on this except for a good USB cable, it should be able to transfer data and not just for charging. Enable developer mode and USB debugging on your Android phone. There are different ways to do this depending on your phone's model but for most phones, you just need to click the Build Version multiple times in the About page on your phone's settings and you'll see the Developer options from there

#### Run your app on a physical iOS device

You can check the docu on how to run an iOS app here: https://flutter.dev/docs/get-started/install/macos#deploy-to-ios-devices

But here's a quick guide:

1. Obtain an Apple ID

2. Check if iPhone/iPad version is compatible with the XCode Version
```
Given:
device software version = AA.CC
xcode version = BB.DD

It will work only if AA <= BB -2 and CC >= DD
```

3. Attach actual iPhone/iPad device via USB cable

4. Click Runner > Targets: Runner > Signing & Capabilities and add your Apple ID under Account > Team

5. If you get a pop-up dialog from codesign wanting to access your keychain, just enter your mac password and click Always Allow

6. If after following all the steps above and you still can not run the flutter app, go to Device Settings > General > Device Management > Click the developer app you want to run > Click Trust to approve the development certificate

---

## Rules that we should keep in mind when developing

1. As per Flutter team's recommendation, whenever you create a Widget which involves round brackets, add a comma after every one of it

2. To make the code easier to read, always follow the indented structure `dartfmt`. In Android Studio, there is a *Reformat Code with dartfmt* shortcut by right clicking on the class

3. Use `{}` instead of `=>` if method's name and body can't fit into one line

---

## Understanding Stateless vs Stateful Widget

The easiest explanation is that stateless can never change while stateful widgets can. Basically if your page wanted to show an image (See Commit ), then a Stateless widget is a good choice. However, if something is changing like a dice app (See Commit e75a1eacdece3a802ce480fc2a5a1d2c67062c09), then use the StatefulWidget.

There's one more thing you have to know, if you want to rebuild the whole widget you need the `setState(() {})` method.

--

## Functions

Creating a function in Dart is almost similar as other languages. It goes like this:

`void myFunction() { .. }`

and with paramters:

`void myFunction(String param) { .. }`

However, you can also do this in dart:

`void myFunction({String param1, String param2}) { .. }`

and the curly braces make this function interesting. You can call this function in many ways:

1. You can call it as normal: `myFunction('a', 'b')` where 'a' and 'b' are param1 and param2, respectively.

2. You can call it with proper designation: `myFunction(param1: 'a', param2: 'b')` which makes it easier to read.

3. You can also call it like this: `myFunction(param2: 'b', param1: 'a')`, actually. But why? Try not to. :)

4. And lastly, it actually makes the parameters optional. I tried calling it as `myFunction(param1: 'a')` / `myFunction(param2: 'b')` and it still works.

If you do item 4, make sure you handle nullables properly.

## Private methods and data

If you add `_` before its names denotes that the method/data is private.

## Objects

A constructor is needed to create an instance of an object in Dart. You can do it in several ways:

```
class User {
  String name;
  int age;

  User(String name, int age) {
    this.name = name;
    this.age = age;
  }
}

User user = User("Cha", 25);
```

or you can make it optional:

```
class User {
  String name;
  int age;

  User({String name, int age}) {
    this.name = name;
    this.age = age;
  }
}

User user = User(name: "Cha", age: 25);
User user = User(age: 25, name: "Cha");
User user = User(name: "Cha");
User user = User(age: 25);
```

but be careful with optionals, always check out for null.

You can also do this:

```
class User {
  String name;
  int age;

  User({this.name, this.age});
}
```
