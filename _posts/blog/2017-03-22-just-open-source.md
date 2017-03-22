---
layout: post
title: Just Open Source
date: '2017-03-22T22:10:00+00:00'
categories: blog
tags: [justeat, open-source]
image:
  feature: JustOpenSource.jpg
author: keith_moon
---

One of the advantages of working with Just Eat is their commitment to Open Source. As an iOS team at Just Eat we are always looking for ways to separate our code into useful, self contained components, and where possible, make them available to the community.

Recently I've been involved in open sourcing 2 Swift modules, with 1 more that can hopefully be open sourced soon.

## Just Persist

The ability to persist data is a key component for many apps, and all too often as your app grows in complexity, you find the implementation details of your persistence solution littered throughout your codebase.

This is not ideal. No matter which persistence solution you choose, Core Data, Realm, User Defaults, Keychain, to name a few, your requirements may change as your app grows. When you do need to change your persistence solution, unpicking all the related code is no small task. Testing can also be tricky, with complex persistence stacks needing to be setup and torn down.

JustPersist aims to provide a implementation agnostic interface to your persistence solution. By keeping your persistence layer behind the JustPersist interface, you ensure testability and the ability to swap out persistence solutions as your needs change.

Here this the [Just Eat tech blog post](https://tech.just-eat.com/2017/03/02/how-to-abstract-your-persistence-layer-and-migrate-to-another-one-on-ios-with-justpersist).

[JustPersist can be found on GitHub](https://github.com/justeat/JustPersist)

## Just Promises

A key non functional requirement if any app is that it is quick, smooth and responsive. To achieve this, you will be frequently working with asynchronous code. Grand Central Dispatch is great, but jumping back and forth between queues can easily become unwieldy with nested blocks.

JustPromises is a framework for doing asynchronous work, based on the "promise" concept, popular in JavaScript. JustPromises is used used heavily in the Just Eat app, and was written in Objective-C a few years ago. As we move more and more of the Just Eat app to Swift 3, the Objective-C interface of JustPromises was really showing it's age. So I undertook to rewrite it in Swift 3.

Doing a full rewrite enabled me to take full advantage of Swift's generics system and other advanced Swift features. It also allowed me to tidy up the conceptual model and base the ```Promise``` on ```Operation``` (formally ```NSOperation```), since handling a long running task is exactly what ```Operation```s are built for.

Here is the [@justeat_tech](https://twitter.com/justeat_tech) @justeat_tech twitter account, announcing the release:
https://twitter.com/justeat_tech/status/805746214356611076

JustPromises is available in Objective-C, Swift or both, from [GitHub](https://github.com/justeat/JustPromises) or [Cocoapods](https://cocoapods.org/?q=JustPromises)

## Other iOS Open Source

The rest of the Just Eat iOS team have also been busy contributing to the open source community

### Just Track

JustTrack is an event tracker.

* Events are declared in a .plist file and Swift 3 code is automatically generated at build time from it.
* Events can be sent to multiple destinations (called Trackers) at the same time.
* Custom Trackers are easy to create and use.

[JustTrack Blog Post](https://tech.just-eat.com/2017/02/01/ios-event-tracking-with-justtrack/) - [JustTrack GitHub Page](https://github.com/justeat/JustTrack)

### Just Log

Remote logging to multiple providers from one interface.

[JustLog Blog Post](https://tech.just-eat.com/2017/01/18/a-better-local-and-remote-logging-on-ios-with-justlog/) - [JustLog GitHub Page](https://github.com/justeat/JustLog)

### Just Peek

JustPeek ports Force-Touch Peek/Pop-like interactions to devices that aren’t force-touch enabled.

[JustPeek Blog Post](https://tech.just-eat.com/2016/12/01/introducing-justpeek/) - [JustPeek GitHub Page](https://github.com/justeat/JustPeek)
