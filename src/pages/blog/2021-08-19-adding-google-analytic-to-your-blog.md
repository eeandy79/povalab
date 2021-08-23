---
templateKey: blog-post
title: "Start your self-hosted blog in 60 minutes (Part 3) "
date: 2021-08-19T06:14:21.551Z
description: How to adding google analytic to your blog with
  gatsby-plugin-google-gtag and gatsby-plugin-react-helmet.
featuredpost: true
online: true
featuredimage: /img/ga.jpg
tags:
  - google-analytic
  - helmet
  - seo
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

## Step 2 - Install and setup google-analytic plugin

Go to your development environment, add and install google-analytic plugin to your site by 

1. open package.json and add "gatsby-plugin-google-gtag": "^3.10.0" to the configuration file
2. npm install

Open and add the following gasby-config.js where the trackingIds is the **"measurement ID"** we got in Step 1.

```
{
  resolve: 'gatsby-plugin-google-gtag',
  options: {
    trackingIds: ["G-CPMP5YWW1L"]
  },
}
```

Commit the change and after Netlify build and deploy your latest changes your site will be able to be keep tracked by google-analytic. Open your site and you will see it will keep firing event to google-analytic backend.

![](/img/ga_step4.jpg)

Go to [https://analytics.google.com](https://analytics.google.com/) you will see the analytic result. I am amazed I already see some traffic to my site with two days as below

![](/img/ga_step5.jpg)

## Step 3 - Using Helmet for SEO

The [gatsby-starter-netlify-cms](https://github.com/netlify-templates/gatsby-starter-netlify-cms) template I am using already got gatsby-plugin-react-helmet installed. What Helmet do is to embed information to the HTML page to enable easier search by google bot. When you view your HTML source with Helmet data you will see the following.

![](/img/ga_step6.jpg)

The Helmet data will be shown to the google analytic result as well. Looking at the google analytic report example in last session; we can see **"Start your self...minutes | Blog"** in the **"PAGE TITLE AND SCREEN..."** session. This helps us understand visitor's behavior on our site.

To use Helmet is pretty easy e.g. for the original template code I am using; it doesn't have a good Helmet for index-page.js. I enhance it by add line 4 and line 20 to 26.

![](/img/ga_step7.jpg)

## Summary

In this article, we have go through how to add google-analytic for site monitoring and basic SEO via Helmet plugin. The source code can be found here:

* https://github.com/eeandy79/myblog

The code have included a little bit of enhancement to control if a post is ready for viewer by adding a "online" flag. When the flag is false, the "in progress" post won't shown to your audience.

Thanks for reading. Please send me an email at povalab@gmail.com for any comment or questions. I am very happy to get feedkback from you.