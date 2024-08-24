---
title: "But what's database pooling?"
date: "2024-07-14"
summary: "What is Database pooling?"
description: "What is Database pooling?"
toc: false
readTime: false
autonumber: false
math: false
tags: ["docker"]
showTags: false
hideBackToTop: false
---
You might be aware that the word _pooling_ means sharing some resource with others, like _car pooling_. The concept is the same here. In database land, we share a bunch of open connections to the database with clients.

Usually, when a database is hosted on a remote server, you have to open new TCP connection for each query you make. Since opening a new TCP connection is costly (both in terms of time and CPU operations), and involves multiple steps, we try to reuse existing connections as much as possible. This is the core idea behind database pooling.

In database pooling, we maintain a set of open connections (from the web server) to the database to use them for different queries without the need for _cold starting_ new ones for different queues from different clients.

Here is a infographic depicting this concept, courtesy of [this](https://ejbvn.wordpress.com/category/week-2-entity-beans-and-message-driven-beans/day-09-using-jdbc-to-connect-to-a-database/) blog post.

![database pooling](/img/db-pooling.png)
