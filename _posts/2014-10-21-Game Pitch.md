---
layout: post
title: Game Pitch #1
---

Had to flex my game design skills and create a 2-minute game pitch. I tried to make it programming-centric by building my pitch off of my <a href="https://rawgit.com/apiotrow/UnityExperiments/master/gravity1.2/gravity1.2.html">Orbit Experiment</a>. Inspired by the non-competitive, chill, veg-out game called Flower,

<center>
<iframe width="560" height="315" src="https://www.youtube.com/watch?v=nJam5Auwj1E" frameborder="0" allowfullscreen></iframe>
</center>

I pitched a game where you begin as an electron directly after the big bang, and work your way up in complexity, becoming an atom, a molecule, a macromolecule, a planet, star, solar system, galaxy, ..., universe, or something. I 



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

I also recently found out that porting Unity projects to Android is fairly painless. Floppy Man didn't even require implementing a control scheme for touch-screen. Alice did, however. I had to find a mobile joystick/button tool to make that game playable. I spent about 2 hours in vain trying to get it to play well with Unity's character controller. It ended up looking like it wasn't worth the effort, though, and that making your own controller specifically for the GUI joysticks would be the only option. Still, it looked powerful, so it's something I'll probably experiment with more in the future:

<center><img src="/assets/2014-10-04/05.jpg"></center>

Then again, I'm being ever so slightly encouraged by a professor of mine to move away from Unity, and into a more C++-based environment. I've resisted as long as I could, due to the lack of any decent C++-based game engine or game-oriented libraries out there, but my will is weakening. I may begin using SFML soon, hardcoding games for 2 weeks that will be on par with a game that could be made in GameMaker in 2 days. But it's all about street cred, right? Knowing those pointers, those templates, those type declarations, those mallocs, and that polymorphism.