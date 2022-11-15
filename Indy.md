Hyperledger

Aries - agents, encrypted messaging, protocols, credential exchange
Ursa - Cryptograpy secret management
Indy - verifiable data registry
Indy node - idienty and transaction
Indy Plenium - consensus
Enterprice mobile agent - Aries Agent Aries SDK Indy Resolver

identy easily verifies
User data is in user control they decide where, when, and how information is shared
Strong cryptography ensures  that data is not modified
Reduced risk of data theft of misuse
Reduced cost of identity management

Network roles and TAA

Trustee
Write administrative transaction to on ledger

eg adding node and add authors

-Endorser
Writes credention transaction to ledger eg schema, credential def

-Author 
privilages to create transaction  and issue crdential from it but need endorser to endorsing transaction
Transaction Author Agreement
Agreement btw network users and ledger governence must be agreed to bfr writting.

indi cli command
indy-cli --config cliconfig
indy> pool create testnet gen_txn_file=pool_transaction_testnet_genesis
pool is network
pool connect testnet
wallet create my_walletKey
wallet open my_walletKey
did new metadata="new did"
did use <press first letter of new DID and then press tab>
help
pool list
wallet list
did list
ledger <tab> <tab>
ledger nym help
ledger get-nym <DID>

 the NYM transaction is written to the Indy distributed ledger

Aries Tool -it interact with agent
Its python based

step 1 Create DID
       Create Schema - its create data definition
       Create credential definition
step 2 Sign & Issue a verifiable credential - metadata about credential, Attribute about subject and Proof(signature)


Credential Issuance
Holder - proposal credential
Issuer Offer credential
Holder - request credential
Issuer - Issue credential

verifier - 

interact with holder
read from ledger
perform cryptograpic computations
Holder - Send Acknologement
Write credential definition on ledger

step 3 Create presentation

i Holder - Propose presentation
ii Verifier - Presentation Request
iii Holder  - approve send presentation
iv verifier - verify & send acknowledgement

step4 Read DID, schema & credential definition from the ledger and verify attestation.
