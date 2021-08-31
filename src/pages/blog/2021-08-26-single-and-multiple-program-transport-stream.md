---
templateKey: blog-post
title: Single and multiple program transport stream
date: 2021-08-26T04:02:29.676Z
description: What are single (SPTS) and multiple (MPTS) transport stream? What
  are their usage in broadcast industry and a brief introduction to statistical
  multiplexing (StatMux)
featuredpost: false
online: false
featuredimage: https://www.maacindia.com/images/courses/course-img-102.jpg
---
![](https://www.maacindia.com/images/courses/course-img-102.jpg)

MPEG-2 TS is the system layer container to carry video and audio data of the TV **programs** across different part of the broadcast head-end. Base on the number of programs carried in the TS, the industry have defined two terms

1. Single program transport stream (SPTS) - the TS contains only have one program (e.g. ESPN sport)
2. Multiple program transport stream (MPTS) - the TS contains multiple programs (e.g. ESPN sport + News)

Below are some use cases for each of them.

## Single program transport stream (SPTS)

SPTS usually used as encoder/transcoder output



Broadcast head-end usually receive high quality MPTS f

SPTS can be found at the encoder output in the broadcast head-end. The encoder take upstream program signal via SDI (one program) or UDP multicast carrying SPTS or MPTS, transcode it and feed the downstream devices via SPTS over UDP multicast



is being used as the container for c video and audio data in the broadcast industry to carry TV programs