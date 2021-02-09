# Implementing fault-tolerant services using the state machine approach: a tutorial

Assumption about the request order


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210204140601.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210204140729.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210204140916.png)



The happens before relation (<) is defined as follows.
1. If a, b are events in the same process, if a occurs before b, then a < b
2. if a denotes sending of message in process-a and b denotes receipt of message in process-b then a < b
3. The relation is transitive, a < b and b < c => a < c



## Logical clock (Lamport clock)

1. It’s a counter within a single process that increments from 1. Events within a process is assigned an unique id based on the counter value. Thus all compute and messaging events within a process are assigned an unique value
2. When sending a message from process-a, we set C(a) = C(a) + 1, then pass on C(a) as part of the message.
3. On recipient of message in process-b we set C(b) = max(C(b) + 1, C(a))

> update the clock when the two server exchanges info - indicate the happen-before relationship

***Lamport clocks can guarantee that if a < b then C(a) < C(b). However it can’t guarantee, that if C(a) < C(b) then event a happened before b.***


## Vector Clock

In a system with N processes, each process keeps a vector timestamp TS[N]

1. In Process i,
    a. TS[j] is logical time of process j as process i knows about it.
    b. TS[i] is the lamport clock of process i.
2. When a new event is generated, TS[i] = TS[i] + 1
3. When sending a message we copy the vector clock to the message
4. On recipient of message with vector timestamp MTS we set the TS of process i as,
TS[k] = max(TS[k], MTS[k]) for k = 1 to N


The happened before ordering in vector clocks is defined as follows.

**e1 < e2 iff TS(e1)[k] <= TS(e2)[k] for k = 1 to N**
* at least one of the value of indices of e1 should be less than e2’s value


***When there are a large number of processes this technique can become extremely expensive, as the vector sent is extremely large.***

Optimizations to Vector clock:
* Singhal–Kshemkalyani’s differential technique: This approach improves the message passing mechanism by only sending updates to the vector clock that have occurred since the last message sent from Process(i) → Process(j). 
* Fowler-Zwaenepoel direct-dependency technique 

## TrueTime
In Google Spanner, it uses TrueTime API to fix the problem of time. Spanner uses GPS and Atomic Clock to correct the time and can guarantee clock uncertainty bound (ε) is very small. 

Because TrueTime has the clock uncertainty bound ε, so for every transaction commit, it must wait 2ε time to guarantee linearizability, but ε is so small that the performance is still high.

***The biggest hurdle to adopting TrueTime is that it depends on special hardware, such as GPS clocks and atomic clocks, which many companies do not have.***

## Timestamp Oracle (TSO)


The timestamp oracle is a server that hands out timestamps in strictly increasing order. Since every transaction requires contacting the timestamp oracle twice, this service must scale well. The oracle periodically allocates a range of timestamps by writing the highest allocated timestamp to stable storage; given an allocated range of timestamps, the oracle can satisfy future requests strictly from memory.

> Large-scale Incremental Processing
Using Distributed Transactions and Notifications, OSDI 2010

***Using TSO to allocate timestamp is simple, but it has the following disadvantages***:

1. Single point of failure (Maybe handled by consensus protocol like Raft)
2. Network latency (hard to scale across data centers)



References

[https://tikv.org/blog/time-in-distributed-systems/](https://tikv.org/blog/time-in-distributed-systems/)
[https://medium.com/@balrajasubbiah/lamport-clocks-and-vector-clocks-b713db1890d7](https://medium.com/@balrajasubbiah/lamport-clocks-and-vector-clocks-b713db1890d7)



