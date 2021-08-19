---
templateKey: blog-post
title: Adding google analytic to your blog
date: 2021-08-19T06:14:21.551Z
description: Adding google analytic to your blog with gatsby-plugin-google-gtag
  and gatsby-plugin-react-helmet
featuredpost: true
featuredimage: /img/ga.jpg
tags:
  - google-analytic
  - helmet
---
![](/img/ga.jpg)

Google analytic is mandatory to keep track the traffic and viewer behaviour on your site. In this article, we will go through how to do it base on our previous work [here](https://andy.povalab.com/blog/2021-08-19-start-your-self-hosted-blog-in-30-minutes/) and [here](https://andy.povalab.com/blog/2021-08-19-setup-netlify-cms-for-self-hosted-blog/).

## Step 1 - Get your google analytic measurement ID

Login to [https://analytics.google.com](https://analytics.google.com/) and go to **ADMIN -> Data Streams**. 

![](/img/ga_step1.jpg)

Then click **Add stream** and select **Web.** Fill in your site url and stream name value, for my case the url is andy.povalab.com and stream name can be anything and I pick "myblog"

![](/img/ga_step2.jpg)

After that select the newly created data stream and you will use the **"measurement ID"** which will be used to setup your site's configuration in next session.

![](/img/ga_step3.jpg)