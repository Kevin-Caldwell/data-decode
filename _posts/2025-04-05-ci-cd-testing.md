---
layout: post
title: "CI/CD Testing: Github Actions vs. Jenkins"
date: 2024-07-15
tags: build-tools
author: Kevin Caldwell
---

## CI/CD

According to [GitLab](https://about.gitlab.com/topics/ci-cd/), CI (Continuous 
Integration) is "the practice of integrating all your code changes into the main
branch of a shared source code repository early and often, automatically 
testing each change when you commit/merge them, and automatically kicking off a 
build. With CI, errors and security issues can be identified and fixed more
easily, and much earlier in the development process."

Similarly, [the same article](https://about.gitlab.com/topics/ci-cd/) also 
describes CD as the "software development practice that works in conjunction
with CI to automate the infrastructure provisioning and application release
process".

While CI/CD is commonly used for application and web development, it plays a 
significant role in testing embedded software as well. CI makes sure the code 
is frequently checked for bugs and errors, meets the target requirements, 
and can also test firmware on the hardware with a Hardware in the Loop (HIL)
setup.

A typical CI/CD pipeline has been described in [this article]
(https://www.embedded.com/how-to-define-your-ideal-embedded-ci-cd-pipeline/), 
and consists of the following tasks:

*CI:*
1. Build
2. Analysis
3. Testing
4. Reports

*CD*
5. Merge 
6. Deploy

There are several software solutions available for highly customizable, 
scalable and easy-to-use CI/CD pipelines, including but not limited to
GitHub Actions, Jenkins and BitBucket.

## Acknowledgements

This article aims to compare the effectiveness of GitHub Actions and Jenkins 
as a CI/CD software solution for spacebound embedded systems for the FINCH
Mission at the University of Toronto Aerospace Team's Space Systems Subdivision.

## Embedded Setup

Although the tests conducted will be platform-independent, the same tasks are 
used in most embedded ecosystems.

For the STM32 Environment, ST provides CLI tools for compiling and uploading
code to their boards. STM32CubeMX is used for generating new projects, 

For the Zephyr Environment, building a project is done using 
the `west build` command, flashing a binary onto an MCU is done using the 
`west flash` command and unit testing can be written using 
[ztest](https://docs.zephyrproject.org/latest/develop/test/ztest.html) and
executed on the 
[twister](https://docs.zephyrproject.org/latest/develop/test/twister.html) tool.

## GitHub Actions

GitHub Actions, developed by GitHub (shocker, I know...) for CI/CD in Git 
Repositories. It is highly customizable, easy to automate and maintain 
software development workflows.

Each pipeline is specified by a Workflow, a configurable autmated process, 
specified by a YAML file, and run when triggered by an event in respective 
GitHub repository, Scheduled Times, manually, or customized in the YAML file.

Each Step in the pipeline is called a `Job`, and executed on a `Runner` machine.
This implies that different Jobs can be run on different machines, although not 
verified at the time of writing this article. 

The Job can be specified inside the YAML file using the YAML syntax, which 
includes the ability to run a shell script for processes that require more
complex logic.

GitHub Actions also provides a convenient and visual way of representing
the progress of an active workflow through a graph view found on the GitHub
website under the Actions page. This can be a useful tool for checking the 
status and log files of current and previous builds, and the control flow
of the pipeline.

It is a widely used tool, and is being used to compile and deliver this website!


## Jenkins

"Jenkins is a self-contained, open source automation server which can be used to
automate all sorts of tasks related to building, testing, and delivering or 
deploying software".

The Jenkins UI is found by opening [localhost:8080](localhost:8080) on a 
browser. This will take you to a dashboard, with a much similar User Interface
to GitHub Actions. 


## Benchmark

In order to compare the performance of both CI/CD tools, a project needs to
be created that tests a full pipeline. For GitHub Actions, while it usually
runs on the cloud, it is important to test a pipeline running locally as well.

This is important for embedded systems as HIL testing is usually done on a 
local server. 

> Add stuff here about embedded build and testing software either being 
> proprietary or GitHub Actions does not readily support it.

Keeping in mind the intended projects of the FINCH Mission's Firmware Projects,


## Results

