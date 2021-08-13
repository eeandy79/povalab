---
templateKey: blog-post
title: Start your self-hosted blog in 30 minutes
date: 2016-12-17T15:04:10.000Z
description: Start your self-hosted blog in 30 minutes
featuredpost: false
featuredimage: /img/blog.jpg
tags:
  - flavor
  - tasting
---
![flavor wheel](/img/blog.jpg)

The first thing we gonna do is to have a website with following requirements

* No cost in hosting the site
* Quick to build e.g. with 30 minutes
* Headless CMS for blogging 

To achieve the above requirement, below is the technical stack

* [Netify](https://www.netlify.com/) for hosting which include headless CMS for our blogging support
* [Gatsby](https://www.gatsbyjs.com/) framework base on [gatsby-starter-netlify-cms](https://github.com/netlify-templates/gatsby-starter-netlify-cms) template

Below is the step by step guide to bring up the site.

## Step 1 - Setup the development environment

My development environment is Ubuntu 20.04. To proceed we need the following installed in our development environment

* Please follow [here](https://linuxize.com/post/how-to-install-node-js-on-ubuntu-18.04/) to install nodejs and npm
* Install gatsby-cli by **"sudo npm install -g gatsby-cli"**
* Please follow [here](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) to access your GitHub account

## Step 2 - Checkout the template to GitHub

Login to your github account (and create one if needed) and go to [gatsby-starter-netlify-cms](https://github.com/netlify-templates/gatsby-starter-netlify-cms). 

* Check **"Use this template"** to add the project to your repository

![](/img/step1.jpg)

* Fill-in the **"Repository name"** and click **"Create repository from template"**

![](/img/step1b.jpg)

## Step 3 - Checkout and build

To make sure the template work as expected. Checkout and build the template

* git clone git@github.com:eeandy79/myblog.git
* cd myblog
* npm install

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

Finally, check in the fix and we are ready to host it to Netify.

## Step 4 - Host your site to Netify

In your current GitHub project, find and click **"Deploy to Netlify"** and then click **"Connect to GitHub"** and **"Authorize netlify"**

![](/img/step2.jpg)