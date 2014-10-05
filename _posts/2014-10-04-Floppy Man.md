---
layout: post
title: Floppy Man
---

To know how proud I am of myself, you only need to look at this screenshot:

<a href="https://rawgit.com/apiotrow/UnityExperiments/master/ropes/ropes1.0/ropes1.0.html"><img src="/assets/2014-10-04/01.png"></a>

I attempted to create a creature that would keep itself erect by placing its feet in the right place as its weight shifted around. I was inspired by this video:

<center>
<iframe width="560" height="315" src="//www.youtube.com/embed/Qi5adyccoKI" frameborder="0" allowfullscreen></iframe>
</center>

The level of realism there is fucking astonishing. I decided to try to recreate those effects from scratch, starting with just trying making a humanoid keep iself from falling over by shifting it's feet around when the center of gravity moves. I'm not sure when I stopped that, but I think it was around the time I randomly stumbled into <a href="http://pastebin.com/j3DWqe3R">DragRigidBody</a>, a script that allows you to drag items in a scene using the mouse. My project quickly devolved from procedural generation into flinging things around.

I imported some rope-like things I created in a previous project, which use <a href="http://docs.unity3d.com/Manual/class-ConfigurableJoint.html">Configurable Joints</a> to connect with each other in a chain. I think these are generally used for limbs, signs, doors, and other swinging things. Once I got the rope thing working though, I've been obsessed with it. It's incredibly versatile, usable for anything from wrecking balls to horse-lifting:

<img src="/assets/2014-10-04/02.png">
<img src="/assets/2014-10-04/03.png">

I'll probably throw it up on the Unity asset store eventually. I can't deny the masses something as ingenious and clearly error-free as this.

I also recently found out that porting Unity projects to Android is fairly painless. Floppy Man didn't even require implementing a control scheme for touch-screen. Alice did, however. I had to find a mobile joystick/button tool to make that game playable. It's something I'll probably experiment with more in the future:

<center><img src="/assets/2014-10-04/05.jpg"></center>

Then again, I'm being ever so slightly encouraged by a professor of mine to move away from Unity, and into a more C++-based environment. I've resisted as long as I could, due to the lack of any decent C++-based game engine or game-oriented libraries out there, but my will is weakening. I may begin using SFML soon, hardcoding games for 2 weeks that will be on par with a game that could be made in GameMaker in 2 days. But it's all about street cred, right? Knowing those pointers, those templates, those type declarations, those mallocs, and that polymorphism.