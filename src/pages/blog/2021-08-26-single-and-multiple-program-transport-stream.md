---
templateKey: blog-post
title: Single and multiple program transport stream
date: 2021-08-26T04:02:29.676Z
description: What are single (SPTS) and multiple (MPTS) transport stream? What
  are their usage in broadcast industry? A brief introduction to statistical
  multiplexing (StatMux) as well.
featuredpost: false
online: false
featuredimage: https://www.maacindia.com/images/courses/course-img-102.jpg
---
![](https://www.maacindia.com/images/courses/course-img-102.jpg)

MPEG-2 TS is the system layer container to carry video and audio data of the TV **programs** across different part of the broadcast head-end. Base on the number of programs carried in the TS, the industry have defined two terms

1. Single program transport stream (SPTS) - the TS contains only have one program (e.g. ESPN sport)
2. Multiple program transport stream (MPTS) - the TS contains multiple programs (e.g. ESPN sport + News)

Below are some use cases to share.

## Single program transport stream (SPTS)

The high quality live SPTS program (e.g. ESPN sport at 20Mbps) received by broadcast back-end from satellite will be transcoded to lower bitrate before broadcasting to the downstream set-top boxes. The encoder appliance involve usually take in SDI or SPTS over UDP and output SPTS to downstream.

## Multiple program transport stream (MPTS)