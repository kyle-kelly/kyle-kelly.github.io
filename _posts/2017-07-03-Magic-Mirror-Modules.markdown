---
layout:			post
title: 			"Magic Mirror Modules"
subtitle:		"Displaying ETA and surge charges for Uber and Lyft on a smart mirror"
date:   		2017-07-03
header-img:		"img/mykonos-beach-pano.jpg"
---

## Magic Mirror

The smart mirror! I know you've [seen them on the Internets](https://www.reddit.com/r/smartmirrors/). So sleek. So futuristic. Such wow! I had to have one.

Well, a few months ago I built a smart mirror for my apartment. The process is [pretty well documented](https://magicmirror.builders/), so I'll spare you the details of my build, but I wanted to add some functionality so that the mirror would display the ETA and surge charges for Lyft and Uber.

![Alt]({{ site.url }}/img/smart_mirror.jpg "My reflection in the smart mirror soon after completion.")

I found [this module](https://github.com/derickson/MMderickson/tree/master/uber), although I was never able to get it working on my mirror. I had never worked with JavaScript/Node and didn't know (and still don't really know) anything about back-end communication but I decided to try and hack something together.

## Writing the Modules

MagicMirror does provide [Module Development Documentation](https://github.com/MichMich/MagicMirror/tree/master/modules), however I didn't find it to be particularly useful. Going through the source code for default modules and other existing modules was a better use of time. Especially if you can find a module that performs a function similar to the function in your own module.

Both Uber and Lyft implement [RESTful APIs](https://en.wikipedia.org/wiki/Representational_state_transfer) and require authentication. Fortunately, there was an [npm package](https://www.npmjs.com/package/request#http-authentication) to handle that. For Uber I used a [Server Token](https://developer.uber.com/docs/riders/guides/authentication/introduction#api-token-authentication) to make requests, and for Lyft I used an [OAuth2 "2-legged" flow](https://developer.lyft.com/v1/docs/authentication). [This blog post](https://stormpath.com/blog/talking-to-oauth2-services-with-nodejs) was really helpful with the latter.

Anyway, here's the source for the [Uber module](https://github.com/kyle-kelly/MMM-uber) and for the [Lyft module](https://github.com/kyle-kelly/MMM-lyft). All the back-end work is done in the ```node_helper.js``` file, while the front-end is taken care of in the ```.js``` file. And here's how it'll look on the mirror:

![Alt]({{ site.url }}/img/lyft-uber-screenshot.png "A screenshot of the Lyft and Uber modules.")

Feel free to report issues and submit pull requests!