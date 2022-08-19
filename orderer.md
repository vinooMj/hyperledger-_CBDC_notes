Orderer
An ordering service allows peers to focus on validating transactions and committing them to the ledger. 

Order the transactions
Cut the block and distribute the block amongst the orgs when the criteria is met ( min txn/size or time).
 
orderer whose is responsible for receiving endorsed transactions from peers and put them into blocks then these blocks are distributed to all peers. These blocks are Final.

Raft Consensus for production network

The problem is that both mechanisms (Kafka and Raft) are only crash fault tolerant. It means that the ordering service should be centralized (at least at the channel level) and governed by a trusted organization. Taking over the orderer nodes and serving malicious content to different peers can lead to corrupted blockchain.

CFT and BFT
CFT (or crash fault tolerance) means that a distributed system can operate normally even when a number of nodes fail. BFT (or Byzantine fault tolerance) means that a distributed system can operate normally even when a number of nodes lie.
BFT is crucial when many organizations cooperate. It is in the interest of all organizations to be resistant to malicious actions of the other ones. With proper endorsement policies and the ordering service managed by a trusted organization, the Hyperledger Fabric network might be considered BFT at the organization level. Even when an organization lies, the state won't corrupt.

The sample network uses a single node Raft ordering service that is operated by the orderer organization. You can see the ordering node running on your machine as orderer.example.com. While the test network only uses a single node ordering service, a production network would have multiple ordering nodes, operated by one or multiple orderer organizations. The different ordering nodes would use the Raft consensus algorithm to come to agreement on the order of transactions across the network.

Their design allows different organizations to contribute nodes to a distributed ordering service.

Raft protocol uses a “leader and follower” model.

General orderer count is five. 

At least 1 orderer in your HLF network to work.	

Not every peer needs to be connected to an orderer - peers can cascade blocks to other peers using the gossip protocol.

Query is not a transaction which writes into the ledger. So it doesn't need the orderer. For query, it will pick up the data from the peer's local 
database.

Orderer organization
The orderer organization might be separated from the root organization. This is the organization that manages the orderer nodes. It is responsible 
for keeping the data consistent and generating blocks of ordered transactions that form a blockchain.
In some cases the orderer nodes might be distributed among other organizations. It might be required in your deployment, however it is also risky 
in terms of the performance and maintaining trust in the network. The orderer organization, as well as the root organization, should be governed by 
an authority with the highest trust in the network.

Orderer genesis block is the genesis block for the system channel as it is the basic configuration block for the network. It a special channel managed 
by the orderer admins which includes a list of the organizations permitted to create channels.
The genesis block of the orderer system channel is special: it must be created and included in the configuration of the node before the node can be 
started.

Orderer Count:

While it's possible to use the console to build a configuration of any number of ordering nodes (no configuration is explicitly restricted), some 
numbers provide a better balance between cost and performance than others. The reason for this lies in satisfying the needs of high availability (HA) 
and in understanding the Raft concept of the "quorum", the minimum number of nodes that must be available (out of the total number) for the ordering 
service to process transactions.
 
In Raft, a majority of the total number of nodes is needed to form a quorum. In other words, if you have one node, you need that node available to 
have a quorum, because the majority of one is one. Similarly, if you have two nodes, you will need both available, since the majority of two is 
two (for this reason, a configuration of two nodes is discouraged; there is no advantage to a two node configuration). In a similar vein, the majority 
of three is two, the majority of four is three, the majority of five is three, and so on.
 
While satisfying the quorum will make sure the ordering service is functioning, production networks also have to think about deployment configurations 
that are highly available (in other words, configurations in which the loss of a certain number of nodes can be tolerated by the system). Typically, 
this means tolerating two nodes failing: one node going down during a normal maintenance cycle, and another going down for any other reason 
(such as a power outage or error).
 
This is why five nodes is a good number for a production network. Recall that the majority of five is three. This means that in a five 
node configuration, the loss of two nodes can be tolerated. If your configuration features four nodes, only one node can be down for any reason 
before another node going down means a quorum has been lost and the ordering service will stop processing transactions.
 
It should be odd number(3, 5 , 7 9)
 
Orderer org or every org has orderer depend on your usecases.
 
Ex:
 Three orderer peer
 
I have solved this in such a way that in my case I have three orderers that run independently on different environments. If I crash all these orderers, 
the peer containers will continue to run on the other participants of the network. As you said, they cannot make any transactions. If one of my orderers 
crashes it is not so bad after the raft consensus, the containers keep running. If another one fails, no transactions can be made. In this case I let
the peers continue and check if the orderers are available again.
