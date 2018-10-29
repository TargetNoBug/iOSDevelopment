


[Building Apps for iPhone X](https://developer.apple.com/videos/play/tech-talks/201) .  

If your app is largely based on standard UIKit controls and you use Auto Layout, then you're in good shape since most of the work will be done for you by UIKit.

 If you use custom controls, or you're not using Auto Layout, or if you're a custom full screen app like many games are, don't worry.

 While there may be some work for you to do, it's not difficult and there is lots of support built in with tools like the new Safe Area layout guides.

-----------------------修复底部太靠近Home Indicator

The problem here is that the page control's bottom constraint is relative to the superview, which is full screen and goes behind the Home indicator.

Instead of constraining to the superview, what we should do is constrain the page control to the Safe Area layout guide at the bottom.

 Let's make that change now.

 I've opened this interface in Xcode, but before I can adjust the constraint I need to enable Safe Area layout guides in this xib file.

 Storyboards and xibs created prior to Xcode 9 will not automatically have Safe Area layout guides turned on.



 One thing to note here is that for iOS storyboards, turning this on will automatically upgrade constraints tied to the scene's top and bottom layout guides, as well as leading and trailing edges. So be sure to review and test your Auto Layout constraints after turning this on.



------------------------修复search bar的颜色和被屏幕圆角剪裁的部分

The color of the search bar background isn't quite right, and the sizing is a bit off.

 And if I rotate to landscape, I can see things don't look right here either.

 The search field and Cancel buttons are both being clipped by the rounded corners of the screen.

 This is a typical example where paying attention to the Safe Area is really important.

 For this search field, what the WWDC app is doing is explicitly presenting a UI search controller.

Now in iOS 11, the search bar can be integrated with the navigation bar, which will give the right presentation like we saw in Contacts.



I'm going to make two changes.

 First, instead of presenting the search controller, we'll hand it to the UINavigationItem for this view controller.

And second, I'll set the search controller's isActive property to true.

This will cause the navigation bar to activate it and start editing.

 Notice that we can use the availability support to only do this for iOS 11, while preserving the existing behavior for older versions of iOS.

 Let's build and run to see how that looks.This looks like the correct presentation of the search field for iOS 11.And in landscape? Terrific(极好的).

 Now the search bar is fitting into the Safe Area nicely, and this is all being automatically managed for us by the navigation bar.



------------------tableview section header.contentView.backgroundColor仅在safe area内有效，造成和tableView.backgroundColor不一致的问题

To help illustrate this, let's start with the really useful View Hierarchy Debugger in Xcode.

By default, table cells will inset their content views so that they are inside the Safe Area.

That insetting behavior is something that you can control.

 In Xcode, you can use the Content View Insets to Safe Area checkbox.(没找到这个)

 There's a corresponding property you can set in code as well.

If you uncheck the checkbox, then the content view will not be inset, and the content view will now go from edge to edge.

One final point here is that regardless of the content view's insetting, the layout margins in the content view will continue to be relative to the Safe Area by default.

Similar to the content view insetting, there are properties that give you control over the behavior of these layout margins.

We can see that we're setting it only on the content view, which is being inset to the Safe Area.

 At this point, there are a couple different ways we could fix this problem.

 One of them would be to disable the table view's default behavior of insetting content views to the Safe Area, but doing that will affect everything else in our content view as well, and we'd lose this helpful default behavior.

 Instead, the best solution here is to set the background color of the background view, which, unlike the inset content view, spans the full width of the cell regardless of any Safe Area insets.（header.backgroundView.backgroundColor=xxColor;）

 With that change, when we build and run, we go from this, where the header background color doesn't go edge to edge, to this, where the colors span the entire table but the content view isn't changed at all.

 That looks much better.

------------------A few quick reminders.

Linking against the iOS 11 SDK and including a Launch Storyboard will enable the fullscreen native resolution for your app.

And while you may see some issues in portrait, the majority will very likely be in landscape so be sure to test all your UI with the interface rotated, both to the left and to the right.

Auto Layout and the safeAreaLayoutGuides will handle a lot of the layout challenges automatically, but if you're doing manual layout you do have access to the Safe Area insets and can do whatever calculations you need.

 This information is available via the UIView class.

 It's also important to not interfere with the Home indicator at the bottom of the screen.

[Building Apps for iPhone XS, iPhone XS Max, and iPhone XR](https://developer.apple.com/videos/play/tech-talks/207/) .  
