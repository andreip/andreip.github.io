---
layout: post
title:  "Suse Studio Command Line Client (ssc)"
date:   2012-03-22
category: tech
---

Hello. My name is Andrei Petre, a 2nd year student at Politehnica University of Bucharest, Romania, and I'd like to work on [Suse Studio Command Line Client](https://github.com/susestudio/ssc) (ssc) during Google Summer of Code 2012, mentored by Cristian Mircea Messel. The GSoC project on the OpenSuse page can be found [here](http://en.opensuse.org/openSUSE:GSOC_ideas#SUSE_Studio_Command_Line_Client_.28ssc.29).

My main motive for writing this blog post is to be able to easily point the Suse Studio community to it and gather ideas, oppinions, or any sort of feedback on it.

Suse Studio is a browser based Linux image creation tool. You can create a custom Linux OS, with applications and packages of your choosing. It also includes a testdrive, so you can test your appliance (custom created distro) not just by building and running it on a live cd/usb, but within your own browser.
SSC is a command line client which aims to help feed back changes to Studio, so that these are applied to your appliance the next time you build it. It can also query your appliance(s). It would be another approach towards Studio, as the browser interaction is the only option until now. SSC would be easy to use and would help very much in scripting.

A list of commands without their complete list of arguments are:

{% highlight bash %}
$  ssc checkout          # checkout the latest changes to an appliance
$  ssc commit            # commit changes to studio
$  ssc status            # show status of the appliance

$  ssc appliance         # manage appliances
$  ssc build             # manage builds
$  ssc file              # manage files
$  ssc package           # manage packages
$  ssc repository        # manage repositories
$  ssc template          # manage templates

$  ssc help [TASK]       # Describe available tasks or one specific task
{% endhighlight %}

To clone an existing appliance, you give the below command. You can also use -u and -p for username and password:

{% highlight bash %}
$ ssc appliance create web_server --source-id=SOURCE_APPLIANCE_ID --username=USERNAME --password=PASSWORD
{% endhighlight %}

For these pretty CLI options, SSC uses [thor](https://github.com/wycats/thor/wiki). And for the working with Suse Studio, it uses the [studio_api](https://github.com/jreidinger/studio_api#readme) API. After you have created a new appliance, a folder with the **#{web_server}** name is created, containing a **.sscrc** file, which stores your credentials (provided above) using YAML.

Here is a list of ideas. Anyone is more than welcome to express his/her ideas by leaving comments :). Actually, I'd be very glad if you do so.
- check for bugs in current implementation, get some workflow going
- be able to feed your changes to Studio right from your appliance
- ~~SSC build to be able to build the appliance locally~~
  - ~~Cristian provided an [idea](http://doc.opensuse.org/products/other/Studio/susestudio-user_sd_draft/app.studio.kiwi-and-autoyast.html#sec.studiouser.exportkiwi) for this approach to export it in kiwi and build it locally (thanks tigerfoot for the idea)~~
  - Support not provided by the Studio API
