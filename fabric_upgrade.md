In Hyperledger Fabric, the specific commands used to upgrade components of a running network may vary depending on the version of Fabric being used. However, 
the general process for upgrading a network usually involves:

Backup certs, ledger, msp

Preparing the new component version: This involves creating a new version of the component to be upgraded, such as a new chaincode or orderer binary, and ensuring 
that it is compatible with the existing network.


Staging the upgrade: This involves testing the new component version in a staging environment to ensure that it works as expected and that there are no compatibility 
issues with the existing network.

Performing the upgrade: Once the new component version has been tested and is ready, the upgrade can be performed on the running network using the appropriate upgrade
command.

Some specific upgrade commands that may be used in different versions of Hyperledger Fabric include:

Fabric v1.4: The peer chaincode upgrade command can be used to upgrade chaincode on peer nodes, and the configtxlator proto_encode and peer channel update commands
can be used to upgrade the channel configuration.

Fabric v2.0: The peer lifecycle chaincode approveformyorg and peer lifecycle chaincode commit commands can be used to upgrade chaincode on peer nodes, and 
the configtxlator proto_encode and peer channel update commands can be used to upgrade the channel configuration.

Fabric v2.2: The peer lifecycle chaincode approveformyorg and peer lifecycle chaincode commit commands are still used to upgrade chaincode, and a new peer channel
signconfigtx command can be used to upgrade the channel configuration.

Fabric v2.3: The peer lifecycle chaincode approveformyorg and peer lifecycle chaincode commit commands are still used to upgrade chaincode, and the configtxlator
proto_encode and peer channel update commands have been replaced by the configtxlator encode and configtx update commands for upgrading the channel configuration.

It is important to consult the appropriate documentation for the version of Fabric being used to ensure that the correct commands and procedures are followed for
upgrading a network.



