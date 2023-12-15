---
layout: post
author: Trey
title: The Quatraits of RxSwift - Part 3
tags: ["poetry", "rxswift"]
---

In [Part Two]({% post_url 2023-10-11-quatraitsPart2 %}) of this series, I went over four different `Trait`s used in RxSwift.

Now, Part Three will go over four kinds of `Subject`s : `BehaviorSubject`, `AsyncSubject`, `PublishSubject`, and `ReplaySubject`.


## Subjects
A base `Subject` can receive and send events, acting as both observer and observable, but we still need some concrete classes of `Subject`s to resolve some ambiguities and add some additional constraints and behaviors. 

### "Born This Way"

Behavior’s an inborn nature —  
then reflects current events —  
you see One at their worst — or best —  
watch their latest contents —  

### Explanation

`BehaviorSubject`s, upon being subscribed to, emit either a) an initial value provided on `init` or b) the most recent received event. They're useful for acting as the backing private `BehaviorSubject<T>` for an exposed public `Driver<T>`[^1].

[^1]: We don't actually want a `BehaviorSubject` for the backing variable, but rather a `BehaviorRelay`. `Relay`s will be gone over in Part 4.

### "Wash Your Hands When Finished"

A sink retains the latest stream –  
seen only when its stopped –  
unplugged – A sink’s an endless pipe –  
(Well, endless but when clogged!). 

### Explanation

An `AsyncSubject` can receive any number of `onNext` events and won't emit any of them until it receives a `Complete` event. After this `Complete`, then and only then will the `AsyncSubject<T>` emit to all of its observers the last `T` received. This `Subject` is useful for one-and-done GET API calls.

### "Self-Published"

pre-gutenberg: an empty shelf –  
no written memory –  
now: Publish books for each event –  
tapped Subjectivity –  

### Explanation

Ignoring that books existed before the printing press (but for the average person, their bookshelf was bare), a `PublishSubject<T>`, as opposed to a `BehaviorSubject`, will not provide a default or last received `T` on subscription. Instead, a `PublishSubject` will emit each new one, not bothering to remember the previous. They're useful for acting as the backing private `PublishSubject<T>` for an exposed public `Signal<T>`[^2].

[^2]: See supra re: `Relay` for `PublishRelay`.

### "Deja Entendu" 

“Now – what’d you say? I couldn’t hear.”  
“I’ll tell what I recall.  
New words come out, I lose what was.”  
Some speech replayed – not  

### Explanation

A `ReplaySubject` is a souped-up `BehaviorSubject`. Whereas a `BehaviorSubject` will emit only the initial/latest value, a `ReplaySubject` contains a buffer (the max capacity determined on `init`) of received `T`s and emits, upon being subscribed to, this buffer. This buffer might also have a time window also, so events received outside a certain duration are removed from the buffer. Unlike `BehaviorSubjects`, a `ReplaySubject` doesn't have an initial `T` and will return its buffered values even after an error.

## Onward!

This third part introduced you to different kinds of `Subjects` in Reactive programming. Next, in Part Four of this series, I will go over some traits that are exclusive flavors of RxCocoa.






