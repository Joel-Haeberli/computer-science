tags: #distributed-systems-security  #blockchain

# Bitcoin Terms

links: [[400 DSS MOC|DSS MOC]] - [[themes/000 Index|Index]]

---

## Preliminaries

- **Collision resistance**: if its infeasible to find a collision for a hash function (except with negligible probability) $\rightarrow$ not collision impossibility (pigeonhole principle, if $s$ is size of hash space, try $s + 1$ inputs)
- **Pre-image resistance**: $H$ is one-way, for a given output $y$ it is infeasible to find an input $x$ with $h(x) = y$ except with negligible probability
- **Second pre-image resistance**: We have $x$ and cannot find a $x'$ which results to the same Hash $y$ for both $x$ and $x'$
- **Unforgeability**: an adversary should not be able to sign a message as Sender $S$ even if he has access to many signed messages by $S$ (unforgeability game)
- **Zooko's Triangle**: all known naming systems have at most two of the given three properties: *Secure*, *Memorable*, *Decentralized*
	- Bitcoin has properties *Secure* and *Decentralized*: public keys are not memorable but secure and everybody can create keypairs without permission from anyone
- **CAP Theorem**: No distributed system can be consistent, available and partition tolerant at the same time.
- **Incentive compatible**: no participant can improve their economic situation by deviating from the protocol
## Bitcoin

- **Bitcoin wallet**: collection of key pairs
- **Bitcoin address**: hash of a public key (plus checksum/encoding) $\rightarrow$ 160bits
- **Bitcoin difficulty**: according to slides: every 10 minutes a puzzle with difficulty of more than 70 Bits
- **SIGHASH**: refers to a part of a Bitcoin transaction that indicates how much of the transaction data is signed by the digital signature, allowing for more flexible transaction types and the ability to sign parts of transactions in various ways.
- **Timelocks**: restricts the spending of some bitcoins until a specified future time or block height
- **Commitment transaction**: a signed transaction in an open payment channel
- **Lightning Network**: enables fast and scalable transactions by creating a network of payment channels without needing to trust all participants, reducing the blockchain's transaction load.
- **CLTV (Check Lock Time Verify)**: allows specifying a time or block height before which a transaction output cannot be spent, ensuring that it remains locked until a certain point in time
- **CSV (CheckSequenceVerify)**: enabling the locking of a transaction output for a relative amount of time, measured in block height or time elapsed since the output's inclusion in a block

## Blockchain

- **Definition Blockchain**: "solves the Double Spending Problem" and certainly involves proof-of-work or something similar
- **Puzzle requirements**: hard to solve, difficulty adjustable, easy to verify
- **Genesis block**: first block of a blockchain (only data, no previous hash)
- **Block Propagation Time**: time between when a block is found and when it is known to the entire network (estimation that 5 seconds after block generation half of the network knows it)
- **Inter-Block Time**: average time between two consecutive blocks found by the network, determined by the puzzle difficulty, chosen such that it is fairly unlike for finding two solution at the same time (in Bitcoin: 10 minutes)
- **Transaction Confirmation**: the higher the number of confirmations, the lower the probability that the transaction will be reversed (rule of thumb to wait for 6 confirmations)
- **Block header**: contains previous hash, nonce, timestamp and the root hash (the root of a merkle tree containing all the transactions in the block)
- **Block body**: contains the transactions
- the **block hash** (256bit): is unique since the hash is collision resistant
- the **block height**: such as block number 12345, is not unique in case of a fork
- **stale blocks**: a valid block that is not in the longest chain
- **orphan block**: block that has no parent
- **Median-Time-Past**: This is the median of the time past of the last 11 blocks
- **Network-Adjusted-Time**: The median time of all connected nodes, unless it diverges more than 70 minutes from local time.
- **Coinbase transaction**: creates new coins (also called block reward), only way of creating new money in the system $\rightarrow$ always first transaction in a block
- **Consensus Rules**: rules that determine the validity of a transaction and blocks, all nodes must agree on updates which can be hard (e.g. block size, coin limit, difficulty)
- **Eventual Consistency**: guarantees that the system will be in a consistent state not immediately but after some time.
- **Escrow Situation**: involve a trusted third party holding funds until certain conditions are met, ensuring both parties in a transaction adhere to agreed terms.

- **Chain split**: same as a *Network Fork*
- **Network Fork**: different parts of the network consider different block chains as valid
- **Software Fork**: new version of any existing software, normally different client versions ("software forks") coexisting on the network
- **Hard fork**: update rules such that new blocks are valid under the new rules but perhaps not anymore under the old rules (e.g. increase block size, increase block reward, chaining block format) $\rightarrow$ generally causes a permanent network fork
- **Soft fork**: update rules that all blocks according to the new rules are also valid according to the old rules (e.g. decrease block size, decrease block reward)

## Overview Protocol Coins

![[overview-protocol-coins.png]]

---
links: [[400 DSS MOC|DSS MOC]] - [[themes/000 Index|Index]]