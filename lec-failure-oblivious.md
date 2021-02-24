# Enhancing server availability and security through failure-oblivious computing


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223140738.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223141039.png)

Assumption - 
1. you can insert bounds checking in the code - then exit if exception - cause server crash
2. BUT they can launch DDoS attacks

So if the requests do not steal information, just let it go. It's okay to return a bogus value.

Questions:
1. How to guarantee the error will not propagate? Will it affect the following services.
2. This violates **FAIL-STOP**. 
![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223150141.png)
![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223141111.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223141144.png)

Security vulnerability - e.g., DDoS

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142106.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142256.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142334.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142416.png)


what does this mean?

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142527.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142659.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142900.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223142955.png)


![](https://raw.githubusercontent.com/byshen/picrepo/master/20210223143219.png)






