---
layout:			post
title:  		"Python Wrapper for the PX4Flow Smart Camera"
subtitle:		""
date:   		2017-10-21
header-img: 	"img/gandia-spain.jpg"
---
I had some time (...let's be real, it was a lot of time) to myself this summer before starting my current job and I was struggling with how I should spend it. Initially, I was thinking about camping out on the couch in a pair of shorts, with a pallet of cereal, to crush Netflix orginals between seasons of It's Always Sunny. However, the prospect of facing my girlfriend as she walked in from work everyday, and the soul-crushing shame induced by the daily routine, drove me in another direction.

![Alt]({{ site.url }}/img/Fat_Mac.png "Fat Mac from It's Always Sunny in Philadelphia...also me, in an alternative timeline.")

I ended up volunteering with a very small drone startup out of the University of Maryland. A few stuents had applied for a patent and were hoping to have a working prototype by the end of the summer. They reached out to other students for help, and while I can't say that I knew (or know) too much about drones, it felt like a good opportunity to get my hands on some hardware and write a bit of code.

My small contribution was in the integration of an [optical flow sensor](https://en.wikipedia.org/wiki/Optical_flow#Optical_flow_sensor), which is critical to the stabilization and navigation of the drone. These sensors are comprised of a digital image sensor with a lens, to take images of a scene, and a CPU, which calculates optical flow to measure apparent motion of objects in the image.

The team decided to go with the [PX4Flow Smart Camera](https://pixhawk.org/modules/px4flow). This sensor also includes a [gyroscope](https://en.wikipedia.org/wiki/Gyroscope) to measure angular velocity, and a sonar to measure ground distance.

The wrapper I created is intended to be run from a Raspberry Pi 3 and communicate with the sensor via the I2C bus. Once you create an instance of the sensor in your code, you can ping the sensor to update its data registers and then read out any [value that the sensor supplies](https://pixhawk.org/modules/px4flow#data_output). That's it!

Since classes started at the University of Maryland I haven't heard much from the drone team, but if you're out there and you're reading this -- I hope all is well and that the code works as intended. Fly true, fellow Terps.

Click [here](https://github.com/kyle-kelly/PX4Flow_python) to check out the code on my GitHub!
