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

One scenario using SPTS is for the back-end to receive high quality live SPTS (e.g. ESPN sport at 20Mbps) from satellite and transcoded it to lower bitrate before sending to end user.

The program  received will be compressed by an encoder appliance by feeding in the signal via SDI or SPTS over UDP and outputting SPTS over UDP multicast. Note that most of the encoder appliance in the market output SPTS only.

## Multiple program transport stream (MPTS)

MPTS enable set-top boxes to switch between different channel/program seamlessly. For example, MPTS contains specific packets to tell set-top boxes available programs in the stream as well as their program name such that viewer can list and select the program they are interested.

Below is an MPTS with two services (or program) if Service 1 is 2Mbps CBR and Service 2 is 4Mbps CBR; the overall bitrate for the MPTS will be 6Mbps. The MPTS will be broadcasted via UDP multicast from the cable head-end; set-top boxes will start receiving the MPTS packets by firing an IGMP request with the MPTS multicast address.

![](https://media-exp1.licdn.com/dms/image/C4D12AQF8o6L8sUTlAQ/article-inline_image-shrink_1000_1488/0/1623747546756?e=1635984000&v=beta&t=r0w16gHD-XdLvhwmgHoHUUJ33tgGnQpHHCHBBsMeWGo)