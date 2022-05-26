Chapter 4 Day 3 - Creating an NFT Contract: Collections (Part 1/3)


-Why did we add a Collection to this contract? List the two main reasons.
So that we can store more then 2 NFT's in one place.
So that we are able to receive NFT's from other people.

-What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")
You need to destroy the nested resource.

-Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.


-Idea #1: Do we really want everyone to be able to mint an NFT? 🤔.
Usually we want people that paid to be able to mint an NFT, and even control how many they can mint.

-Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this good?
It would ne better to reference it, so it doesn't have to move from your collection. It's more secure to keep you NFT in one place.
