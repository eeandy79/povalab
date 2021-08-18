---
templateKey: blog-post
title: Start your self-hosted blog in 30 minutes
date: 2021-08-13T08:55:36.505Z
description: Start your self-hosted blog in 30 minutes
featuredpost: false
featuredimage: /img/blog.jpg
tags:
  - Netlify
  - Gatsby
  - CMS
  - Blog
---
![](/img/blog.jpg)

The first thing we gonna do is to have a website with following requirements

* No cost in hosting the site
* Quick to build e.g. with 30 minutes
* Headless CMS for blogging 

To achieve the above requirements, below is the technical stack

* [Netlify](https://www.netlify.com/) for hosting which include headless CMS for blogging support
* [Gatsby](https://www.gatsbyjs.com/) framework base on [gatsby-starter-netlify-cms](https://github.com/netlify-templates/gatsby-starter-netlify-cms) template

Below is the step by step guide to bring up the site.

## Step 1 - Setup the development environment

My development environment is Ubuntu 20.04. We need the following being installed in our development environment

1. Please follow [here](https://linuxize.com/post/how-to-install-node-js-on-ubuntu-18.04/) to install nodejs and npm
2. Install gatsby-cli by **"sudo npm install -g gatsby-cli"**
3. Please follow [here](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) to access your GitHub account (Please create new account if necessary)

## Step 2 - Checkout the template to GitHub

Login to your GitHub account (and create one if needed) and go to [gatsby-starter-netlify-cms](https://github.com/netlify-templates/gatsby-starter-netlify-cms). 

* Check **"Use this template"** to add the project to your repository

![](/img/step1.jpg)

* Fill-in the **"Repository name"** and click **"Create repository from template"**

![](/img/step1b.jpg)

## Step 3 - Checkout and build

To make sure the template work as expected. Checkout and build the template by

1. git clone git@github.com:***your_account***/myblog.git
2. cd myblog
3. npm install

The build and start the website by **"gatsby develop --host=0.0.0.0"**. Sadly, you will see this in your console.

![](/img/step1c.jpg)

To fix this open gatsby-config.js and replace 'gatsby-plugin-sass' in below:

```
plugins: [
    'gatsby-plugin-react-helmet',
    'gatsby-plugin-sass',
    {
      // keep as first gatsby-source-filesystem plugin for gatsby image support
      resolve: 'gatsby-source-filesystem',
      options: {
        path: `${__dirname}/static/img`,
        name: 'uploads',
      },
    },
```

To this:

```
 plugins: [
    'gatsby-plugin-react-helmet',
    {
      resolve: 'gatsby-plugin-sass',
      options: {
        indentedSyntax: true
      }
    },
```

Run **"gatsby develop --host=0.0.0.0"** now you should see the site up and running at port 8000

![](/img/step1d.jpg)

Finally, check in the fix and we are ready to host it to Netlify.

## Step 4 - Host your site to Netlify

Login [Netlify](https://app.netlify.com/) with your GitHub account. On the Team overview page below; click **"New site from Git"** to create a new site as below. Select **GitHub**

![](/img/step2b.jpg)

Pick the newly created repository in GitHub to continue; in my case that is **myblog**. Click **"Deploy site"** and Netify will start building and deploying your site. From now on, as far as you have new commit to this project on GitHub; Netify will automatically trigger a new build and deploy base on your latest code.

![](/img/step2c.jpg)

After a while you will see your new project been deployed on Netlify CDN e.g. the site can be accessed at [https://adoring-franklin-585280.netlify.app](https://adoring-franklin-585280.netlify.app/)

![](/img/step2d.jpg)

## Summary

In this article, we go through the steps to bring up a gatsby template with CMS support on Netlify. It's quick, nearly no code so far (except a bug fix on config file) and most important **"it's free"**. In the next article, we are going to talk about how to setup Netlify-CMS to manage the blog e.g. create, modify articles like what I am doing right now.

Thanks for reading. Please send me an email at povalab@gmail.com for any comment.