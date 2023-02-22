Hyperledger Fabric 2.5 beta version has been released with several updates and improvements, some of the highlights below:

The most notable feature of this release is the ability to purge the history of private data from a peer while preserving a hash of the private data 
as immutable evidence on the blockchain.

This feature allows for the deletion of private data on demand for privacy reasons or to adhere to government regulations.

It deletes private data from state and from a peer's private data history, preventing it from being queried from block events or other peers.

It is available as a new chaincode API PurgePrivateData() and requires setting the application capability to V2_5 in channel configuration.
