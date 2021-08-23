---
templateKey: blog-post
title: MPEG-2 Transport Stream TimeStamp (Part 1)
date: 2021-08-23T06:26:28.818Z
description: Introduction to MPEG-2 Transport Stream TimeStamp - program clock
  reference (PCR), presentation time stamp (PTS) and decoding time stamp (DTS).
featuredpost: false
online: false
featuredimage: https://www.haivision.com/wp-content/uploads/ind_broadcast_hero.jpg
---
![](https://www.haivision.com/wp-content/uploads/ind_broadcast_hero.jpg)

MPEG-2 Transport Stream (or just transport stream) is a system level container format to embed video and audio data. The format is heavily used in the broadcast/cable industry like Comcast, Sky etc to transmit video and audio system over IP for two scenarios

1. transmit video/audio signal within the cable head-end between broadcast equipments e.g. from QAM to encoder
2. transmit video/audio signal from cable head-end to individual subscribed users' set-top box via the private cable network

There are three timestamps in transport stream playing an important role in synchronizing video and audio data perfectly across different part of the broadcast system:

* program clock reference
* presentation timestamp
* decoding timestamp

We hope that after this series you will have a better understanding what they are and how they work in a high level sense.