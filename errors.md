1, Error: Endorsement failure during invoke. response: status:500 mssage" Function CreateProduct not found contract SC"
Fix: In our case we had an extra huge file inside  our go chaincode folder So while packagaging chaincode it pakages that too and that had 
caused the issue for the smart contract
So just make there are no extra/ther file present in CC folder.

