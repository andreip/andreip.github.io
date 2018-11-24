---
layout: page
title: Contributions
noindex: true
---

## Open Source Contributions

* [JS] some of public sample [@uberVU](https://github.com/uberVU/mozaic/commit/c2a0e723abfa9abf33ddc3b8575e8bdac4e0b70f) ; we did work in private repo and then published it periodically
* [C] [4 contributions for Freedroid RPG](http://rb.freedroid.org/users/andreip/) but only one was accepted:
	* [accepted](http://rb.freedroid.org/r/1024/diff/)
	* this [rejected one](http://rb.freedroid.org/r/1077/) tackled a memory problem and was hard to find, I feel bad I didn't send an update to the hack
* [Python] [Tweepy](https://github.com/tweepy/tweepy/pull/446) fixed one bug
* [JS, grunt] [Schema inspector](https://github.com/Atinux/schema-inspector/pull/11) fixed a bower install bug
* [ruby] [SUSE Studio CLI client](https://github.com/susestudio/ssc/pull/1) feature
* [Android, Java] [Augmented Reality GUI](https://github.com/aismail/AndroAR)

## Open Source Personal Work

* [Python, Twitter API] [Undergraduate thesis](https://github.com/andreip/tweeter-authorities):
	* computes Twitter authoritative users based on their tweets, calcuating specific metrics and doing some Machine Learning straightforward preprocessing of the input set beforehand
	* [paper here](https://www.dropbox.com/s/3xh7hjxewtgdswe/findingtopicalauthoritiesontwitter.pdf?dl=0)
* [Prolog] [Created homework](https://github.com/andreip/AI-MAS) for AI-class while was in 1st undergraduate year (summer work)
* For full list of repositories and coding style please check my github profile [<img src="/public/img/github.png">](https://github.com/andreip/)


## Technical Knowledge

* [C, Article] [GDB introduction](http://techblog.rosedu.org/gdb-a-basic-workflow.html)
* [Git, Article] [Git aliases](http://techblog.rosedu.org/git-speeding-workflow.html)
* [Flask, Presentation] [ROSEdu CDL course](http://cdl.rosedu.org/editions/unibuc_2013/#details_course3)
* [Git, Presentation] [ROSEdu CDL course](http://cdl.rosedu.org/editions/spring_2013/#details_course2)
* [Python, Teaching] Part of team for [teaching python in schools](http://py4school.rosedu.org/)

## Closed Source Contributions

### [UpbeatPR](https://www.upbeatpr.com/)

* was one of the first engineers to join the team to work on Upbeat's new exiting greenfield work there! Initially we focused our attention on bloggers/content creators who could potentially write about a company (our client) for a small fee and thus would benefit from this influencer's audience.
* pivoted eventually to match journalists with our clients and so we started focusing on being up to date with what journalists write across all the publications on the web that were using english!
* Here's a more extensive list of things I've done while with the company:
	* a client had trouble updating his credit card info and I jumped on it to fix a client's pain point. The old code was integrating with Stripe but was now using old API and soon to go unsupported, so I took this opportunity to refactor the code with stripe's new library (stripe react elements) and I was able to:
		* remove code on our end (less code to maintain!)
		* fix the client's pain point and he could now both add and update their credit cards in a secure way
	* for our scraper infrastructure, built a system that ran a subset of our unit tests by doing live http requests (so sort of like integration tests we could call them) to verify that the scraping rules we had in place continued to work on the publication websites (they could in the meantime update their website and unit tests would have still passed)
	* feed poller system to poll feeds with several subsequent improvements:
		* head requests with last-modified/etag headers for efficiency checking
		* adaptive feed polling interval (poll feeds every 5m/10m/1h/1d)
		* async requests using gevent and celery
		* coached a colleague to built a feed finder (given a publication finds all feeds for it)
	* did out ElasticSearch setup (before we were using various external search providers)
		* had the idea of detecting possible hits through links in the documents we store and built that as first prototype which put us in a positive light in client's eyes!
		* built graphs & metrics in kibana (e.g. number of articles with or without author, # of articles in crt week/month compared to past week/month, histogram of publications' articles we found etc.)
	* had the idea of concentrating our efforts on a list of priority publications and to improve metrics on those instead which we ended up doing and striving for!
	* the ES search system wasn't surfacing relevant journalists sometimes, and I looked into why that was:
		* the scoring of a journlist I made it so it was the sum of the individual scores of the articles that matched the current search terms, so usually if a journalist had 19 articles and another had only 2 articles, the former would probably score higher!
		* but it turned out that we had some duplicate articles in the database (those came to be because we used a normalized version of the url as the key of the content stored in ES)
		* I ended up hashing the content and keeping the hash as a key on each ES document, so when a new article was ready to be indexed, I checked if the hash was equal and if it was, checked against the content and if that was equal, it was a duplicate so wouldn't index it (similar to Rabin-Karp algorithm) and that fixed the issue in a pretty neat and efficient way
	* added an interface for our PR agents to be able to tell our system to enqueue some URLs for scraping and to even give it some hints that those articles were written by some journalist from our system
		* this interface was used by our PR agents to fill in some important articles and authors that our system didn't have, while working on some campaigns for clients
	* made our scraping system figure out the twitter account of the journalist that wrote the article by doing a name check with an extra hit on twitter; it was important to get as much meta-data about the journalist who wrote the article we were scraping, in order to personalize the pitching to each journalist as much as possible! Having twitter information accurate was very important in that sense and increased our numbers by about 10% of total articles we were able to link with an identity of an author. Moreover, more than 70% of our twitter info improved and became reliable now; unlike before when some twitter accounts were mis-matched against identitis from time to time, now the info was sanity-checked let's say.
		* the scaper cached information to avoid repeated checks (similar to how you'd do memoization in a DP problem)
	

### [TradeIT](https://www.tradingticket.com/), while working for dev.Label

* [check demo](https://www.tradingticket.com/widget/examples.html)
* with the widget you can easily buy/sell actions from multiple brokers
* worked on:
	* frontend: Coffeescript, Javascript
	* backend: grails, Geb (implements webdriver API) which one can use to perform browser actions

### [uberVU](http://ubervu.com/)

#### Facts

* Did ~1700 commits in the main repository
* languages: Python, Coffeescript, Javascript
* frameworks, libraries: django, tastypie, elasticsearch, mozaicJS
* databases: mysql, mongoDB
* worked on almost all features from [this video](https://www.youtube.com/watch?v=wFN_Lw6WSg0) and more

#### Some Features I worked on

* having actions generic enough to work for both [signals](https://drive.google.com/file/d/0Bxk_4cdT7c8fdnhEcDdPdmI2T28/view?usp=sharing) and for [mentions](https://drive.google.com/file/d/0Bxk_4cdT7c8fM2dKX1ZLdjBaX2M/view?usp=sharing)

* [analytics page](https://drive.google.com/file/d/0Bxk_4cdT7c8fSFU4SXBMWlRmMzg/view?usp=sharing)

	In backend, for [Conversation Map from screenshot](https://drive.google.com/file/d/0Bxk_4cdT7c8fSFU4SXBMWlRmMzg/view?usp=sharing) I did fix the way the top n-grams were computed on GET: applied stemming for the search words before combining results from 8 hour analytics, so as to not have words like 'car' 2% and 'cars' 3% both appear in results, but rather combine them and obtain 'car' ~ 4-5%.

* also being able to customize widgets into [boards](https://drive.google.com/file/d/0Bxk_4cdT7c8fbGZJaWRuTWRPbms/view?usp=sharing) and [reports](https://drive.google.com/file/d/0Bxk_4cdT7c8fYmxxcVlDOEw0VWs/view?usp=sharing)
* allowing users to [engage with their social media accounts](https://drive.google.com/file/d/0Bxk_4cdT7c8fa0lDR3NCRlh3X2c/view?usp=sharing)
* see overview of [group activity](https://drive.google.com/file/d/0Bxk_4cdT7c8faXZrV2hKS2RsUE0/view?usp=sharing)
* offering users [recommended top stories to post about a topic](https://drive.google.com/file/d/0Bxk_4cdT7c8fR0t6MV9LQmpZcjQ/view?usp=sharing)
* [change between multiple groups](https://drive.google.com/file/d/0Bxk_4cdT7c8fU3cxNktyRENUeDQ/view?usp=sharing) of your brand's social media teams
* all [account settings](https://drive.google.com/file/d/0Bxk_4cdT7c8fekJKMmNhVEo1Umc/view?usp=sharing) sections
* being able to do [search in search](https://drive.google.com/file/d/0Bxk_4cdT7c8fb0pGRVpKTGtkdnM/view?usp=sharing) (in already filtered mentions)
* and a lot other small features, legacy code refactoring and bugs which would be to hard to remember and explain thoroughly
