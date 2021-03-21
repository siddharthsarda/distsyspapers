## [A Note on Distributed Computing (1994) ](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.41.7628)

This paper from 1994 is mostly a critique of vision of object oriented computing which tries to hide the distinction between local member function calls and remote object invocations. The thesis of the paper is that while well meaning this aim is misguided as distributed computing is fundamentally different to ‘local computing’ in many ways.

In the vision of unified objects, writing a distributed application proceeds in the following three phases:

1. Write the application without worrying where objects are located. The focus is on hardening the interfaces between objects.
2. Concretize the object locations and communication methods.
3. Beef up the interfaces to deal with partial distributed systems failures and implement things like replication, transactions or whatever else is needed.

This desire to provide a comfortable abstraction to the programmer while trying to hide the undelrying communication paradigm is not new. This happened with messages, methods and objects.

The objects all the way approach is based on the following assumptions
* There is a single natural object oriented design for a given application, regardless of the context in which the application is deployed.
* Failure and Performance Issues are tied to the implementation of the components and should be left out of implementation design.
* The interface of an object is independent of the context in which the object is used.

The paper argues that these assumptions are incorrect and that the fundamental problems in distributed computing are not about marshaling and unmarshaling things on and off the wire.
They are rather around
* Latency 
Assuming that remote calls take the same amount of time as local calls leads to poor design.[2] 






1. One could say its happening now with graphs and GraphQL
2. Machine gun queries
