
## What is dependability?

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210107140547.png)

## Faults, Errors Failures

- failure is perceived by the users
- Error : some wrong internal states that are not perceivable by the users
- Fault : the cause of the error (e.g. BUG)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210107141035.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210107142719.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210107144244.png)

Crash is good some times - avoid corrupt larger services  through the error propagation.

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210112140418.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210112140930.png)

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210112141737.png)

Fault prevention: 
- periodically reboot to prevent resource leak

Fault tolerance:
- mechanisms to handle failures

Fault removal:
- remove fault before release

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210112142148.png)

Reliability: Mean Time To Failure
Maintainability: Mean Time To Repair 
Availability: available time percentage

![](https://raw.githubusercontent.com/byshen/picrepo/master/20210112142640.png)