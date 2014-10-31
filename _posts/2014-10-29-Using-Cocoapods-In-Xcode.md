---
layout: post
categories: [xcode, pods]
title: Using CocoaPods in Xcode
keywords: xcode, cocoapods, ios, pods
summary: Quick guide for using cocoapods to automate importing/updating dependencies in your xcode projects.
author: girishvr
---



##[CocoaPods](http://cocoapods.org/)

### Introduction
CocoaPods is the dependency manager for Objective-C projects. It has thousands of libraries and can help us scale our projects elegantly.

### Prerequisites
CocoaPods is built with **Ruby** and is installable with the default Ruby available on OS X. 

*Please Install Ruby in your system if you do not have it.*

Fortunately, all recent versions of Mac OS X (since OS X 10.7 Lion) ship with Ruby already installed. So all you need to do is update RubyGems (just to make sure you have a recent version).

 - To do so, open Terminal and type the following command:

    `$ sudo gem update --system`

*Enter your password when requested.*

-----
### Installation

1. Using the default Ruby install will require you to use sudo when installing **gems**. 

     `$ sudo gem install cocoapods`

2. Lastly, enter this command in Terminal to complete the setup of CocoaPods:

     `$ pod setup`

   *This process will likely take a while as this command clones the CocoaPods Specs repository into ~/.cocoapods/ on your computer.*



### Initializing Pod into the App

- Navigate to the directory containing your app project by using the cd command:

    `$ cd ~/Path/To/Folder/Containing/AppName`


- CocoaPods provides a `pod init` command to create a Podfile with smart defaults. You should use it.
To do so, enter this command:

    `$ pod init`

   *This will create a default Podfile for your project. The Podfile is where you define the dependencies your project relies on.*



### Installing Your Dependency

* Type this command to open **Podfile** using Xcode for editing:

    `$ open -a Xcode Podfile`

   **Warning:** *You shouldn’t use TextEdit to edit the pod file because TextEdit likes to replace standard quotes with more graphically appealing quotes. This can cause CocoaPods to get confused and display errors, so it’s best to just use Xcode or another programming text editor.*



* Now, list the dependencies in a text file named **Podfile** in your Xcode project directory:


  
        source 'https://github.com/CocoaPods/Specs.git' 
        platform :ios, '8.0'

        pod 'AFNetworking', '~> 2.4.1'
        pod 'ARAnalytics', '~> 2.7' 


  This tells CocoaPods that your project is targeting iOS 8.
Also, you want to include AFNetworking version 2.4.1 (the latest as of the writing of this tutorial) and ARAnalytics version 2.7 as a dependency for your project

   ***Save and close the Podfile.***

   **NOTE:** You can [search for pods](#search-for-pods) also if you wish.



### Finishing

   You now need to tell CocoaPods to “install” the dependencies for your project. 

- Enter the following command in Terminal:

   `$ pod install`

   *Make sure that you’re still in the directory containing the app project and Podfile.*

- Open the app project
 
 
   `$ open App.xcworkspace`
   
  *Make sure to always open the Xcode workspace instead of the project file when building your project*


- Now you can import and use the dependencies e.g.:
  
        #import <Reachability/Reachability.h>
    
**Thats all!**

----


### Search for pods
You can search for all the available pod files also.

- To search for pods by name:

    `$ pod search QUERY`

- To search for pods in the name, the description and any other relevant metadata you can use:

    `$ pod search --full QUERY`

- Finally, to dump the full list of the pods installed in your system you can do:

    `$ pod list`


------

### What next?
##### Create a Pod

 Sometimes CocoaPods doesn’t yet have a pod for one of your dependencies. Fortunately, creating a pod is pretty easy:

`$ pod spec create Peanut`

`$ edit Peanut.podspec`

`$ pod spec lint Peanut.podspec`


*You can find a lot of information on the [process in the guides](http://guides.cocoapods.org/).*
 
*When you're done you can get an account and push your [pod to the CocoaPods Trunk](http://guides.cocoapods.org/making/getting-setup-with-trunk.html).*

---