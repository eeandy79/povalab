---
templateKey: blog-post
title: Backend API stress test using artillery.io (in progress)
date: 2021-08-25T08:54:42.653Z
description: Introduction to MPEG-2 Transport Stream TimeStamp - program clock
  reference (PCR), presentation time stamp (PTS) and decoding time stamp (DTS).
featuredpost: false
online: false
featuredimage: https://www.newscaststudio.com/wp-content/uploads/2019/02/broadcast-automation-NCS.jpg
tags:
  - PCR
  - DTS
  - PTS
---
![](https://www.newscaststudio.com/wp-content/uploads/2019/02/broadcast-automation-NCS.jpg)

In the last [article](https://andy.povalab.com/blog/2021-08-23-mpeg-2-transport-stream-timestamp-part-1/), we talk about how to synchronize the clock between upstream (e.g. encoder) and downstream (e.g. set-top box) devices by using the program clock reference (PCR) in the MPEG-2 transport stream. That means all the set-top boxes receiving the TS will run with the **same** clock as the encoder in both value and frequency after clock synchronization.

Given they are running with **same** clock, we are going to talk about decoding and presentation timestamp in the MPEG-2 TS.

## Decoding timestamp (DTS)

Every compressed video and audio frames produced and packaged into TS will be tagged with decoding timestamp (DTS). As the name have implied, DTS is used to instruct decoder the time to decode the compressed video or audio frames and put into the raw frame buffer. As a result, DTS have several attributes to note:

1. DTS run on the same PCR clock time base
2. The first packet of a compressed frame will be attached with DTS and receiving time can be derived with a PCR value. This compressed frame must be fully received between the first packet PCR and DTS; otherwise the compressed frame cannot be decoded at DTS.
3. Base on (2), the first packet DTS must be larger than PCR as illustrated below

![](https://d3i71xaburhd42.cloudfront.net/2d26e07fe9d8c3b881a2334e3f53761d374456ed/4-Figure5-1.png)

## Presentation timestamp (PTS)

Similar to DTS, every compressed video and audio frames are tagged with presentation timestamp (PTS). PTS is used to instruct the decoder when to display the decoded raw video and audio in the frame buffer to the screen.

In real world, DTS is required only if **frame re-ordering** happen i.e. the order of frame transmission is different from the order they display on the TS. This happened on compressed video like AVC or HEVC when B-frame is used to improve the compression efficiency where time to decode and present the compressed video frame is different.

For the example below, the first P frame have been re-ordered and packaged right after the first I-frame in the TS which will be decoded at DTS = 1 and presented at PTS = 3.

![](https://1.bp.blogspot.com/-USpO9dddbRo/Xx9-vt7sJdI/AAAAAAAAGKA/5YrWd2dWoMAF8eZfFftKoxEF-tep5nqMQCLcBGAsYHQ/s1600/ts.jpg)

For compressed audio or video without B-frame; we can skip DTS to save some bandwidth in transmission.

## Summary

In this article, we have talked about using PTS and DTS to control when to decode and present compressed video and audio frames on the decoder side. For PTS and DTS work properly, the decoder need to synchronized the local clock with the input TS via PCR.

Thanks for reading. Please send me an email at povalab@gmail.com for any comment or questions. I am very happy to get feedback from you.