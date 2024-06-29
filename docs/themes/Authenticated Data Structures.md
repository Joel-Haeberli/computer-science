tags: #cryptocurrency #bitcoin #symmetric #data-structure #authenticated-data-structure

# Authenticated Data Structures

links: [[402 DSS TOC - Preliminaries|DSS TOC - Preliminaries]] - [[themes/000 Index|Index]]

---

## Idea & Concept

The idea of an Authenticated Data Structure is to have data stored in an untrusted or hostile environment, without loosing the ability to verify that it was not tampered, when reading it back from there.

The Idea is that a verifier can verify a proof given by the prover. The verifier is often the owner of the structure or the party interested in authenticating the structure prior to its usage. The prover on the other side, is the environment who holds the structure for the verifier.

- the owner is called *the verifier*
- someone else is called *the prover*

## Hash Pointer

The Hash Pointer is the simplest Authenticated Data Structure. It just points a value to its hash: $v = hash(p)$
Here $v$ stands for verifier owned token while $p$ stands for the token the prover is in command of (the data structure).

![Hash Pointer](hash_pointer.png)

Example: File $\rightarrow$ I as verifier make a hash of the file and store the hash on my side. Then I send the prover (maybe a file cloud or similar), the file for storage. I can later check when downloading that the file was not altered, by using the hash function.

## Hash List 

Leveraging Hash Pointers we can know create Hash Lists. These are put together from multiple hash pointers, hashed together: $v = hash(p = p_1 || p_2 || p_3)$ where $p_1, p_2, p_3$ are defined by $v_i = hash(p_i)$. Here again $v$ tokens are controlled by the verifier, while the $p$ tokens are held by the prover.

![Hash Pointer](hash_list.png)

Example: Partial files $\rightarrow$ A file is to big to be downloaded in one step. It is sliced into three parts. Each of the three parts can be authenticated by the downloader because the hashes of the different parts result in the hash of the entire file.

*How can Alice retrieve and verify* $d_1$: She get $h_0, h_2 ... h_n$ and $d_1$ $\rightarrow$ then she can calculate $h_1$ & $h$

## Hash Tree

A Hash Tree is the generalized concept of Hash Pointer and Hash List. Hash Trees have the property that **each node holds the hash of the concatenation of its children**. Only leaves are holding actual data.

- **Ordered**: The order of children is defined and known (1, 2, 3)
- **Rooted**: The root node is known

![Hash Pointer](hash_tree.png)

## Hash-Linked List

A Hash Linked List is a Binary Hash Tree where the right side of each node is a leaf.

![Hash Pointer](hash_linked_list.png)

*Example*: **Tamper-Evident Log**: Let's say that I store data ($d_i$) on an external file share. I want to make sure that the files are uploaded in the order I said them to be. I'm first uploading $d_0$ and keep it's hash $h_0$. Then I'm uploading $d_1$ and create a hash $h_1 = hash(h_0 || d_1)$. I proceed like this for all files I want to upload. If I now get the log of the upload order ($h_0$, $h_1$, etc.) I can reconstruct the last hash $h_n$ which lets me verify that the order of uploading was respected $\rightarrow$ it is sufficient for Alice to only have $h_3$.

### Blockchain

- Blockchains are Hash-Linked lists
- every block consists of some data and the hash of the previous block
- the exception is the first block, which only consists of some data $\rightarrow$ it is called the **genesis block**
- Hash-Linked List $\neq$ Blockchain
	- Hash-linked lists exist since 1970s and do not solve the double spending problem
	- Blockchains exist since 2008 and solve the double spending problem

## Merkle Tree

A Merkle Tree is a Hash Tree with the limitation that **each leaf has no siblings**. The root of a Merkle tree is called Merkle Root. Verification of leaves
 (which hold the data) is done by applying a Merkle Proof.

### Merkle Proof

In order to verify some data $d$ we can seek a Merkle Proof. The Merkle Proof is the set of all siblings up the path from the data of interest to the Merkle Root. The prover delivers the data $d$ and the Merkle Proof (list of all siblings on the path from the requested data to the Merkle Root). The Verifier can then check if she gets the same list of siblings when walking up her tree. To conclude the verification, the verifier must compare the Merkle Root to the Merkle Root of the prover.

![Hash Pointer](merkle_tree.png)

- *Example:*
	- proof for $d_1$: root path $\{d_1,e,b,a\}$, siblings $\{d,c\}$ $\rightarrow$ the prover delivers $d_1$ and the merkle proof $\{d,c\}$

## Proof Size

- the prover sends a piece of data and wants to prove that it is correct
- the verifier only holds the top hash

Question: How much data does the prover have to send to the verifier in case of:

- a hash-linked list: all data & hashes ($n$, linear)
- a hash list: all other hashes and the data ($n$, linear)
- a merkle tree: $log_2(n)$

---
links: [[402 DSS TOC - Preliminaries|DSS TOC - Preliminaries]] - [[themes/000 Index|Index]]