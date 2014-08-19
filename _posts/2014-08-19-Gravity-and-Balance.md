---
layout: post
title: Gravity and Balance
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
	transform.RotateAround (transform.position, 
	Vector3.forward, 
	Time.deltaTime * dist);
} else {
	transform.RotateAround (transform.position, 
	Vector3.back, 
	Time.deltaTime * dist);
}

if (zdiff < 0) {
	transform.RotateAround (transform.position, 
	Vector3.left, 
	Time.deltaTime * dist);
} else {
	transform.RotateAround (transform.position, 
	Vector3.right, 
	Time.deltaTime * dist);
}
{% endhighlight %}

This method is a bit amateurish. I'm just testing the ball's position relative to the center of the plate. If it's off to one side, the plate tilts. How quickly it tilts depends on the ball's distance from the center. As the ball nears the edge, the plate will begin tilting faster. The downside of this method is the plate gets jittery at extreme tilts, most likely because I'm tilting on two axes at once. I tried the pro method of determining the needed axis of tiltage by calculating a vector off of the ball. When I tried that, the vector worked, but the tilt didn't. I blame quaternions, and my refusal to understand what a quaternion is.

<a href="https://rawgit.com/apiotrow/UnityExperiments/master/balance/balance.html"><img src="/assets/2014-08-19/balancesc.png"></a>


I also added to a project I didn't think would go anywhere. It started out as an attempt to make a game where you leap from planet to planet, coming under the effect of their gravitational fields as you neared them. As I worked on it, I moved away from that and just ended up wanting to make an orbit simulation. I was interested in how some of the "planetary systems" I was making were tending toward equilibrium. So I decided to work on a solar system type thing, where each planet interacted realistically with every other planet. I went balls out and decided to do minimal work with Unity's interface, instead opting to generate as much as I could within the code. I ended up with some pretty sick loops. Check em:


{% highlight c# %}
//array of planets
public Planet[] planets;
	
void Start () {	
numPlanets = PlayerPrefs.GetInt ("numplan");

planets = new Planet[numPlanets];

//inital planet we make clones from
planets[0] = 
	GameObject.Find ("Planet1").GetComponent ("Planet") as Planet;

//the sun
planets[1] = 
	GameObject.Find ("Planet3").GetComponent ("Planet") as Planet;
planets [1].renderer.material.color = Color.yellow;

float maxrange = 200f;

for(int i = 2; i < planets.Length; i++){
	//spawn planet in a random location
	Vector3 randLoc = 
		new Vector3(Random.Range (-maxrange,maxrange), 
			Random.Range (-maxrange,maxrange), 
			Random.Range (-maxrange,maxrange));

	//make a clone
	Planet newplanet = 
		Instantiate (planets[0], randLoc, transform.rotation) as Planet;
		
	//add it to the array
	planets[i] = newplanet;

	planets[i].rigidbody.mass = 
		Random.Range (PlayerPrefs.GetFloat ("massMin"), 
		PlayerPrefs.GetFloat ("massMax"));
	massMax = PlayerPrefs.GetFloat ("massMax");
	massMin = PlayerPrefs.GetFloat ("massMin");

	//random color for planet
	planets[i].renderer.material.color = 
		new Color(Random.Range (0f,1f),
			Random.Range (0f,1f),
			Random.Range (0f,1f));

	//random planet size
	float randScale = Random.Range (1f, 6f);
	planets[i].transform.localScale += 
		new Vector3(randScale,randScale,randScale);

	//some randomization for initial direction
	float rand = Random.Range (0f,1f);
	Vector3 dir;
			
	if(rand > 0f && rand < 0.25f)
		dir = Vector3.left;
	else if(rand > 0.25f && rand < 0.5f)
		dir = Vector3.right;
	else if(rand > 0.5f && rand < 0.75f)
		dir = Vector3.forward;
	else if(rand > 0.75f && rand < 1f)
		dir = Vector3.back;
	else
		dir = Vector3.back;
			
	planets[i].rigidbody.AddForce (dir * 900);
}
}

void FixedUpdate () {
//make every planet influenced by the gravity of every other planet
for(int i = 0; i < planets.Length; i++){
	for(int j = 0; j < planets.Length; j++){
		if (i != j)
			planets[i].rigidbody.AddForce(
			(planets[j].transform.position 
			- planets[i].transform.position) 
			 / (planets[j].rigidbody.mass / 18));
		}
	}
}
}
{% endhighlight %}

Pretty beastly nested loop I have there. Don't act like you're not impressed. This is just a summary of the code. I left out all the butt-ugly GUI and PlayerPref junk. I didn't realize passing data from one scene to another was so easy in Unity. For a long time I thought Application.LoadLevelAdditive was the only way to preserve anything. That's a super ugly method, where you have to iteratively delete every object you don't want passed in to the level you're loading. PlayerPrefs allowed me to keep user-inputs across level reloads. Hence, a brand new GUI to streamline the solar system creation process.

This build is still buggy, but can generate some cool results if you mess with the settings enough. Not sure where I'm going to take this one. I may not find the orbital equlibrium I was seeking, but I think some cooler shit might spawn from this.

<a href="https://rawgit.com/apiotrow/UnityExperiments/master/gravity/gravity.html"><img src="/assets/2014-08-19/orbitsc.png"></a>
