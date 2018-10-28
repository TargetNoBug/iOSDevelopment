[]() .  
[]() .  
[]() .  
[]() .  
[]() .  
[]() .  
### 2018
[220_high_performance_auto_layout](https://developer.apple.com/videos/play/wwdc2018/220/) .  
But let's talk about what it's doing more concretely now so that we can understand the performance. So the first thing to understand is what exactly is updateConstraints, this method we're overriding. Well, it's one component of the Render Loop. **The Render Loop is the process that runs potentially at 120 times every second**. That makes sure that all the content is ready to go for each frame. OK, so it consists of three phases -- Update Constraints, Layout, and Display. First every view that needs it will receive updateConstraints.

And that runs from the leaf most views up to the view hierarchy towards the window.

Next, every view receives layout sub views. This runs the opposite direction starting from the window going down towards the leaves. Last, every view gets draw if it needs it, that kind of thing. OK, what are these for? Why do they exist? Well, they all have the exact same purpose and they have exact parallel sets of methods.

And that purpose is to avoid wasted work, which I can explain by example.

So a label, a UI label needs to have constraints that describe the size of its text, OK? But there are many properties that contribute to that size. There's the text property itself, there's the font, and the text size, etcetera. One way to do this would be that every time one of those properties changes go re-measure your text.

However, that would often be pretty inefficient because you usually change a bunch of these right in a row. When you're first setting up a label, you're probably going to call a bunch of these property setters and if you're re-measuring text on each one, all the intermediate ones are wasted, you really just want to measure at the end.

And that's what the Render Loop gives you. Because what you can do instead is that inside a set font you can just call setNeedsUpdateConstraints and then you're guaranteed to get update constraints at the end before the frame goes to the screen. And that's what it's for. So the couple things to understand from this before we move on is number one it runs a lot, 120 frames a second.

Number two they're parallel. So you can use that for intuition as well.
