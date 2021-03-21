## [A Note on Distributed Computing (1994) ](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.41.7628)

This paper from 1994 is mostly a critique of vision of object oriented computing which tries to hide the distinction between local member function calls and remote object invocations. The thesis of the paper is that while well meaning this aim is misguided as distributed computing is fundamentally different to ‘local computing’ in many ways.

In the vision of unified objects, writing a distributed application proceeds in the following three phases:

1. Write the application without worrying where objects are located. The focus is on hardening the interfaces between objects.
2. Concretize the object locations and communication methods.
3. Beef up the interfaces to deal with partial distributed systems failures and implement things like replication, transactions or whatever else is needed.
This desire to provide a comfortable abstraction to the programmer while trying to hide the undelrying communication paradigm is not new. This happened with messages, methods and objects.<sub>1</sub>

The objects all the way approach is based on the following assumptions
* There is a single natural object oriented design for a given application, regardless of the context in which the application is deployed.
* Failure and Performance Issues are tied to the implementation of the components and should be left out of implementation design.
* The interface of an object is independent of the context in which the object is used.

The paper argues that these assumptions are incorrect and that the fundamental problems in distributed computing are not about marshaling and unmarshaling things on and off the wire.
They are rather around
* Latency
  
  Assuming that remote calls take the same amount of time as local calls leads to poor design of distributed applications<sub>[2]</sub>. However latency is only the   most obvious of issues. There are more irreconciable differences in doing distributed computing. 
* Partial Failure and Concurrency

  In distributed computing unlike local computing, failures can be partial. In local systems failure is either total affecting all application or detectable by a central allocator such as an operating system. Failures in distributed computing are non deterministic. A key challenge in distributed computing is that the state of the whole system is consistent after a partial failure. Remote programming interfaces should be designed in a way that they can respond to partial failures and recover to a consistent state [sub]3[/sub]. 

The other concern mentioned is the difference in memory access between local and distributed computing. 

1. Reading this section really made me think of GraphQL and of all the proponents of Graphs all the way down. 
2. N + 1 Query problem or machine gun queries are a good example.
3. This actually holds true very well. Status codes exist for both http and grpc communication methods. Service meshes have evolved to make the concerns of remote communication even simpler.  
