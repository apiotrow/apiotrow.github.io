---
layout: post
title: We Jekyll Now
---

Had this idea of a plate, and on the plate is a ball. The plate has to continually tilt in order to keep the ball from rolling off the edge. I wondered how effective I could make an AI plate. Ended up with more-or-less this:


{% highlight c# %}
platePos = transform.position;
ballPos = ball.transform.position;

float xdiff = platePos.x - ballPos.x;
float zdiff = platePos.z - ballPos.z;
dist = Vector3.Distance (ballPos, platePos);
float xrot = transform.rotation.eulerAngles.x;
float zrot = transform.rotation.eulerAngles.z;

if (xdiff < 0) {
	transform.RotateAround (transform.position, Vector3.forward, Time.deltaTime * dist);
} else {
		transform.RotateAround (transform.position, Vector3.back, Time.deltaTime * dist);
}

if (zdiff < 0) {
	transform.RotateAround (transform.position, Vector3.left, Time.deltaTime * dist);
} else {
	transform.RotateAround (transform.position, Vector3.right, Time.deltaTime * dist);
}
{% endhighlight %}

This method I consider a bit amateurish. I'm just testing the ball's position relative to the center of the plate. If it's off to one side, the plate tilts. How quickly it tilts depends on the ball's distance from the center. As the ball nears the edge, the plate will begin tilting faster. The downside of this method is the plate gets jittery at extreme tilts, most likely because I'm tilting on two axes at once. I tried the pro method of determining the needed axis of tiltage by calculating a vector off of the ball. The vector worked, but the tilt didn't. Fucking quaternions.

![balance]({{ site.url }}/assets/2014-08-19/balancesc.png)

