---
layout: post
title: "FPU: Introduction to Designing a Floating Point Unit based on IEEE 754"
date: 2024-09-18
tags: stm32, testing
author: Kevin Caldwell
---

## Introduction

A Floating Point Unit (FPU) for a compute device is a module that operates on
floating point values. It allows a computer to compute non-integer values.

The Main Arithmetic for Floating Point Values include

- Addition $(x + y)$ and Subtraction $(x - y)$
- Multiplication $(x * y)$ and Division $(x / y)$
- Square Root $( \sqrt{x} )$
- Exponents $(x ^ y)$ and Logarithms $ \log_{b}{x} $
- Fused Multiply Add $(x * y + z)$
- Convert From Int $(x_{int} \rightarrow x_{float})$

## Format

| Sign | Biased Exponent | Significand |
