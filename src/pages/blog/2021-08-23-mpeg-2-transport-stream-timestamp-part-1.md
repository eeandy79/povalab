---
templateKey: blog-post
title: MPEG-2 Transport Stream TimeStamp (Part 1)
date: 2021-08-23T06:26:28.818Z
description: Introduction to MPEG-2 Transport Stream TimeStamp - program clock
  reference (PCR), presentation time stamp (PTS) and decoding time stamp (DTS).
featuredpost: false
online: true
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

* Encoder as producer - taking in raw video/audio signal, encode it and output transport stream to downstream
* Set-top box as consumer - taking upstream transport stream produced by encoder, decode it back to raw video/audio signal and display on the TV

One criteria for the system to play correctly is to make sure the rate of producing and consuming the transport stream are equal i.e.

* If the rate of encoder producing transport stream is **higher** than the consumption rate of set-top box. Buffer **overflow** will be happened on the set-top box, resulting video or audio data lost on TV
* If the rate of encoder producing transport stream is **lower** than the consumption rate of set-top box. Buffer **underflow** will be happened on the set-top box, resulting video get stalled on TV

In order to achieve same rate of running, the producer clock frequency must be equal to the consumer clock frequency, this can be done by synchronizing their clock by some timing protocol. In transport stream or the broadcast domain, this clock synchronization is done by the program clock reference (PCR). 

## Program clock reference (PCR)

The idea using PCR to synchronize the clock between upstream (e.g. encoder) and downstream device (e.g. set-top box) is like this. We can imagine each TS packet produced by the upstream device in **real time** will have the PCR value set to device's local time before sending to the network. The downstream device receiving these packets extract the PCR value and lock/synchronize to the upstream device clock frequency by phase lock loop (PLL) or some regression technique.

To help you sense the concept; here is an example

1. encoder at local time 10 produce first packet and mark the packet PCR = 10
2. encoder at local time 20 produce second packet and mark the packet PCR = 20
3. set-top box receive the first packet with PCR = 10 from upstream at local time 10
4. set-top box receive the second packet with PCR = 20 from upstream at local time 25

Base on 3 and 4, from set-top box's perspective

* the local time difference receiving first and second packet is 15
* the PCR time difference receiving first and second packet is 10
* i.e. set-top clock have advanced by 15 clock unit but upstream only advance by 10 clock unit as represented by the PCR difference

That means the set-top's local clock is running faster than encoder. In order to match upstream clock frequency, the set-top have to reduce the local clock frequency accordingly.

Eventually, the downstream device will have a clock synchronized to upstream in both **value** and **frequency**.

## Summary

In this article , we have gone though the idea in MPEG-2 Transport Stream to synchronize the clock between upstream and downstream via program clock reference (PCR). In the next article, we will talk about how presentation (PTS) and decoding timestamp (DTS) work base on the synchronized time base.

Thanks for reading. Please send me an email at povalab@gmail.com for any comment or questions. I am very happy to get feedkback from you.