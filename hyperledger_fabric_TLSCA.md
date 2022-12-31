Hyperledger Fabric uses TLS to secure communication between any components inside a network.
TLS relies on a public key infrastructure (certificate authorities), and so does the identity (MSP) in a fabric network. 
We can treat them into two different and independent parts.
Unlike the MSP, TLS in Hyperledger Fabric is an option. 
The fabric system can run well without TLS, although in production TLS is always preferred.
When TLS is used, we can decide whether server authentication or mutual authentication is needed according to the security policy of the consortium.
There are different ways to implement TLS CA, and the choice is again to meet the security policy of the consortium.
