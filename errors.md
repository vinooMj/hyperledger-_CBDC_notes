1, Error: Endorsement failure during invoke. response: status:500 mssage" Function CreateProduct not found contract SC"
Fix: In our case we had an extra huge file inside  our go chaincode folder So while packagaging chaincode it pakages that too and that had 
caused the issue for the smart contract
So just make there are no extra/ther file present in CC folder.

Error 18: Chaincode already exists. This error occurs when you try to instantiate a chaincode that already exists on a peer. To fix this error, you need to remove the existing chaincode from the peer.

Error 20: Failed to create channel. This error occurs when you try to create a channel that already exists. To fix this error, you need to delete the existing channel.

Error 25: Failed to connect to peer. This error occurs when you cannot connect to a peer. To fix this error, you need to make sure that the peer is running and that you are using the correct connection string.

Error 30: Failed to install chaincode. This error occurs when you cannot install a chaincode. To fix this error, you need to make sure that the chaincode is packaged correctly and that you are using the correct installation command.

Error 34: Failed to instantiate chaincode. This error occurs when you cannot instantiate a chaincode. To fix this error, you need to make sure that the chaincode is instantiated on all of the peers in the channel.

Error 40: Failed to invoke chaincode. This error occurs when you cannot invoke a chaincode function. To fix this error, you need to make sure that the chaincode is invoked on the correct peer and that the function parameters are correct.

Error 50: Failed to query chaincode. This error occurs when you cannot query a chaincode state. To fix this error, you need to make sure that the chaincode is queried on the correct peer and that the query parameters are correct.

Error 400: Bad Request. This error occurs when the request is malformed or invalid. To fix this error, you need to check the request and make sure it is valid.

Error 500: Internal Server Error. This error occurs when there is an internal error in the Hyperledger Fabric platform. To fix this error, you need to contact the platform administrator.

Error Timeout. This error occurs when the request takes too long to process. To fix this error, you can increase the timeout value.
These are just a few of the many errors that can occur in Hyperledger Fabric. The best way to troubleshoot these errors is to consult the Hyperledger Fabric documentation and the error logs.

MSP error. This error occurs when there is a problem with the membership service provider (MSP). To fix this error, you need to make sure that the MSP is configured correctly.
Certificate mismatch error. This error occurs when the certificates are not valid or do not match. To fix this error, you need to make sure that the certificates are valid and that they match.

Docker demon error. This error occurs when there is a problem with the Docker daemon. To fix this error, you need to start the Docker daemon or restart your computer.

Swarm error. This error occurs when there is a problem with the Docker swarm. To fix this error, you need to check the Docker swarm configuration and make sure that it is correct.

Event hub error. This error occurs when there is a problem with the event hub. To fix this error, you need to check the event hub configuration and make sure that it is correct.

