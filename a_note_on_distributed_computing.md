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

The paper goes on to discuss the NFS filesystem as a way to illustrate the difficulties in working with distributed systems. NFS implements the same API as a non distributed file system (open, read, write, close). While in non distributed file systems, failures (disk full, crash) are rare, in NFS this is something actively to be dealt with. NFS has two ways of dealing with an inaccessible file server.

* Soft Mounts: In this mode, network or server failure is exposed to the client.
* Hard Mounts: In this mode the application hangs until the server failure is resolved.

As an observation even then you could see the tradeoffs between safety (nothing bad ever happens) and liveness (something good eventually happens). Also you can clearly see that network failures or partition (as described in CAP theorem) is unavoidable. Surprisingly at that time, the preferred option was to use the hard mount option, which often required the intervention of a human actor to resolve issues.

The paper exhorts to take the differences between distributed computing and local computing seriously by giving distributed objects the special attention that they require.

### My Observations

It’s an approachable read. You could also see how even some of the current developments (for example service meshes) are an attempt to tackle the same difficulties in distributed systems that are raised in the paper. It also illustrates the problems in distributed computing with an example of NFS. It’s interesting that you could see the tug of war between safety and liveness even then. Fairly quick easy read.


[1] Reading this section really made me think of GraphQL and of all the proponents of Graphs all the way down. 
[2] N + 1 Query problem or machine gun queries are a good example.
[3] This actually holds true very well. Status codes exist for both http and grpc communication methods. Service meshes have evolved to make the concerns of remote communication even simpler.  
