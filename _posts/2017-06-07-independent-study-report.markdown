---
layout:			post
title: 			"Remote Virtual Access to a Vehicle Using Ford’s OpenXC and Exploring Related Vehicle Security Vulnerabilities"
subtitle:		""
date:   		2017-06-07
header-img:		"img/mykonos-night.jpg"
---
In the Summer of 2016, while still pursing my Masters degree, I joined a team of faculty, graduate
and undergraduate students at the University of Maryland on the Ford Vehicle Security project. The goal 
of the project was to explore potential security vulnerabilities of a late-model Ford vehicle with a
particular focus on the [OpenXC platform environment](http://openxcplatform.com/) and on the development of a [hardware-in-the-loop](https://en.wikipedia.org/wiki/Hardware-in-the-loop_simulation)
simulation environment for OpenXC.

Among other things, the project produced an [Android app](https://github.com/nkbalacha/open_xc_1) that leveraged vehicle driving data in real-time 
to provide visual feedback to the driver on the quality of their driving. The app, named Trippy Face,
established a set of rules on acceleration, deceleration and speed limit (using the Google Maps API) and
notfied the driver when these rules were broken. The rule-break locations were also plotted on a map so 
that they could be reviewed by the driver at the end of their trip.

The research project was successful and I was able to continue into the Fall as part of an Independent 
Study for course credit. At the end of the study I produced a paper, and the abstract of that paper
is presented below.
>A Controller Area Network (CAN bus) is the protocol responsible for the communication
>between various embedded systems within an automobile. Recently, the CAN bus has become 
>a conduit for cyber-physical attacks that can potentially put a vehicle’s passengers at great risk
>[1]. Therefore, as we transition in the era of autonomous vehicles, an understanding of the CAN
>bus and its vulnerabilities has never been more important. This report summarizes previous
>work done by students at the University of Maryland to create a hardware-in-the-loop (HIL)
>simulation of a vehicle’s CAN bus. It also summarizes a continuation of that work done as part 
>of a collaboration between the University of Maryland and Ford to investigate vulnerabilities of
>the CAN bus using an open sourced project developed by Ford, called OpenXC. The report
>focuses on an Independent Study involving a project that leveraged various OpenXC tools to log
>CAN data from a Ford vehicle and mirror that data on the a HIL simulation in a lab, in real-time.
>Finally, tangential projects in which an automated assist feature from a Ford Fusion 2017 was
>examined for playback vulnerability, and where a portion of OpenXC code was reverse 
>engineered in an attempt to discover critical CAN information, are also discussed.

Click [here]({{ site.url }}/assets/Independent_Study_Summary_Report.pdf) to download the full paper!

Below, you can view two videos of the hardware-in-the-loop simulation being fed authentic vehcile [CAN 
messages](https://en.wikipedia.org/wiki/CAN_bus) scraped from a server and delivered in real-time. Observe the dials and lights on the Instrument 
Panel Cluster as they change according to the messages they recieve.

<iframe width="560" height="315" src="https://www.youtube.com/embed/6_lFeueNxlw" frameborder="0" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6Ssk2NXEs4A" frameborder="0" allowfullscreen></iframe>
