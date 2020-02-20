# Getting Started With RxSwift and RxCocoa

## RxSwift and RxCocoa

RxSwift is a framework for interacting with the Swift programming language,
while RxCocoa is a framework that makes Cocoa APIs used in iOS and OS X easier
to use with reactive techniques.

ReactiveX frameworks provide a common vocabulary for tasks used repeatedly
across different programming languages. This makes it easy to focus on the syntax
of the language itself rather than figuring out how to map a common task to
each new language.

## Observables and Observers

Two key concepts are the Observable and the Observer.

- An Observable emits notifications of change.

- An Observer subscribes to an Observable and gets notified when that Observable has changed.

You can have multiple Observers listening to an Observable. When the Observable changes, it will notify all its Observers.

## The DisposeBag

The DisposeBag is an additional tool RxSwift provides to help deal with ARC and memory management. Deallocating a parent object results in the disposal of Observer objects in the DisposeBag.

When deinit() is called on the object that holds the DisposeBag, each disposable Observer is automatically unsubscribed from what it was observing. This allows ARC to take back memory as it normally would.

Without a DisposeBag, you’d get one of two results. Either the Observer would create a retain cycle, hanging on to what it’s observing indefinitely, or it could be deallocated, causing a crash.

To be a good ARC citizen, remember to add any Observable objects to the DisposeBag when you set them up. The DisposeBag will clean up nicely for you.

## Where to Go From Here

Try adding a couple things to make this application even more reactive:

- Change the CartViewController to use a reactive table view (instead of a label) to display the contents of the cart.

- Allow the user to add or remove chocolates directly from the cart, automatically updating the price.
