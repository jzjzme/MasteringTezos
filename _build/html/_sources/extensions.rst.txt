.. _emacs_help:


******************************************
Part 3: Blockchain 201
******************************************
Cryptographic Fundamentals
=============================
Despite being an emerging technology, blockchain is not built on anything new, but on existing technology and theories like cryptography. There are three main concepts to power blockchain: Cryptography, P2P networks and Game Theory/Protocol.

Cryptography is the backbone of the blockchain, providing the security infrastructure needed for participants to securely access data as well as protect it from tampering. At its root, cryptography is the art of exchanging a message between two parties without the message being compromised or revealed. You may be familiar with cryptographic techniques like a substitution cipher, replacing a letter with another, or transposition ciphers, rearranging letters in a different order. Historically, cryptography has been used in war to prevent messages from falling into enemy hands, having given birth to complex computational ciphers like the German Enigma in World War II. Blockchain utilizes asymmetric cryptography, also known as public key cryptography.

Public key cryptography utilizes both public and private keys to encrypt data. These keys are just long strings of numbers that are paired together, but are not identical. The public key can be shared with anyone, while the private is kept secret to just the owner. Any message encrypted with the public key can only be decrypted with the corresponding private key, and vice versa.

Let’s look at an example of public key cryptography. Bob and Alice have special envelopes (public key) that each have a corresponding key (private key). Bob and Alice both have the keys to their respective envelopes so that they are the only ones that can open them up. Neither wants anyone to read their messages so Alice sends her envelope to Bob to enclose his letter. Bob seals the envelope with the letter, and ships it back to Alice, who opens it with her key and reads the contents.

Like any cryptography, public key encryptions are vulnerable to brute force attacks. This means that the private key can be guessed by method of guessing every possible combination, with attack speed being proportional to computing power. Brute force methods can take years or decades to crack secure encryptions.

P2P (Peer 2 Peer) networks allow the blockchain to operate as a decentralized system. In a P2P network, participants utilize and provide the infrastructure for the network. These participants are classified as nodes, and can offer different resources to support the network such as storage, computing power and bandwidth. This allows P2P networks to be sustained without the need of a centralized entity. In blockchain, a miner, also known as a full node, stores the entire blockchain information. In case, the blockchain network is attacked and information is loss, as long as there is one full node, the network can be restored.

Game Theory is essential in blockchain to provide incentives for participants in the network. Game theory studies mathematical models between rational parties, covering strategies and incentives. Correct incentive models encourage people to participate in the system, and discourage cheating or malicious actions.

In the Bitcoin blockchain, game theory is heavily embedded in the mining system. Miners can cheat in using these methods:

- Add an invalid block and transactions to receive more BTC

- Mine on top of an invalid or suboptimal blocks

The Bitcoin blockchain ecosystem is designed so that coins mined from invalid blocks hold little to no value. This discourages miners from adding invalid blocks as they will be wasting computational power on a useless asset. Since parties that join a blockchain cannot be inherently trusted, it is essential to consider game theory and incentives when building a blockchain.


Blockchain Technicals
=============================
After covering the theory for blockchain, let’s delve into the technicals on how the blockchain works. The blockchain is a linked series of blocks, with the oldest/first block known as the genesis block. Each block is composed of two parts: the block header which stores metadata for identification and references to link it to the previous block, and a list of transactions.

The Bitcoin blockchain header contains six fields:

- The Bitcoin version number

- The previous block hash, which links the block to the last one

- The Merkle Root, which is a hash that summarizes the block’s transactions

- The timestamp of the block

- The difficulty target of the block

- Nonce, which let’s miners generate the correct hash

While the header can be used to identifies the block in relation to the previous one, the block height identifies the location of the block in the chain, with the first genesis block having a block height of zero.

While blockchains have predetermined sets of rules established by the protocol, these mechanics can be modified in events call a fork. You can compare the fork to a software update that the majority of the community agrees on. A hard fork is not compatible to previous versions, typically changing consensus rules such as protocol or block size. A soft fork in comparison is compatible with previous versions of the blockchain.

Smart Contracts
=============================
While the Bitcoin blockchain was built for the single application of the blockchain as a decentralized currency, the Ethereum blockchain opened up an ecosystem for a variety decentralized applications. The introduction of programmable smart contracts is what powers this ecosystem.

A smart contract is a piece of code which runs on top of the blockchain that operates on arbitrary rules. It is auto-enforceable code which does not require a third party to activate or oversee. They have the attributes of a contractual agreement but should not be confused as a contract in the legal sense. It is more comparable to a if-then mechanism like a vending machine: put money in, get a soda out. Smart contract flow can be broken down as:

1) Creation of smart contract code which defines terms

2) Define events that trigger execution of Smart Contract

3) Execution of smart contract based on interaction or information received

4) Settlement of assets, such as cryptocurrencies or real life events

Let’s look at a decentralized apartment leasing use case for smart contracts. Alice rents an apartment, owned by Bob, with a lock connected to the blockchain via smart contract. The smart contract dictates that if Alice pays rent, the lock remains unlocked. If she does not pay rent on time, Alice is locked out of her apartment. In this example, despite owning the apartment, Bob does not facilitate the rental/lock process. The process is greatly streamlined, and removes any potential issues of Bob locking Alice out despite her paying rent since its governed by auto-enforced code.

Smart contracts reduce transaction costs through machine consensus and auto-enforced code. They bypass principal-agent problems, and establish trust in trustless environments.

Additional Resources
=============================
`Public Key Encryption <https://en.wikipedia.org/wiki/Public-key_cryptography/>`_

`Elliptic Curve Cryptography <https://en.wikipedia.org/wiki/Elliptic-curve_cryptography/>`_

`P2P Network <https://en.wikipedia.org/wiki/Peer-to-peer/>`_

`Game Theory <https://blockgeeks.com/guides/cryptocurrency-game-theory//>`_

`Merkle Trees <https://hackernoon.com/merkle-trees-181cb4bc30b4/>`_

`Forks <https://blockgeeks.com/guides/what-is-ethereum-classic/ />`_

`Smart Contracts <https://blockchainhub.net/smart-contracts//>`_

`Ethereum Whitepaper <https://github.com/ethereum/wiki/wiki/White-Paper />`_
