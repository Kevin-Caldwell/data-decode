---
layout: post
title: "Automated Remote Test Bench for STM32"
date: 2024-05-07
tags: stm32, testing
author: Kevin Caldwell
---

The concept of Continuous Integration has more prominent in the Embedded World, but is 
difficult to accomplish due to the constraints of testing on the target hardware. 

This blog post dives into the process required to set up an automated test bench, where
STM32 code can be run remotely, and accessing it only requires a GitHub Repository.

# Requirements
The Hardware required for the Server side is
- A Computer capable of running Linux
- A USB hub for connecting to ST-Link
