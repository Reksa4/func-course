# Chapter 1, lesson 3
## Blockchain design principle and three generations of blockchains

The previous lesson was a little bit of an overview and might sound a little bit strapped. To give you more context and perspective of why it is designed this way, we'll do a little bit of a historical tour.

## Bitcoin blockchain

### Bitcoin's Design for Censorship-Resistant Digital Cash Transfers

We'll start with the simplest design problem that Bitcoin solved 14 years ago. Bitcoin is the first blockchain so far as the most popular one that solves one problem, the problem of censorship resistant digital cash transfers, or if some people prefer to say, digital gold. So, the idea is that you have one ledger ,you have accounts that are identified by public keys, and the only thing you could do is just to transfer abstract units of coins from one public key to another.
And every time you transfer it, you package it up as a data envelope that says, Okay, I'm taking this coin from this public key and sending it to that public key. And you need to authorize this operation by putting the digital cryptographic signature into this envelope that is verified by the source public key. So you don't need to ask the destination request permission, you just show that okay, the public key A recovers the coin, therefore, public key A should be used to verify the signature.

### Multi-Input/Output Transactions and Chain Consensus in Bitcoin

Bitcoin supports splitting and merging those coins. It means that you don't have to just move individual numbers, you could have 100 on one key ,and then kind of split it in 90 and 10,or you can merge them. Hence, you have these multi input and multi output transactions,and you have these chains.Actually, direct the graphs of transactions that move the coins and merge them and split them. And these graphs are subject to consensus to prevent double spins. So you have a proof of work, miners just create the blocks of these transactions going to chunks of these sub graphs, put the proof of work. And every node simply chooses the chain that has, first of all valid transactions, and second of all, has the biggest weight.

### Bitcoin's Network Resilience and Scripting Language Extension

If there was any synchronization issue, or someone attempted to attack the network or split the network, then when the network reunites, and you get the flood of , like up to date up, when you get the flood of all the blocks that exist.You can switch from the minor chain to the bigger chain and be in synchronization with the rest of the world. That's how Bitcoin works. This is pretty simple, just public keys moving coins from one to another. Except it's slightly more generic,at a very late stage of development, there was added a scripting language that extended this idea of the public key to predicate. Instead of just the public key, you could have a little program that acts as a logical predicate that allows or disallows transfer of a coin.

### Bitcoin's Scripting Language for Account Control and Limitations

In the simplest case, it means, that predicate says just check the signature for this public key,  this the simplest possible thing you could imagine. But this little scripting language allows you to do something more than that, it allows you to do, for instance, two public key checks. Or say, I want to check two keys out of three, or I want to check into this key, or after a timeout, I want to check another key. So you could do some time locks,some hash checks, and some various combinations of signature checks. But this scripting language is just limited to controlling the sum of coins that are sitting on this account to unlock or not unlock,so that's pretty limited.

### Bitcoin's Account-Based System and Privacy Measures

Therefore the whole state of the system is just this collection of these accounts, that are having those little predicates and the balances on them. And every time you spend the coins from there, you destroy this record and create new ones. For instance, if you have 100 coins sitting here, and you want to send 10 of them, then you destroy this record and create two new records, 90 coins for the same scripting predicate, or for a different one.
For privacy reasons in Bitcoin, you have a new account address generated every time you make a transfer. And another 10 goes to someone else's predicate that contains a single public key or some other person.That's the whole system of Bitcoin. 

## Ethereum blockchain

### The Flexibility and Functionality of Second-Generation Ethereum

Now, the second generation blockchain Ethereum, that generalizes, this idea takes this kind of global view of this list of accounts with balances and says, Okay, what if we have a more flexible access to this coins on each account, and also allow us to store arbitrary data that we can mutate, when we make transactions, so transactions effectively sort of a call to function within this program, and the program then can do whatever they want. And the problem would pay for execution cost of all these operations.

### Composable Contracts: The Foundation of Decentralized Finance on Ethereum

 Some kind of invariance says: “Okay,  I will give you money or change my state only, if you pay me or if some authorization logic is checked”. But every transaction effectively can touch multiple contracts, and they can compose with each other this way. So you could have a contract that implements in some like list of tokens and another contract that implements an exchange, and then you can craft a transaction that says, Okay, you transfer this coin there, and then this other contract will credit me with some other assets in exchange for this coin. All these things become possible and Ethereum showed the world that this is a hugely valuable platform for this sort of, decentralized financial applications.

### The Trade-off between Functionality and Scalability in Ethereum

What is the big trade off here is that the function is much richer than Bitcoin. And you can build much more things and you want more transactions, but the architecture doesn't scale. That's a big problem, it all like the core network has to see all the state and every transaction has to wait for all the other transactions to happen, because it may potentially touch the entirety of the state of the system can touch all the contracts, and send messages anywhere in the system.


## TON blockchain

### Scalability and Security in TON Blockchain

So, the TON is a third generation blockchain that comes on the stage and says, Okay, let's introduce a few limitations that will unlock scalability. Let's make sure that the contracts cannot see the global state, so ,everything's super local. We still do have this predicament that you have a piece of code, a piece of data, and some balance of coins together, like in Ethereum. But this thing can only see itself and to communicate with anything else, it has to emit the messages and then we don't provide the guarantees of when exactly they will be delivered. And you don't get an automatic response, you can only receive another message that was explicitly sent to you.
But this will unlock scalability, because now a bunch of contracts operating in one place, and not touching another contract, could be verified completely independently. And to make it all work with the consensus, we couldn't use proof of work for this. So, we have to use proof of stake , because kind of sharding proof of work is a definition of attack on proof of work. Proof of stake allows you to have intersecting groups with separate stakes that are going to focus on different parts of the contracts, and then have clever routing rules to have partial agreements on how to route the messages from one place to another, so that ,no point, all the parties don't have to see the globe like a global set of all the messages flying around.

### Scalability and Security in TON Blockchain with Cost Control

So that's the big idea of TON like ultimate scalability and all the data structures, they're designed in a way that you never have this risk, unbounded growth of any data or unbounded exposure of data to like the whole of the network. And this is the principle of scalability. One more thing that TON implements is the precise cost controls. In Ethereum, you only have their cost in terms of gas of the operation execution, but generalizes this to not only you pay for the gas for execution, but you also pay rent for all the bytes that you store under contract. The more data you want to store, the more you pay, like per second,and also their explicit fees for all the message routing. So that can really close us the lead on various denial of service possibilities.

### Conclusion

To sum up, we described three generations of blockchain design and how we write the design of TON. So, we started with a Bitcoin that is very simple and limited and doesn't like perfectly scale, but kind of doesn't have to, then Ethereum expands the functionality and flexibility of the platform. But, this kind of hits the limitations in terms of scalability of the single blockchain. TON introduces certain trade offs that make development no harder and more weird to do this multi contract execution, but this allows infinite scaling.

