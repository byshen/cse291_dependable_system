Whova

SLI (monitoring metrics)
SLO (internal objectives)
SLA (customer promise)




At Uber

Micro-services:
- each repo is a service, modularity
- different tech stacks
- more than 3000 services



Service communication

HAProxy  + HTTP + JSON/REST
- Load balancing
- fixed port number for each service.

Muttley + http + Apache Thrift
- fine-grained traffic control
- dynamic service discovery?

- strict contract/type safety/faster transmission



Dual data center architecture
- fail over (one server down)

Consistency
- Use OLTP database (Sharded mysql, MySQL dual writer) (strong consistency)
- OLAP (HDFS/Hive) (eventual consistency)












