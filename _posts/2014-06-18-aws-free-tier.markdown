---
layout: post
title:  "About AWS Free Tier"
date:   2014-06-18
category: amazon
---

I've recently created a [Free Tier AWS][aws-free] subscription (available for one year). This includes
all their services (EC2, S3, CloudWatch etc.) for **free**, with [limitations][aws-price] of course.

I mainly played with EC2 so I'll share things I found out. Even though it's free, you still
have to be careful to not get billed (mostly on I/O opperations).

Creating an instance
===

1. Creating your first instance on EC2 service. Selecting **Instances** from dashboard
and then **Launch Instance** will prompt some AMIs (Amazon Machine Image) from which
you have to choose. Being on a Free Tier, I opted for the *Ubuntu 64bit* one, as I was comfortable
with it. Amazon Linux uses `yum`.

2. Next you select your instance type. Micro kind of sucks, it's very slow (also see 613MiB RAM),
so you'll have to supply it some **swap** too (more about it in just a bit). As I didn't want to
pay, I selected Micro for Free tier.

3. Make sure you don't skip step 4 **Add Storage**, as clicking next may get you to the end where
you just **Review and Launch**.

4. At step **Add Storage** you will most definetly like to **uncheck Delete on Termination** on your
root Volume. Also you might want to add more than 8GiB to your root volume? I wasn't paying attention
to this step at first so I had to add a new volume later and mount it so I can get more space.
(**NOTE** you only have 30GiB in Free Tier at the time I'm writing, and leave the type Magnetic,
don't think you have SSD in Free Tier either ; moreover, use no encryption on HDD)

5. Before launching you will go through a final step to get an **SSH private key**, store it well and don't
loose it, you'll use it to connect to your newly launched instance.


Tips on using the instance
====

7. I personally did an alias on my desktop/laptop:

        $ echo "alias sshaws='ssh -i ~/.ssh/aws/my.pem ubuntu@your-ip'" >> ~/.bash_aliases
        $ source ~/.bash_aliases
Now you can simply do `sshaws`. Make sure to replace with `your-ip` and the path to your `.pem`.

8. You **should add** yourself some **swap**. Else you will bump into problems
like the operating system killing your processes in case it runs out of memory (`dmesg` for output)
and you'll won't know what hit you :). See this [stack overflow post][swap], very easy.

9. If you somehow want to migrate to a newer better instance in the future and save your
installed files and saved data, you can just migrate the Root Volume from your old instance
(you can even terminate the instance, remember you unchecked that option in step 4.). Check
[another SO post][volume] for how to, easy again.

10. Set `noatime` as a parameter with which your HDD (/dev/xvda1 probably? see `df` and look for the one
which is mounted on `/`). Check my `/etc/fstab` below. See [this tutorial][fstab] too.

        ubuntu@ip-xxx:$ cat /etc/fstab
        LABEL=cloudimg-rootfs	/	 ext4	defaults	0 0
        /dev/xvda1 / ext4 rw,noatime,nodiratime 0 0
        /var/swap.1 swap swap defaults 0 0
Also notice the `/var/swap.1` from [SO][swap]. You need to `$ sudo reboot` machine and reconnect via SSH
to see changes.

Surpassing the Free Tier (getting billed)
===

11. Make sure to check the [AWS Pricing][aws-price] before using. Also the [AWS Billing Page][aws-billing] regularly.

12. The I/O requests can be easily surpassed (I did that with a mongoDB server and few days of read/writes).
You can [learn how to calculate your I/O requests][calculate-io-req]. If you don't know what they are, see [aws forums][what-io-req].
Don't worry that much if you surpass it, it's just 0.05$ (at least now) per 1 million I/O for Free Tier. You can also monitor
your total I/O requests in the [billing page][aws-billing] by going to bill details.


tl;dr I liked the AWS Free Tier experience (even if I got billed 3$ eventually :), try it
as you've got nothing to loose.
For a well written intro also you can check [this one][aws-intro].

Have a great time!

If you know things better/differently please tell, I'd like to find out new things!
<br><br>

[aws-free]: http://aws.amazon.com/free/
[swap]: http://stackoverflow.com/questions/17173972/how-do-you-add-swap-to-an-ec2-instance
[volume]: http://stackoverflow.com/questions/6377669/can-i-change-the-root-ebs-device-of-my-amazon-ec2-instance
[aws-billing]: https://console.aws.amazon.com/billing/
[aws-intro]: http://www.infoworld.com/d/cloud-computing/free-amazon-web-services-and-how-make-the-most-of-them-216105
[aws-price]: http://aws.amazon.com/ec2/pricing/
[fstab]: http://lifehacker.com/5074959/speed-up-linux-hard-drives-by-disabling-atime
[calculate-io-req]: http://www.caseylabs.com/how-to-calculate-amazon-ebs-io-costs/
[what-io-req]: https://forums.aws.amazon.com/thread.jspa?threadID=78919
