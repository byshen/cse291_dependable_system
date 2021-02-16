https://stackoverflow.com/questions/26589137/why-is-multi-paxos-called-multi-paxos

It's about multiple rounds of the algorithm to agree sequential requests from a stable leader with minimal messaging. Initially with no recognised leader you must run at least one round of basic Paxos where a candidate leader sends a prepare request (using the terminology of the paper Paxos Made Simple). Positive responses from a majority confirm it as leader. It then sends accept messages for that round which terminates successfully if you get a majority of accept acknowledgements. Rather than start again with prepare requests it can move immediately to a galloping mode where it sends successive accept messages when it hears a majority of acknowledgments for the previous accept request. This is highly efficient as it needs the minimal number of messages but it only occurs for multiple rounds from a stable leader. This may be interrupted by the leader crashing else a network failure which causes a follower to timeout on an otherwise healthy leader. It will then issue its own prepare request as a leadership challenge which is resolved via basic Paxos rules. As soon as you get a stable leader it can upgrade to multi-Paxos galloping mode.


https://www.youtube.com/watch?v=d7nAGI_NZPk

