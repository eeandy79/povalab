---
templateKey: blog-post
title: Setup Netlify-CMS for self-hosted blog
date: 2021-08-13T08:57:58.855Z
description: How to setup Netify-CMS base on gatsby-starter-netlify-cms template
featuredpost: true
featuredimage: /img/netlify-cms-blog-featured-image-02.png
tags:
  - Netlify-CMS
  - Gatsby
  - Blog
---
![](/img/netlify-cms-blog-featured-image-02.png)

In the last [article](https://andy.povalab.com/blog/2016-12-17-making-sense-of-the-scaas-new-flavor-wheel/), we have gone though to bring up the blog site on Netlify. In this article, we will talk about how to config Netlify-CMS to manage the blog post like create, update, upload image etc.

## Step 1 - Make sure point to the right branch

The idea of Netlify-CMS is to check-in all updates eg. contents, images to your site's git repository. Every commit will eventually trigger Netlify to build and deploy. Hence telling Netlify-CMS pointing to correct git branch is critical.

1. Go to your GitHub account and check the branch name of your site e.g. by default it should be master
2. Go to your development environment and make sure the branch name == your site's git repo branch name (e.g. master) in the "static/admin/config.yml"

   ```
   backend:
     name: git-gateway
     branch: master
     commit_messages:
       create: 'Create {{collection}} “{{slug}}”'
       update: 'Update {{collection}} “{{slug}}”'
       delete: 'Delete {{collection}} “{{slug}}”'
       uploadMedia: '[skip ci] Upload “{{path}}”'
       deleteMedia: '[skip ci] Delete “{{path}}”'
   ```

## Step 2 - Enable Netlify Identity and Git Gateway

Go to your Netlify project / Identify and click **"Enable Identify"** and then click **"Invite users"**. Enter your email address and you will receive invitation email shortly. Complete the registration.

![](/img/netlify_cms_step1.jpg)

Click **"Settings and usage"**

![](/img/netlify_cms_step3.jpg)

Then scroll down to **Services/Git Gateway** click **"Enable Git Gateway"**

![](/img/netlify_cms_step4.jpg)

## Step 3 - Login Netlify CMS

![](/img/netlify_cms_step2.jpg)

Now you are ready to login to Netify-CMS and start manage your content at

* https://***yournetlifydomain***/admin
* in my case it is *https://adoring-franklin-585280.netlify.app/admin*

After login success, boom here it is and you are start managing your content now.

![](/img/netlify_cms_step5.jpg)