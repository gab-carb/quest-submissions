# quest-submissions

Chapter 1 - Day 1

1.Explain what the Blockchain is in your own words:
The Blockchain is a shared database, where the data is store into blocks, the blocks of data are stored one after the other, forming a chain. This blockchain is also open and decentralized. Meaning the database is spread out among several networks in various locations, so it's not own by one person, amd it's accessible by anyone.

2.Explain what a Smart Contract is:
A Smart contract is stored code on the blockchain, enabling users to use transactions to execute actions predetermined by the code. These actions can range from sending a notification to releasing funds.  When a transaction is completed it is added the blockchain. 

3.Explain the difference between a script and a transaction:
A transaction changes the data on the blackchain, a transaction has a cost associated to it, will a script is use to view data on the blockchain, and has no cost.


Chapter 1 - Day 2 

1.What are the 5 Cadence Programming Language Pillars:
-Safety and Security: mostly by having a separation between contracts and transactions, and by having a Resource Oriented programming.
-Clarity: Cadence is easy to read and making the code declarative by design which makes the developpers intentions clear.
-Approachability: Cadence is very familiar to other programming languages, making it easy learn.
-Developer Experience: Error messages are very clear making easy to debug.
-Resource Oriented Programming: Ressources are at the core of Cadence.

2.In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5):
Having anyhing to do with the web, security is a must in todays world. When dealing with money, user infos, etc, if the code is design with safety and security in mind, it makes it even more easy for developpers to create a secure environment for it's users. If the develloppers can also easily debug it's makes it more effecient and quicker to get code working properly and safely. Since the code added to the blockchain is accessible to all, it's important that's it's clear and easy to understand for everyone. Also if it's easy more people can contribut to the flow blockchain.


Chapter 2 - Day 1 - Our First Smart Contract

Smart contract:
pub contract JacobTucker {

pub let is: String

  init() {
  self.is = "the best"
  }
}

Script:
import JacobTucker from 0x03

pub fun main(): String {
    return JacobTucker.is
}

