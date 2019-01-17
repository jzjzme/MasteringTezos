.. _custom_look:


******************************************
Part 3: Blockchain 201
******************************************
Blockchain Technicals
=============================

Despite being an emerging technology, blockchain is not built on anything new, but on existing technology and theories like cryptography. There are three main concepts to power blockchain: Cryptography, P2P networks and Game Theory/Protocol.


Cryptography
-----------------

Cryptography is the backbone of the blockchain, providing the security infrastructure needed for participants to securely access data as well as protect it from tampering. At its root, cryptography is the art of exchanging a message between two parties without the message being compromised or revealed. You may be familiar with cryptographic techniques like a substitution cipher, replacing a letter with another, or transposition ciphers, rearranging letters in a different order. Historically, cryptography has been used in war to prevent messages from falling into enemy hands, having given birth to complex computational ciphers like the German Enigma in World War II. Blockchain utilizes asymmetric cryptography, also known as public key cryptography. 

Public key cryptography utilizes both public and private keys to encrypt data. These keys are just long strings of numbers that are paired together, but are not identical. The public key can be shared with anyone, while the private is kept secret to just the owner. Any message encrypted with the public key can only be decrypted with the corresponding private key, and vice versa. 

Let’s look at an example of public key cryptography. Bob and Alice have special envelopes (public key) that each have a corresponding key (private key). Bob and Alice both have the keys to their respective envelopes so that they are the only ones that can open them up. Neither wants anyone to read their messages so Alice sends her envelope to Bob to enclose his letter. Bob seals the envelope with the letter, and ships it back to Alice, who opens it with her key and reads the contents. 

Like any cryptography, public key encryptions are vulnerable to brute force attacks. This means that the private key can be guessed by method of guessing every possible combination, with attack speed being proportional to computing power. Brute force methods can take years or decades to crack secure encryptions. 


P2P Networks
-----------------

P2P (Peer 2 Peer) networks allow the blockchain to operate as a decentralized system. In a P2P network, participants utilize and provide the infrastructure for the network. These participants are classified as nodes, and can offer different resources to support the network such as storage, computing power and bandwidth. This allows P2P networks to be sustained without the need of a centralized entity. In blockchain, a miner, also known as a full node, stores the entire blockchain information. In case, the blockchain network is attacked and information is loss, as long as there is one full node, the network can be restored. 

Game Theory
-----------------
Game Theory is essential in blockchain to provide incentives for participants in the network. Game theory studies mathematical models between rational parties, covering strategies and incentives. Correct incentive models encourage people to participate in the system, and discourage cheating or malicious actions. 

In the Bitcoin blockchain, game theory is heavily embedded in the mining system. Miners can cheat in using these methods:
Add an invalid block and transactions to receive more BTC
Mine on top of an invalid or suboptimal blocks

The Bitcoin blockchain ecosystem is designed so that coins mined from invalid blocks hold little to no value. This discourages miners from adding invalid blocks as they will be wasting computational power on a useless asset. Since parties that join a blockchain cannot be inherently trusted, it is essential to consider game theory and incentives when building a blockchain.



Blockchain Breakdown
-----------------


Additional readings
=============================
`Bitcoin white paper <https://bitcoin.org/bitcoin.pdf/>`_

`Proof of Work <https://en.wikipedia.org/wiki/Proof-of-work_system/>`_

`Proof of Stake <https://en.wikipedia.org/wiki/Proof-of-stake/>`_

`Two General Problem <http://hydra.infosys.tuwien.ac.at/teaching/courses/AdvancedDistributedSystems/download/1975_Akkoyunlu,%20Ekanadham,%20Huber_Some%20constraints%20and%20tradeoffs%20in%20the%20design%20of%20network%20communications.pdf/>`_

`Byzantine General Problem <http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.126.9525&rep=rep1&type=pdf/>`_

`Byzantine General Problem <https://marknelson.us/posts/2007/07/23/byzantine.html/>`_

`51% Attack and Double Spending <https://medium.com/coinmonks/what-is-a-51-attack-or-double-spend-attack-aa108db63474/>`_
