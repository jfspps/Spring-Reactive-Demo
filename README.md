# Reactive programming with Java and Spring

This example was followed along from SpringframeworkGuru. Below is a little about the underlying components of reactive programming as applicable to Spring. Reactive programming is a `non-blocking` execution of independent, asynchronous tasks. It is expressed with four keywords: Responsive, Elastic, Resilient and Message Driven.

A `Publisher` object (given by an interface) is a provider of sequenced elements to one or more `Subscriber` objects (which consume elements). Such sequences are referred to as 'streams' of data. The construction of each element is implemented via a Factory pattern and can be called more than once. Subscribers can only subscribe to one Publisher.

Publisher has subscribe() which starts streaming data. A Publisher with zero or one element in the stream is termed a `Mono`. A Publisher with zero or more than one element is referred to as a `Flux`.

Subscriber has four methods: onSubscribe(), onNext(), onError() and onComplete(). 

The link between the Publisher and Subscriber is a `Subscription` interface. This facilitates a one-to-one lifecycle which can only used once. The methods available to this interface are request() and cancel().

The processing stage is handled by the `Processor` interface and is both a Subscriber and Publisher in character.

The Publisher offers a Subscription. The subscriber then requests to subscribe to the subscription. This initiates a reactive stream between the Subscriber and Publisher (via the Subscription). The flow rate is characterised by a 'back pressure' whereby the Subscriber is only fed as much data as it needs and signals to the Publisher how much to send through a back-pressure mechanism. The Subscriber sends messages which the Publisher can monitor.