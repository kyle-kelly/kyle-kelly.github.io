---
layout:			post
title: 			"Reviewing the Reviewers"
subtitle:		"A quantitative statistical analysis of 12 movie reviewing publications over the last 5 years"
date:   		2017-06-15
header-img:		"img/mykonos-sunset.jpg"
---

# Reviewing the reviewers

A wise man once said, "Opinions are like assholes: they're all full of shit!" Or maybe that was an insane man...Either way, what are movie reviews but an opinion with a number attached? And it's my opinion that we've reached the review saturation point. Print publictions review movies. Bloggers review movies. Moviegoers review movies. Websites score movies based on users' scores of movies. There are more reviews than any one [sarlacc](https://en.wikipedia.org/wiki/Sarlacc) could swallow!

So the real questions is: who can we trust?...who's reviewing the reviewers?

![Alt]({{ site.url }}/img/watches-the-watchmen.jpg "Marketing image from the 2009 film 'Watchmen'")

Well, today it's me. I'm reviewing the reviewers. But first I'll need to talk a bit about how movies are scored and where my data came from. Personally, I could talk about this all day, but some people might only care for the results. If you're one of those people, click [here]({{ site.url }}/2017/06/15/reviewing-the-reviewers/#whos-the-best). Otherwise, come friend, let's argue about rating systems.

## One rating to rule them all

Just like [Mia Wallace says](https://www.youtube.com/watch?v=LbTcqyimYVY#t=1m6s), "...when it comes to important subjects, there are only two ways a person can answer. Which way they choose, tells you who that person is." So who are you, a Rotten Tomatoes person or an IMDb person? I suppose they each have their merits, but without having this devolve into diatribe I will try to briefly explain why I am an IMDb person.

Rotten Tomatoes uses what they call the [Tomatometer](https://www.rottentomatoes.com/about/) which "represents the percentage of professional critic reviews that are positive for a given film or television show." So, essentially what Rotten Tomatoes does is take reviews from other publications, rescale them to a binary scale ("fresh" or "rotten") and then issue their Tomatometer score, which is the number of fresh reviews as a percentage of total reviews.

The [IMDb rating system](http://www.imdb.com/help/show_leaf?votestopfaq) is much different. For each movie and TV show they "take all the individual votes cast by IMDb registered users and use them to calculate a single rating" using a [weighted average](https://en.wikipedia.org/wiki/Weighted_arithmetic_mean). Scores can range from 1 to 10, and although their scoring scheme is proprietary, it employs [statistical methods](http://www.imdb.com/help/show_leaf?votes), such a trimmed mean and weighting system, to prevent abuse.

It seems like a lot is lost when Rotten Tomatoes translates reviews to either "fresh" or "rotten". It misrepresents the reviewer and the minutae of their review. And then for some reason they decide to average this score, which basically rescales to a 0 to 10 rating. Why not just stick to your guns and only label the movie as "fresh" or "rotten" and not show the misleading perecentage? 

However, some might argue that, becuase we don't know how IMDb assigns weights, the IMDb system is inherently untrustworthy. In reality, the system (most-likely) is used to prevent ballot stuffing and to prevent one demographic from having too much sway over the final rating.

All aside, the main reason I prefer IMDb over other sites is becuase I am a firm believer in the [law of large numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers). IMDb is the world's [most popular movie database](https://en.wikipedia.org/wiki/IMDb) "with approximately 4.2 million titles (including episodes), 7.8 million personalities, as well as 75 million registered users." At the time this article was written, IMDb had an [Alexa rank](https://en.wikipedia.org/wiki/Alexa_Internet) of 55 and [more than 250 million monthly users worldwide](https://en.wikipedia.org/wiki/IMDb#Fan_activity).

Why is any of this important? Well, to figure out which movie review publication is the best we need to know a movie's true rating....the one rating to rule them all!

![Alt]({{ site.url }}/img/one-ring.jpg "One ring to rule them all'")

This is where the IMDb rating comes in: basically just something to compare each review against. We'll say the IMDb rating is the true movie rating and that movie review publications are attempting to predict or estimate this rating. In this way we can quantify how good each publication is!

## Ratings means data

Now we need some movie publications and their ratings to perform our analysis. I decided on the top 50 US grossing films per year, from years 2012 to 2016. I then picked 12 movie reviewing publications that contribute to the Metacritic Metascore. This allowed me to scrape ratings from their website to build my dataset.[^1] The publications were picked somewhat arbitrarily, but in general they are a combination of the most widely circulated US publications and publications that [have reviewed the most movies](http://www.metacritic.com/browse/movies/publication/popular).

A quick note on Metacritic: I would be remiss if I did not mention how Metacritic calculates the rating for each publication. If a publication uses the 4-star scale or letter grade, the rating is  [converted](http://www.metacritic.com/about-metascores) to a rating on a 0 to 100 scale. Basically the score is just extrapolated.

[^1]: It is a violation of the [CBS Interactive Terms of Use](https://cbsi.secure.force.com/CBSi/articles/FAQ/CBS-Interactive--Terms-of-Use?retURL=%2FCBSi%2Fapex%2Fknowledgehome%3Freferer%3DmobileTerms.com&popup=false&categories=CBS_Interactive%3AmTOU&template=template_mobileTerms&referer=mobileTerms.com) to scrape from the Metacritic website.

The most time-intensive step was building the [dataset](https://github.com/kyle-kelly/reviewing_reviewers/blob/master/data/ratings_data.csv). I used Python and [lxml](http://lxml.de/) to scrape IMDb for the movies and their IMDb rating. Unfotunately I wasn't able to scrape Metacritic in the traditional fashion (due to some site protection that blocked my requests) and had to use the [Selenium WebDriver](http://www.seleniumhq.org/projects/webdriver/) as a work around. All the movie titles, ratings and the review publications were written to a CSV file. The complete code can be found [here](https://github.com/kyle-kelly/reviewing_reviewers/blob/master/source/ratings2csv.py).

BOOM! Done. Now we can start doing some maths.

![Alt](https://media2.giphy.com/media/BmmfETghGOPrW/giphy.gif "Zach Galifianakis math gif from 'The Hangover'")

## What do you mean squared error?

As I stated before, we are going to assume that the rating from each publication is an estimate of the IMDb rating, which is taken to be the true rating of the movie. Under this assumption we can use statistics to measure the quality of the estimator through the [mean squared error](https://en.wikipedia.org/wiki/Mean_squared_error).

![Atl]({{site.url}}/img/dont-assume.jpg "Don't assume")

So for each publication, and each movie reviewed by that publication, we find the difference between the publication's rating and the IMDb rating. This difference is called the error. The error is then squared, summed over all movies reviewed by the publication and averaged. The code to perform this calcuation on my dataset can be found [here](https://github.com/kyle-kelly/reviewing_reviewers/blob/master/source/mse.py).

## Who's the best?

Enough already! Time to look at the results. Below is a bar chart plotting the mean squared error (MSE) of each publication for 250 movies over a 5 year period. However, not every publication reviewed every movie. In fact, only The AV Club reviewed all 250 movies, while the Wall Street Journal reviewed the least with 162 movies. The average number of movies reviewed per publication was 222.33.  

![Atl]({{site.url}}/img/mse_IMDB_bar_chart.png "MSE bar chart using IMDb mean")

Here's a ranked table for another look at the results:

Rank | Reviewer | MSE
:---:| --- | ---
1 | USA Today | 171
2 | Boston Globe | 184
3 | The AV Club | 209
4 | Chicago Tribune | 258
5 | Entertainment Weekly | 262
6 | Los Angeles Times | 278
7 | RogerEbert.com | 302
8 | Rolling Stone | 331
9 | The New York Times | 377
10 | Washington Post | 401
11 | New York Post | 616
12 | Wall Street Journal | 735

So there it is: USA Today is the best predictor of the IMDb score. The Boston Globe and The AV Club are not far behind to round out the top three and the Wall Street Journal is about as accurrate as a Stormtrooper.

![Alt](https://i.imgur.com/hz4DpVC.gif "Please hit something")

For shits n' gigs I also calculated the MSE for each publication using the average rating over all publications as our true score. The bar chart and corresponding table are below:

![Atl]({{site.url}}/img/mse_reviewer_bar_chart.png "MSE bar chart using reviewer mean")

Rank | Reviewer | MSE
:---:| --- | ---
1 | Boston Globe | 130
2 | Chicago Tribune | 160
3 | USA Today | 171
4 | Washington Post | 186
5 | The New York Times | 198
6 | Los Angeles Times | 202.1
7 | The AV Club | 202.3
8 | Rolling Stone | 229
9 | RogerEbert.com | 262
10 | New York Post | 307
11 | Wall Street Journal | 340
12 | Entertainment Weekly | 369

USA Today and the Boston Globe are both still in the top three. The MSEs of all publications are also much lower, on the whole. 

Finally, I calculated the another MSE, taking the error to be the difference between the average rating over all publications and the IMDb rating. This produced an MSE of 227, which would not even put it as a top 3 predictor of IMDb ratings. Perhaps removing the Wall Street Journal would change that...

## Afterthoughts

It's interesting to note that USA Today and the Boston Globe use a 4-star scale. So, the extra granularity provided by a letter grade or a 1 to 10 scale don't necessarily make for a better predictor. 

This above method of comparison also doesn't take into account the author of each review. It also makes an assumption about the purpose of the rating attached to each review. In reality, the reviewer is almost certainly not trying to predict the IMDb score of the movie.

Going forward I plan to do a few more things with the dataset. It would also be cool to see how the MSE compares to the [mean absolute error](https://en.wikipedia.org/wiki/Mean_absolute_error) (MAE). I also plan on trying my hand at some modeling and I have already started on [PCA](https://en.wikipedia.org/wiki/Principal_component_analysis) for dimensionality reduction.

Anyway, if you've made it this far, thanks for reading. And if you enjoyed what you've read, then I speak to you the words of Doug Glatt...

![Alt](https://i.imgur.com/QTl3RuG.gif "Seann William Scott in 'Goon'")
