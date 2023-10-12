---
layout: post
author: Trey
title: The Quatraits of RxSwift - Part 2
tags: ["poetry", "rxswift"]
---

In [Part One]({% post_url 2023-09-27-quatraitsPart1 %}) of this series, I provided the mnemonic poems I used to help learn and retain the basics of Reactive programming, specifically `Observable`s and one operator (`flatMap`) in `RxSwift`.

Now, Part Two will go over three different `Trait`s that an `Observable` can be: `Single`, `Completable`, and `Maybe`.

## Traits
A `Trait` is an `Observable` but with its own specifications and limitations and uses beyond the broader `Observable`. These shared `Trait`s allow for consistency across Rx implementations (RxJava, RxSwift, RxKotlin, etc.) and enable easier cross-platform communication and guarantees certain properties. `Traits` are largely just syntactical sugar and interfaces atop the underlying `Observable`.


### "All The Single Clades"

a Single has one guarantee:  
an element or wrong –  
if eventS emit, error –  
error fore’er long –  

### Explanation

The base `Observable`, as mentioned in part one, may produce multiple elements over its lifetime. A `Single`, however, as the name implies, will only ever provide 1 `T` element (if it produces an element at all). A `Single`, then, combines both its `T` element and its `onComplete`. A `Single` still can produce an Error instead of an element. `Single`s are very useful for API calls, e.g., downloading an image, and the 1-element or 1-error nature maps nicely to different API status codes (200 + an element or maybe a 404 + an error). This `Trait` will be one of the most common ones you will use in RxSwift.


### "Mission: Completable"

Completable is Never less  
than Success or Not –  
credit – for cache or when E’er —  
a zero-one is sought  —  

### Explanation

Unlike the `Single` above, `Completable`s do not provide any elements or data. It returns either the `onComplete` or an`onError`. A `Completable` is useful when the app only cares about whether an action was done or could not be done. For instance, `Completable` is the goto `Trait` for updating caches. The app doesn't necessarily need to know what's in the cache, so returning an Element is overkill. All the app cares about is that the cache was successfully updated (or not). This also works for other API calls like POSTs or DELETEs where all that matters is seeing that pretty `200` status (or errors). 

`Completable`s also nicely chain together with `.andThen` operators, allowing for declarative programming. Very useful in your `AppDelegate` setup methods if you need initializations or API calls performed in a specific order. 

### "Three Times A Maybe"

a Maybe’s yes, yes and, or no —  
it can Complete alone —  
it can complete returning One —  
it can own an Error —   

### Explanation

A `Maybe` is like a `Single` combined with a Swift `@discardableResult` or a `Completable`. `Maybe` will have one of three possibilities: an `onComplete`, a `success` with `T` element, or an `onError`. It's used when you could want the element but not necessarily need to have an element returned. For instance, fetching a value from a cache. The `Maybe` trait is not one I used too often in my day-to-day programming. I... actually don't think I ever used it at all myself...

## Onward!

This second part introduced you to some `Traits` of `Observable`s in Reactive programming. Next, in part 3 of this series, I will go over some more intense `Subject`s in RxSwift.






