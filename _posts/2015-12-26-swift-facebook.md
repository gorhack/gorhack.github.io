---
layout: post
title: "Getting Started: Swift 2 and Facebook SDK 4.8.0"
author: "Kyle Gorak"
date: "2015/12/26"
output:
  html_document:
    keep_md: true
comments: True
tags: [Facebook, api, Swift, Xcode, programming]
---

I was starting a new Swift 2 project and saw the Facebook developer portal did not cover Swift. I figured I would take it upon myself to fill in some of the missing pieces of the tutorial found on [developer.facebook.com](https://developers.facebook.com/quickstarts/?platform=ios). Repository with project on [Github](https://github.com/gorhack/fblogin_swift2).

#### Importing the FB SDK Frameworks into the project:

Download the [Facebook SDK](https://origincache.facebook.com/developers/resources/?id=facebook-ios-sdk-current.zip) add the Framework files to your project. You will need to  select "Copy items if needed" when adding the files to your project.
![Add files to project]({{ site.url }}/assets/images/add_files.png){: .center-image}

#### Configure your .plist

Add the following to `info.plist` (right click, Open As > Source Code):
{% gist gorhack/7d8ff0c39903dd6f750e info.plist %}

#### Add Facebook login to your App Delegate

In your `AppDelegate.swift` import `FBSDKShareKit` and add a new application function.
{% gist gorhack/7d8ff0c39903dd6f750e AppDelegate.swift %}

#### Add login button to your View Controller

In one of your `ViewController.swift` files import `FBSDKLoginKit` and add the login button to the `viewDidLoad()` function.
{% gist gorhack/7d8ff0c39903dd6f750e ViewController.swift %}

#### Test your program

Run your application on the emulator or on a device and you should see a Facebook login button that will direct you to login. Logging in will store your application in your Facebook account's Apps section as an authorized application. Inside the Swift application you now have a logout button instead of a login button.
![Add files to project]({{ site.url }}/assets/images/facebook-test.png){: .center-image}
