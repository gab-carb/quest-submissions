Chapter 4 Day 3 - Creating an NFT Contract: Collections (Part 1/3)


-Why did we add a Collection to this contract? List the two main reasons.

So that we can store more then 2 NFTs in one place. 
If you have thousands of NFTs it would be complexe to have that many storage paths to remember.

So that we are able to receive NFTs from other people.
By using only account storage you would not be able to, since only the account owner can store in their account.

-What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")

You need to destroy the nested resource. 

-Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.

-Idea #1: Do we really want everyone to be able to mint an NFT? 🤔.

Usually we want people that paid to be able to mint an NFT, and even control how many they can mint.
You could mange this with resource interface.

-Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?

It would be better to get a reference to the NFT, using borrow, so it doesn't have to be moved from your collection. 
It's more secure to keep your NFTs in one place, then to move them around all the time.
