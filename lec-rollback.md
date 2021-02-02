# a survey of rollback -recovery protocols in message-passing systems


Goal - add reliability and high availability 


rollback recovery - LONG RUNNING systems


How to take checkpoints?



what is a consistent system state?
- if a process's state shows a message is received, the corresponding sender's state must shows that the message has been sent.


Interactions with outside world

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202141714.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202141904.png)




Checkpoint based recovery

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202141957.png)



How to calculate the recovery line?
- dependency based
- checkpoint graph


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202143201.png)



![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202143227.png)





Non-blocking checkpointing coordination

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202143451.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202143637.png)



Communication-induced checkpointing


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202143918.png)

Log-based rollback recovery

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202144125.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202144602.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202144635.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202144820.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202144900.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210202145151.png)



why this thing is not used?

- design task based checkpointing? If a task fails, just redo it?
- how to scale? how to coordinate a thousand machines' checkpoints? it's really hard to implement such complex recovery protocols in real life
- application will implement their own checkpointing mechanism, what they want to make it durable.