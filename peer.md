Peers

Peers are the fundamental components of any Fabric network. 

Peers store the blockchain ledger and validate transactions before they are committed to the ledger. Peers run the smart contracts that contain 
the business logic that is used to manage the assets on the blockchain ledger.

A peer may belong to one organization and multiple channels. It is responsible for keeping the ledgers and chaincodes.

A ledger consists of two parts: a log of transactions (blockchain) and a state database (world state). All peers in the channel have their 
own copy of the ledger. 

If a peer belongs to multiple channels, it has multiple ledgers, one per channel.

Aside from keeping the state, a peer keeps and manages chaincodes. This is a broader concept than the smart contract itself. Smart contracts are packaged 
as a chaincode. Thus, the chaincode is a bundle that, among others, contains smart contracts.

Peer types
First, there are anchor peers - peers that are available outside the organization. Any cross-organization communication requires anchor peers. They play a significant role in the service discovery - they discover the network and they might be discovered from other organizations. In the transaction flow diagram above, anchor peers are peer 1 and peer 3. It is written in configtx.yaml file.
Then, at the simulation phase of the transaction, the smart contract is executed in endorsing peers. In the transaction flow diagram above, 
endorsing peers are peer 2 and peer 3.

When the transaction is ordered, the ordering service delivers new blocks to leading peers and they distribute it further in the network. 
In the transaction flow diagram above, leading peers are peer 2 and peer 3.

Finally, committing peers append all new transactions to their own copy of the ledger. All peers in the channel are committing peers.

