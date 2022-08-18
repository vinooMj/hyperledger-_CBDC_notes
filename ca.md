CA

Hyperledger Fabric provides an optional certificate authority service that you may choose to use to generate the certificates and key material to configure 
and manage identity in your blockchain network. 

We have walked through both the cryptogen tool and the Fabric-CA, and see the difference between them. Cryptogen is good for demo or static setup, while 
Fabric-CA provides a better way to issue certificates in real life.

CA that can generate ECDSA certificates may be used.

The Fabric CA server should now be listening on port 7054.

The Fabric CA issues and stores public keys only. Private keys are generated and stored by the client prior to invoking the enroll API (which essentially 
generates a CSR - certificate signing request - and submits it to the Fabric CA which then issues a signed X509 certificate.

Registration of identities, or connect to a Lightweight Directory Access Protocol (LDAP) as the user registry.
Issuance of Enrollment Certificates (ECerts). Enrollment is a process whereby the Fabric CA issues a certificate key-pair, comprised of a signing 
certificate and a private key that forms the identity. The private and public keys are first generated locally by the Fabric CA client, and then the 
public key is sent to the CA which returns an encoded certificate, the signing certificate.
Certificate renewal and revocation.


We are using Javascript codes provided in the Fabcar application. In particular we look into enrollAdmin.js and registerUser.js. as both are using 
SDK to interact with the Fabric-CA and fabric network.

Verify user certificate
Each activity on fabric network and chaincode requires identity, presented as X.509 digital certificate. As far as the issuer CA is trusted by f
abric network.

inside set() we use cid.GetX509Certificate() method to extract the x509 certificate, and inside x509 we extract the Subject.CommonName (CN). 
We enforce access control by checking If the CN is Admin or not, and non Admin user will be returned with error message.

Registers Identy
Issues ECerts
Renew & Revoke Certs
Sqlite db is using
