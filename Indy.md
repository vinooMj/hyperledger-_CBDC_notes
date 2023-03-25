Hyperledger Indy

Indy is decentralized identy

Indy has own implementation of distributed ledger not dependent on any other blockchain platform
Indy has its own implementation of a PBFT	-like consensus protocol
Indy is one of active project
Indy deployment (Sovrin) is in production for more than 2 years..
It has real customers.
There are other Indy ledger deployment as well(Findy, kiva, etc).

SSI and Public blockchain 

Issuer   zeroKnowledge Encoding   -> Prover - wallet     zeroKnowledgeProof ->  Verifier
Sign credential                      Countersign credential                     Verifies signature

Why blockchain?
Decentralized source of trust for publicly available information.

Why blockchain is public?
Anyone in ecosystem need to be able to read data(such as public key, schemas etc)

What is onblockchain?
Public DID, DID DOCs, Issuer's publickey, Credential Schema's, Information about revoction

What is not blockchain?
Pairwise DID's
Credentials
Proves
Private Key

Indy-Plenum and Indy -node

Indy-Plenm is like consensus and general one

Indy node is top on indy plenum and identy specific transaction.

Indy is a Ledger purpose built for identity

Indy-Plenum and Indy -node written by python

Depends on ZMQ, indy-Crypto(Ursa), libsodium.

We can test with 25 nodes

Indy is permissioned network it allows steward node can join the network as node and it can write in ledger with policies

Validator
Validator pool - its fixed number node.
Validator handles writes and reads 
Its part of consensus
25 validator node
N= 3F+1
Each node replicates all ledger   
Each ledger has a merkle Tree
Most of the ledger have state based on Particia tree
BLS signature for every transaction in ledger.
multi signature by user
Digital signature: Ed25519

Incase read reques it need one node.

Observer node
Its only read
It state sync with validator
 
Authentication:

Write Request:

Must be signed(Ed25519 digital signature)
Signature its verified against public key stored on the ledger(DID txn)

Read request:
Anyone can read no authentication is required

Authorization

Write request
Role associated with every DID
Configurable auth rules(in configledger) - authorization policy for every action
How many signatures of the given role
OR/AND expressions

Read request
no autherization required

Ledger: Transaction  Log & Merkle Tree

Ledger:

ledger is like dtabase
Ordered log of transaction
It has three db
Transaction log, Merkle leaves and merkle nodes
RocksDB as key-value storage
Merkle tree for whole ledger
No real blocks

Four different ledger

Audit ledger
order across ledger
Pool ledger
Transaction for every node in the pooll addind editing removing nodes
Config ledger
pool config parameter & policy
validation rules
Domain ledger
identity specific transaction
Application specific transaction.




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
