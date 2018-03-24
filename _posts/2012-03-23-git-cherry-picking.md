---
layout: post
title:  "git cherry picking"
date:   2012-03-23
category: tech
---

I recently read [this awesome git tutorial](http://gitolite.com/gcs.html), about what is going on inside git for a day-to-day workflow like checkout, reset, branching, HEAD, commit etc. And I found myself in the bellow situation, when I remembered what I learned. Here's the `master` branch:

![master branch]({{ "assets/img/posts/git-cherry-pick1.png" | absolute_url }})

And now, here's my `old_dev` branch, on which I have some unmerged commits:

![old dev branch]({{ "assets/img/posts/git-cherry-pick2.png" | absolute_url }})

Suppose now that I only what the commit on which old_dev is pointing to (SHA d33957a). Where I to:

{% highlight bash %}
$ git merge old_dev
{% endhighlight %}

from `master` branch, I would add commit `9fdd36a`, which is "buggy" (as the commit message says), and I don't want that. Also, I may be required to resolve some merge conflicts manually. So to "pick" only a specific commit, one **cherry-pick**s that commit only, once you're on the branch you want to apply that commit onto:

{% highlight bash %}
$ git cherry-pick d33957a
{% endhighlight %}

Now the `master` branch only has the commit I wanted to add in the first place:

![master branch with cherry-picked commit]({{ "assets/img/posts/git-cherry-pick3.png" | absolute_url }})

