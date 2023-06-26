Peer-related commands:
peer channel create: Create a new channel.
peer channel join: Join a peer to a channel.
peer channel update: Update the configuration of a channel.
peer channel list: List the channels a peer has joined.
peer chaincode install: Install a chaincode on a peer.
peer chaincode instantiate: Instantiate a chaincode on a channel.
peer chaincode upgrade: Upgrade a chaincode on a channel.
peer chaincode list --installed: List installed chaincodes on a peer.
peer chaincode list --instantiated: List instantiated chaincodes on a channel.
peer chaincode invoke: Invoke a transaction on a chaincode.
peer chaincode query: Query the ledger using a chaincode.
Orderer-related commands:
configtxgen: Generate the required artifacts (e.g., genesis block, channel configuration) for a Fabric network.
configtxlator: Perform various operations on Fabric configuration files.
orderer create: Create a new orderer node.
orderer start: Start an orderer node.
Fabric network management commands:
cryptogen: Generate cryptographic material (e.g., certificates) for the network.
configtxgen: Generate the network configuration and channel configurations.
configtxlator: Convert and manipulate Fabric configuration files.
configtxlator start: Start the configtxlator service.
configtxlator encode: Encode a configuration file.
configtxlator decode: Decode a configuration file.
configtxlator compute_update: Compute the difference between two configurations.
configtxlator sign: Sign a configuration file.
