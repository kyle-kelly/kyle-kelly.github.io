---
layout:			post
title: 			"Reviewing the Reviewers"
subtitle:		"A quantitative statistical analysis of movie review publications over the last 5 years"
date:   		2017-06-14
header-img:		"img/mykonos-sunset.jpg"
---
# Reviewing the reviewers

A wise man once said, "Opinions are like assholes: they're all full of shit!" Or maybe that was an insane man...Either way, what are movie reviews but an opinion with a number attached? And it's my opinion that we've reached the review saturation point. Print publictions review movies. Bloggers review movies. Moviegoers review movies. Websites score movies based on users' scores of movies. There are more reviews than any one [sarlacc](https://en.wikipedia.org/wiki/Sarlacc) could swallow!

So the real questions is: who can we trust?...who's reviewing the reviewers?

![Alt]({{ site.url }}/img/watches-the-watchmen.jpg "Marketing image from the 2009 film 'Watchmen'")

Well, today it's me. I'm reviewing the reviewers. But first I'll need to talk a bit about how movies are scored and where my data came from. Personally, I could talk about this all day, but some people might only care for the results. If you're one of those people, click [here](). Otherwise, come friend, let's argue about rating systems.

## One rating to rule them all

Just like [Mia Wallace says](https://www.youtube.com/watch?v=LbTcqyimYVY#t=1m6s), "...when it comes to important subjects, there are only two ways a person can answer. Which way they chose, tells you who that person is." So who are you, a Rotten Tomatoes person or an IMDb person? I suppose they each have their merits, but without having this devolve into diatribe I will try to briefly explain why I am an IMDb person.

Rotten Tomatoes uses what they call the [Tomatometer](https://www.rottentomatoes.com/about/) which "represents the percentage of professional critic reviews that are positive for a given film or television show." So, essentially what Rotten Tomatoes does is take reviews from other publications, rescale them to a binary scale ("fresh" or "rotten") and then issue their Tomatometer score, which is the number of fresh reviews as a percentage of total reviews.

The [IMDb rating system](http://www.imdb.com/help/show_leaf?votestopfaq) is much different. For each movie and TV show they "take all the individual votes cast by IMDb registered users and use them to calculate a single rating" using a [weighted average](https://en.wikipedia.org/wiki/Weighted_arithmetic_mean). Scores can range from 1 to 10, and although their scoring scheme is proprietary, it employs [statistical methods](http://www.imdb.com/help/show_leaf?votes), such a trimmed mean and weighting system, to prevent abuse.

It seems like a lot is lost when Rotten Tomatoes translates reviews to either "fresh" or "rotten". It misrepresents the reviewer and the minutae of their review. And then for some reason they decide to average this score, which basically rescales to a 0 to 10 rating. Why not just stick to your guns and only label the movie as "fresh" or "rotten" and not show the misleading perecentage? 

However, some might argue that becuase we don't know how IMDb assigns weights their system is inherently untrustworthy. In reality, the system most-likely is used to prevent ballot stuffing and to prevent one demographic from having too much sway over the final rating.

Why is any of this important? Well, to figure out which movie review publication is the best we need to know the true rating....one rating to rule them all!

![Alt]({{ site.url }}/img/one-ring.jpg "One ring to rule them all'")

This is where the IMDb rating comes in: basically just something to compare each review against. We'll say the IMDb rating is the true movie rating and that movie review publications are attempting to predict or estimate this rating. In this way we can quantify how good each publication is!

## Ratings means data

The most time intensive step was building the [dataset](https://github.com/kyle-kelly/reviewing_reviewers/blob/master/data/ratings_data.csv). 

## What do you mean squared error? 

## Who's the best?