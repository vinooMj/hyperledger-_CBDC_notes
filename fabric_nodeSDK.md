Node - SDK

Fabric-network

This module is interacting with deployed chaincode. 

Fabric-ca-client

This module is using to create user certifications registrations & enrollments on the network.

Main classes:

gateway
This class help to connect and interact with fabric network

fileSystemWallet
This class deals with user identies inside the network

X509WalletMixin
This class create identity in x509 inside the network

Fabric-ca-client

register
This class register new user to network this return secret as response when invoked

enroll
This class helps to enroll registered user and input to this secret
