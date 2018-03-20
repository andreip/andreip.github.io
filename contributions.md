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
