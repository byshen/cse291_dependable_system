

## redundancy



## fault isolation




## clock synchronization

tolerate byzantine fault
（arbitrary fault）
- need at least 3M+1 to tolerate M faults


basic algorithm:
- each transfer the view of all other nodes (cons : a lot of communication overhead to
        reach a consistent view)



## fault detection and reconfiguration

- fault detection (paxos)
- reconfiguration (no tasks assigned to failed nodes)
 


## validation and verification

- the markov probability model meets the reliability requirements
- `(h,d,f)` to node the handled, detected, and faults

`(h,d,f)` ->`(h,d,f+1)` means meet new fault
`(h,d,f)` -> `(h,d+1,f)` means detect one new fault

build a state transition graph, 
how likely it is to reach a unsafe state?

