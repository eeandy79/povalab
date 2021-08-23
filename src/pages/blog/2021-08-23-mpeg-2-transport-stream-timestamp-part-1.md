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

* program clock reference (PCR)
* presentation timestamp (PTS)
* decoding timestamp (DTS)

We hope that after this article you will have a better understanding what they are and how they work in a high level sense.

## Buffer overflow and underflow

In high level, transmitting digital video/audio system within the broadcast system is simply a producer and consumer model e.g.

* Encoder as producer - taking in raw video/audio signal, transcode it and output transport stream to downstream
* Set-top box as consumer - taking upstream transport stream produced by encoder, decode it back to raw video/audio signal and display on your TV

One criteria for the system to play correctly is to make sure the rate of producing the transport stream equal the rate of consuming it i.e.

* If the rate of encoder producing transport stream is **higher** than the consumption rate of set-top box. Buffer **overflow** will be happened on the set-top box, resulting video or audio data lost on TV
* If the rate of encoder producing transport stream is **lower** than the consumption rate of set-top box. Buffer **underflow** will be happened on the set-top box, resulting video get stalled on TV

The most critical part resulting same produce and consume rate is to make sure the producer and consumer clock frequency are synchronized

## Program clock reference (PCR)