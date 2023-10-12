---
layout: post
author: Trey
title: The Quatraits of RxSwift - Part 1
tags: ["poetry", "rxswift"]
---

I arrived at Grindr in January of 2022 both knowing they had an [RxSwift](https://github.com/ReactiveX/RxSwift) tech stack and knowing that I did not know RxSwift itself.[^1] Never having used [functional reactive programming](https://en.wikipedia.org/wiki/Functional_reactive_programming) (FRP) before, I had to quickly reach highway speeds if I wanted to merge any pull requests. The [Kodeco book](https://www.kodeco.com/books/rxswift-reactive-programming-with-swift/v4.0) (née Wenderlich) on RxSwift helped immensely as did, of course, actually coding six to seven hours a day. But to truly guarantee I understood FRP's concepts and continued to retain them, I decided to combine my triple love of poetry, puns, and programming into a mnemonic: some didactic light verse. Emily Dickinson’s ballad style was the main inspiration for the format; its flexibility, humor, and concision was ideal for my purposes. 

This blog series is not intended to teach RxSwift fully but rather should solidify familiar concepts. Part 1 will contain the very basics of FRP. Part 2 will go over traits common across Reactive specifications. Part 3 covers the different flavors of Subjects. Part 4 delves into what is specific to RxCocoa and iOS.

[^1]: My team also knew this about me going in – one should be forthright with what they don't know in an interview. Learning new tech and reading docs is a coding constant and shouldn't necessarily be a hiring red flag. 

## The Basics of FRP

### "Consider the Observable"

a data stream – a Sequence – with  
immutability –  
asynchronous events comprise  
Observable of T –

to this Subscribe – receive direct  
data, done, or error –  
declared intent when you compose  
agnostic Operators –

onNext provides an Element –  
continues on – until –  
onError – onCompleted – ends  
the stream for all –

ensure the ended’s onDispose –   
its computers freed –  
otherwise well-architected   
we’ll leak – memory –  

### Explanation

In FRP, data is delivered over time downstream as a sequence of immutable Events. This concept is captured in an `Observable`. The data an `Observable<T>` passes down can be anything, hence the generic element T.[^2] 

[^2]: Realizing "Observable of T" and "immutability" both rhymed and had identical meter was the inspiration behind the poems.

Once an `Observable` has been created, the app can then subscribe to this `Observable` in order respond to a new event. These events are one of three types: an element, a complete, or an error. We also, after subscribing to the `Observable`, can perform a series of different non-mutating functional operators on the delivered data events, e.g., `map`, `filter`, `reduce`. Ideally, providing the series of operators at the call site results in future engineers knowing what is happening to the data (the "declaring intent"), but one should still leave a comment explaining Why the operations are being done to avoid potential misinferences. 

The subscription to an `Observable` will receive zero to many `T` elements during its lifetime and will continue to perform the operators we provided to it until one of three possibilites occur: the `Observable` returns an error, the `Observable` returns a complete, or the subscription's `DisposeBag` is emptied. Upon the first two of these, the subscription (and any others which subscribed to that same `Observable`) will no longer respond to any further elements provided. Emptying an instance of a `DisposeBag` will only dispose of the subscriptions that have been added to that instance.

Every subscription must be added to a `DisposeBag` for garbage collection and lifecycle purposes.[^3] If a subscription isn't properly disposed, then the observable objects and the downstream subscriptions will remain in memory and leak. Take a look at the memory graph in XCode after not including a `DisposeBag` to see for yourself.

[^3]: While not strictly true that EVERY subscription needs a `DisposeBag` (e.g., a one-and-done autocompleting subscription), my personal preference is to still add to the `DisposeBag` and avoid the ugly ambiguity of `_ = observable.subscribe()` in the code.

## One operator

### "Arizona-Lipton-Earl Grey"

source different streams – and bottle yours –  
in it the blending new –  
mixed Teas taste flat – Mapped all to One —  
but take it— and make do –  

### Explanation

This poem is the first one where allegorical imagery and wordplay are key to the mnemonic.[^4] The `flatMap` operator combines one or multiple data streams (the different flavors of `T`eas) into a single new `Observable` of a different data type altogether (the "bottle yours") . `.flatMap` keeps the same subscription whenever new `onNext` data arrives, unlike `flatMapLatest` which disposes first. `.map` changes the data but doesn't create a new `Observable`.

[^4]: I call poems like these Object-Oriented Poetry.

## Onward!

This first post introduced you to the basic concept of an `Observable` as well as one of its most used operators, `.flatMap`. Next, in [Part Two]({% post_url 2023-10-11-quatraitsPart2 %})  of this series, I will go over some Traits that all Reactive specifications use.






