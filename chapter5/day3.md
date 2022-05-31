Chapter 5 Day 3 - Creating an NFT Contract: Implementing the NonFungibleToken Standard (Part 3/3)

-What does "force casting" with as! do? Why is it useful in our Collection?

It brings get a generic NFT type to become a specfic NFT type. We don't want just any type of NFT in our collection, 
we only want CryptoPoops NFTs, so we need to make sure of this using force casting.

-What does auth do? When do we use it?

It give you an authorized reference. You use it with references, in order to autorize the downcast.

-This last quest will be your most difficult yet. Take this contract:
and add a function called borrowAuthNFT just like we did in the section called "The Problem" above. 
Then, find a way to make it publically accessible to other people so they can read our NFT's metadata. 
Then, run a script to display the NFTs metadata for a certain id.
You will have to write all the transactions to set up the accounts, mint the NFTs, and then the scripts to read the NFT's metadata. 
We have done most of this in the chapters up to this point, so you can look for help there :)

