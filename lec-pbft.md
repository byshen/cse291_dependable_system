# Practical Byzantine Fault Tolerance


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209140059.png)

### About the authors

Barbara is the founder of PDOS which recruited Frans K. and Robbert M.

Miguel Castro - Mark Weiser award winner

***This paper is a great example to show that the paper should tell the readers the assumptions upfront!***

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209140433.png)

How to reach an agreement in case of Byzantine Fault(BF).
- an agreement (liveness)
- can not have a bad plan (safety)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209140707.png)

In this case - 1 traitor in 3 generals is an impossible condition to tolerate BF.





![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209140811.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209140829.png)

**Intuition : n-f >= f+(f+1)**

The remaining 2f+1 nodes can still have an agreement.

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209140943.png)




### Why Practical?

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141137.png)

- Denial of service (no synchrony)
- Efficiency

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141208.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141239.png)

- Independent failure (one fail does not impact others)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141322.png)

Weak assumption of Adversary Model

- Can tolerate delay communication but not indefinitely


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141612.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141708.png)

- they have to use the synchrony for liveness. always need to make progress.

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141757.png)

Views is the configuration of all the replicas. for a certain view, the primary is determined by the quotient/remainder.


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209141940.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209142016.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209142111.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209142129.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209142243.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209142305.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209142651.png)

1. client request
2. pre-prepare
Pre-Prepare phase they receive the request and creates a proposal (think of it as the order they are formally putting down on paper with all the necessary details).

3. prepare
Prepare phase they are coming to an agreement.


4. commit only if (2f+1 receipts)

Commit phase, the name says it all, they commit their agreement and reply back. In addition they individually execute the request to check that they are getting the same results (to ensure the consensus property safety).

5. reply back to the client

### Why does PBFT divide into these phases?



### How to handle abnormal conditions?
![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209142856.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209143042.png)

- Rely on the synchrony to detect fault that does not broadcast

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209143137.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209143243.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209143518.png)

### Why do we need the commit phase?

In case of network delays, the view has changed, but the view-change message to the new primary may lost, then the remaining nodes can never reach an agreement and can not execute.

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209143729.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209144405.png)

Use another timeout to detect the new primary lost.

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209144509.png)

Optimizations to reduce the number of network messages

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210209144726.png)

Authentication to reduce the cryptographic calculations




Related read
- [A Byzantine failure in the real world](https://blog.cloudflare.com/a-byzantine-failure-in-the-real-world/)
- [http://ug93tad.github.io/pbft/](http://ug93tad.github.io/pbft/)
- [XFT: Practical Fault Tolerance Beyond Crashes， OSDI2016](http://vukolic.com/xft-osdi2016.pdf)


