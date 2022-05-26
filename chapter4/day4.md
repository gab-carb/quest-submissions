Chapter 4 Day 4 - Creating an NFT Contract: Transferring, Minting, and Borrowing (Part 2/3)

-Because we had a LOT to talk about during this Chapter, I want you to do the following:

Take our NFT contract so far and add comments to every single resource or function explaining what it's doing in your own words. Something like this:


``` cadence
pub contract CryptoPoops {
  pub var totalSupply: UInt64

  // This is an NFT resource that contains a name, favouriteFood, and luckyNumber
  pub resource NFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

  // This is a resource interface that allows us to give public access only to deposit, getIDs, borrowNFT functions
  pub resource interface CollectionPublic {
    pub fun deposit(token: @NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowNFT(id: UInt64): &NFT
  }

  // This is a Collection resource that allows us to store all the NFTs to one storage path
  pub resource Collection: CollectionPublic {
    pub var ownedNFTs: @{UInt64: NFT}
    // This is a function that allows us to deposit an NTF resource to the collection
    pub fun deposit(token: @NFT) {
      self.ownedNFTs[token.id] <-! token
    }
    // This is a function that allows us to withdraw an NFT resource from the collection
    // If there's no NFT it panics 
    pub fun withdraw(withdrawID: UInt64): @NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
              ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }
    // This is a function that returns an array of all the NFTs IDs in the Collection
    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }
    // This function allows us to read the NFT's metadata
    pub fun borrowNFT(id: UInt64): &NFT {
      return &self.ownedNFTs[id] as &NFT
    }

    init() {
      self.ownedNFTs <- {}
    }
    // This function destroys all the resources in the collection
    destroy() {
      destroy self.ownedNFTs
    }
  }
  // This function saves the resource Collection to an empty collection
  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }
  // This is a Minter resource that contains 2 functions to mint the NFT to the 
  pub resource Minter {
    // This function mints a new NFT resource with a name, favoriteFood and luckyNumber 
    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }
    // This function creates a Minter resource
    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

  init() {
    self.totalSupply = 0
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
