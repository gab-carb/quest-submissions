Chapter 5 Day 3 - Creating an NFT Contract: Implementing the NonFungibleToken Standard (Part 3/3)

-What does "force casting" with as! do? Why is it useful in our Collection?

It brings get a generic NFT type to become a specfic NFT type. We don't want just any type of NFT in our collection, 
we only want CryptoPoops NFTs, so we need to make sure of this using force casting.

-What does auth do? When do we use it?

It give you an authorized reference. You use it with references, in order to autorize the downcast.

-This last quest will be your most difficult yet. Take this contract.
And add a function called borrowAuthNFT just like we did in the section called "The Problem" above:

<img width="518" alt="Capture d’écran, le 2022-06-01 à 10 55 25" src="https://user-images.githubusercontent.com/104936636/171471063-290a3f67-0723-4d66-bab3-7d2d96b1d64e.png">

-Then, find a way to make it publically accessible to other people so they can read our NFT's metadata:

<img width="998" alt="Capture d’écran, le 2022-06-01 à 12 07 58" src="https://user-images.githubusercontent.com/104936636/171471084-b84d2ee6-dedb-44d0-84df-b8b174d209e2.png">

-You will have to write all the transactions to set up the accounts, mint the NFTs

<img width="1201" alt="Capture d’écran, le 2022-06-01 à 13 53 38" src="https://user-images.githubusercontent.com/104936636/171471166-46daca6a-21b7-4c75-8091-92ce9aec40dd.png">
<img width="1202" alt="Capture d’écran, le 2022-06-01 à 13 54 10" src="https://user-images.githubusercontent.com/104936636/171471178-db30fb6b-b7e8-44f3-8816-fb90b3987da4.png">

-Then, run a script to display the NFTs metadata for a certain id:

<img width="939" alt="Capture d’écran, le 2022-06-01 à 13 55 11" src="https://user-images.githubusercontent.com/104936636/171471213-7b1e8def-70cd-4664-abcd-ff24d8e6f9d5.png">

-Full Code:
``` cadence
import NonFungibleToken from 0x02
pub contract CryptoPoops: NonFungibleToken {
  pub var totalSupply: UInt64

  pub event ContractInitialized()
  pub event Withdraw(id: UInt64, from: Address?)
  pub event Deposit(id: UInt64, to: Address?)

  pub resource NFT: NonFungibleToken.INFT {
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

  pub resource interface MyCollectionPublic {
    pub fun deposit(token: @NonFungibleToken.NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT 
    pub fun borrowAuthNFT(id: UInt64): &NFT
  }

  pub resource Collection: NonFungibleToken.Provider, NonFungibleToken.Receiver, NonFungibleToken.CollectionPublic, MyCollectionPublic {
    pub var ownedNFTs: @{UInt64: NonFungibleToken.NFT}

    pub fun withdraw(withdrawID: UInt64): @NonFungibleToken.NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
            ?? panic("This NFT does not exist in this Collection.")
      emit Withdraw(id: nft.id, from: self.owner?.address)
      return <- nft
    }

    pub fun deposit(token: @NonFungibleToken.NFT) {
      let nft <- token as! @NFT
      emit Deposit(id: nft.id, to: self.owner?.address)
      self.ownedNFTs[nft.id] <-! nft
    }

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

    pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT {
      return &self.ownedNFTs[id] as &NonFungibleToken.NFT
    }

    pub fun borrowAuthNFT(id: UInt64): &NFT {
      let ref = &self.ownedNFTs[id] as auth &NonFungibleToken.NFT
      return ref as! &NFT
    }

    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }
  }

  pub fun createEmptyCollection(): @NonFungibleToken.Collection {
    return <- create Collection()
  }

  pub resource Minter {

    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

  init() {
    self.totalSupply = 0
    emit ContractInitialized()
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
```
