tags: #cryptocurrency #bitcoin #difficultyadjustmentcoin #inputoutputcoin #simplifiedpaymentverificationcoin

# From IncentiveCoin to Bitcoin

links: [[404 DSS TOC - Bitcoin|DSS TOC - Bitcoin]] - [[themes/000 Index|Index]]

---

Builds up on decentralization: [[From BankCoin to IncentiveCoin]]

[[From BankCoin to IncentiveCoin#IncentiveCoin|IncentiveCoin]] solves the decentralization problem. With the process from [[From BankCoin to IncentiveCoin#IncentiveCoin|IncentiveCoin]] to Bitcoin we solve the problems remaining for Bitcoin to be a usable currency.

## DifficultyAdjustmentCoin

*Predecessor: [[From BankCoin to IncentiveCoin#IncentiveCoin|IncentiveCoin]]*

The [[From BankCoin to IncentiveCoin#IncentiveCoin|IncentiveCoin]] finally solved the centralization problem of the bank by implementing a sequence of mechanisms which allow to have a distributed ledger in an eventually consistent state. The problem that comes with the [[From BankCoin to IncentiveCoin#IncentiveCoin|IncentiveCoin]] is that the computing power changes (increases). Like this, the puzzle which shall prevent 51% attacks becomes easier again until it's possible that it might happen (Inter-Block-Time gets smaller and smaller - [[Eventual Consistency]]). So what we need is a possibility to adjust the difficulty of the puzzle (as described in [[Proof-of-Work (PoW)#Concept|Proof-of-Work]]). This is done by the DifficultyAdjustmentCoin. This coin makes it possible to adjust the difficulty, so that the inter-block time is constant (e.g. 10 minutes). Besides the properties of the IncentiveCoin, the **DifficultyAdjustmentCoin, now also contains a timestamp. With the timestamp we are now able to measure the computational power of the network**.

The Timestamp is a Unix timestamp serialized as 32-Bit integer (seconds since 1970-01-01). Using this timestamp, participants are able to measure following properties:

1. *Median-Time-Past*: This is the median of the time past of the last 11 blocks
2. *Network-Adjusted-Time*: The median time of all connected nodes, unless it diverges more than 70 minutes from local time. 

This properties build the rules for the DifficultyAdjustmentCoin. These say that a node *accepts* a block timestamp if, it is greater than the *Median-Time-Past* and less than *Network-Adjusted-Time + 2 hours*. **Concluding, a block timestamp is accepted** iff:

1. Block-Timestamp > *Median-Time-Past*
2. Block-Timestamp < *Network-Adjusted-Time + 2 hours*

Only if a block timestamp holds on to these rules, it is considered for the calculation of the networks power. Nodes only need to ensure that the timestamp is accurate enough to allow measuring computational power (sometimes block $n + 1$ has smaller timestamp than block $n$).

Now we could try to adjust the [[Proof-of-Work (PoW)#Hashcash|Hashcash]] difficulty but the problem is, that this cannot be done smoothly. So we change the puzzle. Now not the amount of zeros prefixing the hash is the problem but the value of the hash itself. **We now ask the solvers to find a number which is smaller than a given number in $[0,..,2^{256}]$**. We can now adjust the difficulty more fine-grained. 

For the adjustment, every 2016 blocks (around two weeks - $2016 * 10min = 20160; 20160min / 60min / 24hours = 14 days$) a **retarget** operation is performed by the network. This means that the problem hardness is adjusted by measuring the performance and calculating a difficulty which will result in around 10 minutes of computing per problem.

The **retarget** flow works like this:

1. Node looks at last 2016 timestamps 
2. Adjust the ration between intended time (2 weeks, 20160 minutes) and the actual time taken
3. look that it does not exceed factor 4

**DifficultyAdjustmentCoin solves**: 

- Computing power increase of [[From BankCoin to IncentiveCoin#IncentiveCoin|IncentiveCoin]] can be addressed with changing the difficulty

**Problems** with the DifficultyAdjustmentCoin:

- We are only able to transfer one coin per transaction which is bit nasty.

## InputOutputCoin

*Predecessor: [[From BankCoin to IncentiveCoin#TransactionCoin|TransactionCoin]]*

At the moment we still have the design of the [[From BankCoin to IncentiveCoin#TransactionCoin|TransactionCoin]] for the transactions. The problem is that this only allows us to send one coin per transaction (because the coin *is* the transaction. What we want is...

- that we can combine amounts by referencing multiple transactions
- split amount by specifying multiple Amount/Recipient pairs to send coins to

For this we look what a transaction is built of: Inputs and Outputs. The output consists of: 

 - the **number of coins** to be sent
 - and the **public key of the recipient**

whereas the input consists of:

- a reference to an output of a previous transaction
- a signature of the sender (matching the public key in the referenced output) $\rightarrow$ this is the proof that the coin we reference and use for our new transaction is owned by us

With this we are able to validate transactions following this process:

1. For each input, check that the referenced output exists and is not already spent
2. Check that sum of output values is not greater than sum of input values
3. For each input do the following input validation:
	- Verify signature with the signature of the input, public key from the referenced output and the message (which is the current transaction without the signatures contained)

**InputOutputCoin solves**: 

- Transactions can now take more than one coin.

**Problems** with the InputOutputCoin:

- We can only send money to public keys.

## ScriptCoin

*Predecessor: [[From IncentiveCoin to Bitcoin#InputOutputCoin|InputOutputCoin]]*

Currently we are able to send money to one public key at a time. This is good but we want to build more complex cases. The cases are:

- Inputs needs to be signed by two keys, not only one
- Only one of the two keys is required to sign
- in general: $m$ of $n$ keys are *required* to sign
- Before a time $x$ Alice's signature is required, after time $x$ Bob's signature is required

To implement this functionality the Bitcoin Script is introduced. It is a stack-based assembly language. It is simplified and only supports a small set of operations (arithmetic operations, handling the stack, conditionals, hashing, signature, verification, no loops/jumps). The outcome of each Bitcoin Script is either *Error* or *No Error*.

The scripts are now placed in into the inputs and outputs of the [[From IncentiveCoin to Bitcoin#InputOutputCoin|InputOutputCoin]]. The outputs are holding the [[Bitcoin Scripts#Lock|Lock Scripts]] while the inputs are holding the [[Bitcoin Scripts#Unlock|Unlock Scripts]]. For more information about [[Bitcoin Scripts]] and how they work, read the respective [[Bitcoin Scripts|page]].

A transaction in ScriptCoin is validated by doing the same process as in [[From IncentiveCoin to Bitcoin#InputOutputCoin|InputOutputCoin]], but the input validation step is removed in favor of the script validation step:

1. Do for each input and the referenced output:
	1. Start with Empty Stack
	2. Run unlock script of current input
	3. Run lock script of referenced output
	4. if end of script is reached and stack is empty or top element is true, input is valid.

Remark: **do not chain the scripts all together**

**ScriptCoin solves**: 

- Flexibly define when and how coins are to be spent.

**Problems** with the ScriptCoin:

- The problem that remains is that the verification of the payment is hard (download entire blockchain to verify a transaction > 500GB)

## SimplifiedPaymentVerificationCoin / SPVCoin

*Predecessor: [[From IncentiveCoin to Bitcoin#ScriptCoin|ScriptCoin]]*

The SimplifiedPaymentVerificationCoin (also SPVCoin) solves the problem that verification of payments is hard in [[From IncentiveCoin to Bitcoin#ScriptCoin|ScriptCoin]] (due to the fact, that each node must have the entire chain, which is bigger than 500GB, to validate a payment). Therefore it introduces *SPV nodes* who do not store the entire chain but instead only the headers of the blocks containing metadata needed to still verify payments but stripped of the transactions, which are not needed for this purpose.

Therefore a block is split into *block header* and *block body*.

- **Block header**: contains previous hash, nonce, timestamp and the root hash (the root of a merkle tree containing all the transactions in the block)
- **Block body**: contains the transactions

Nodes who carry the entire chain are now called *full nodes*. A *block header* is only 80 bytes which leads to a size around 60MB (2022). The *block headers* store the root hash of the transaction if they were put into a [[Authenticated Data Structures#Merkle Tree|Merkle Tree]]. The *SPV nodes* then call *full nodes* for [[Authenticated Data Structures#Merkle Proof|Merkle Proofs]] to verify payments. *SPV nodes* rely on trustworthy *full nodes*. If *full nodes* do not good at their job of validating transactions properly, the construct breaks. *SPV nodes* accept Security and Privacy Tradeoffs.

**Security and Privacy Tradeoff**

- An SPV node is vulnerable to miners: the miner majority can easily make your SPV client believe that it just received 1000 BTC when in fact it did not $\rightarrow$ a verifier cannot be sure if a transaction is in this block, if it is a valid block and if that the outputs that are referenced actually exist
- SPV nodes typically ask multiple full nodes for verification (does not solve the issue above)
- You would only use SPV for amounts that are small compared to the block reward
- By requesting the merkle proof, we expose the connection between our IP address and the incoming transaction
- *You would not use SPV if your privacy is important*

**SimplifiedPaymentVerificationCoin solves**: 

- SPVCoin solves the problem that payment verification is hard due to the size of the blockchain.

## Bitcoin

*Predecessor: [[From IncentiveCoin to Bitcoin#SimplifiedPaymentVerificationCoin / SPVCoin|SimplifiedPaymentVerificationCoin / SPVCoin]]*

Finally we arrive in the eden of happiness, equality, freedom and peace (so exciting!)! I present: THE BITCOIN (yeah, it's a bit polemic...)

The Bitcoin builds on top of the [[From IncentiveCoin to Bitcoin#SimplifiedPaymentVerificationCoin / SPVCoin|SimplifiedPaymentVerificationCoin]] and possesses a block header with following structure:

- Version (4 bytes)
- Previous Block Hash (32 bytes)
- Merkle Root (of transactions contained) (32 bytes)
- Timestamp (4 bytes)
- Difficulty Target (4 bytes)
- Nonce (solution to puzzle) (4 bytes)

Each Bitcoin Block Header is therefore **80 bytes**.

A block can be identified by:

- the **block hash** (256bit): is unique since the hash is collision resistant
- the **block height**: such as block number 12345, is not unique in case of a fork
- **stale blocks**: a valid block that is not in the longest chain
- **orphan block**: block that has no parent

The first transaction in a block is always the **coinbase transaction** (as described in [[From BankCoin to IncentiveCoin#IncentiveCoin|IncentiveCoin]]). It has only *one input* which references no transaction (zero hash) and an arbitrary coinbase parameter up to 100 bytes (instead of an [[Bitcoin Scripts#Unlock|unlock script]]). It has. *any number of outputs*, spending the block reward and the transaction fees.

The first block of the chain is called the **genesis block** and is statically encoded in the bitcoin client. It contains the message "The Times 03/Jan/2009 Chancellor on brink of second bailout for banks." which is the heading of the newspaper ["The Times"](https://www.thetimes.co.uk/article/chancellor-alistair-darling-on-brink-of-second-bailout-for-banks-n9l382mn62h). This proves, that the chain did not exist before the third of january 2009 and therefore proves, that Nakamoto was not able to pre-mine blocks for himself.

**Block Validation Simplified**

Every node validates every block it receives (simplified):

1. Validate the block data structure and size
2. Validate the proof-of-work
3. Validate the hash of the previous block
4. Validate the block timestamp
5. Validate the merkle root
6. Validate the coinbase transaction
7. Validate all other transaction

**Bitcoin solves**: 

- EVERYTHING. At the moment not one thing...
- wait I forgot: Weapon dealers can now sell their stuff without getting caught and cartels can pay their hitmen without the fear of being tracked down... yai! Such a great improvement to the world.

**Problems** with the Bitcoin:

- Lots of crazy insane assumptions of how the participants behave and how the network evolves...
- It's not working as expected (technically it is for sure)
- Human... maybe if we get rid of the "human-problem", bitcoin might work... Looking at the world right now we are on a good track to reach this last goal to make bitcoin a great technology... so invest in bitcoin... when you are dead it will be worth a lot... probably ;)

---
links: [[404 DSS TOC - Bitcoin|DSS TOC - Bitcoin]] - [[themes/000 Index|Index]]