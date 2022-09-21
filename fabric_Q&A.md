How many transactions are in the block?
It depends. There are several configuration options regarding the block size.
There is a BatchSize group of parameters: MaxMessageCount, AbsoluteMaxBytes and PreferredMaxBytes). The first one specifies the maximum number of transactions in the 
block, the latter ones set maximum and preferred block size.
Then, there is a BatchTimeout config parameter to specify how long the orderer should wait to form a block. Even if there are fewer transactions than specified by 
MaxMessageCount or other parameters, the block will be created after the specified amount of time. This value should be typically set to 1-5 seconds to keep the
responsiveness of the blockchain in case of low load.
Note that in some cases it is useful to set MaxMessageCount to 1. This is a quick and easy way to handle the key collisions problem in the networks that do not 
need high performance.

Block size scaling
The configuration of the Fabric can be done in many areas of the network. Enterprises
can decide for themselves the composition of peers by deciding how many endorsers,
committers and orderers that suits their use case. Furthermore, there is one parameter,
MaxMessageCount, that can be optimized to maximize throughput. This parameter tells
the orderer how many transaction that can be included inside a batch which is then sent to
committers to form the next block.

Endorser scaling Here we mainly focus on endorser scaling on the same channel. we concluded that adding endorsers on different channels would not have any impact on 
the performance of a channel. Therefore, we limit the test to a single channel.
The test is configured with a single client that uses 1 thread to send 1000 transactions to varied amount of endorsers and record the time taken for all transaction 
to be included in a block The most significant drop in throughput; from one endorser to two endorsers; is the most interesting part.

Finality

In Hyperledger Fabric, on the other hand, once a transaction is committed to the chain, it becomes final (absolute finality). There are no forks because the service
responsible for the consensus itself - the ordering service - is centralized and deterministic. Blockchain cannot be changed.

Best practice
If you can, increase the pool of available endorsing peers and load balance across that set to achieve greater TPS, improve latency or both. Note that transaction
latency is also a function of the time your chaincode takes to execute for an endorsement, so as noted above, YMMV.
Dealing with latency
Note that I haven’t mentioned latency until now. The reality is that as you scale the rate of transactions sent on a channel, you will likely reach a point where 
transaction latency becomes untenable because the peers become saturated consuming all the available CPU and/or disk i/o allocated to the container. For purposes 
of this set of experiments, I endeavored to keep the average latency under one second. We can actually scale beyond the TPS cited above if we are willing to 
tolerate additional latency, though with diminishing returns because while you may distribute the processing of endorsement across a set of available endorsers,
every peer that participates in a channel acts as a committer and must validate the transactions received from the ordering service.
Scaling Hyperledger Fabric
Another myth (or maybe it is FUD?) that I have heard recently is that Hyperledger Fabric limits the number of peer nodes in a network. I’m not sure of the source

of this myth, but nothing could be further from the truth! As a function of our system testing for a release, we kick off a scale test to ensure that we have not
introduced any changes that might affect performance and scale. Our testing creates a network comprised of 32 organizations each with four peers for resilience
(a total of 128 peers) and establishes a channel between each pair of organizations for a total of 325 channels — six of the organizations are configured as 
auditor or regulator nodes that observe each channel but do not perform endorsement.
 
Kafka vs Raft
kafka will come with additional baggage such as zookeeper & kafka itself and many complained about connection issues
kafka & raft are distributed consensus mechanisms, but raft is matured
