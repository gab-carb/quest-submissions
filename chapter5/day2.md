Chapter 5 Day 2 - Contract Interfaces

1-Explain why standards can be beneficial to the Flow ecosystem.

Standards are beneficial because they make sure every NFT smart contract are set up in the same way,
so that external apps can easily access information about the NFT. If all NFT smart contacts where 
structured differently, it would be very complexe to find information about a specefic NFT.

2-What is YOUR favourite food?

Tacos

3-Please fix this code (Hint: There are two things wrong):

The contract interface:

``` cadence
pub contract interface ITest {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    pre {
      newNumber >= 0: "We don't like negative numbers for some reason. We're mean."
    }
    post {
      self.number == newNumber: "Didn't update the number to be the new number."
    }
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff {
    pub var favouriteActivity: String
  }
}
```
The implementing contract:

``` cadence
  import ITest from 0x01 // We need to import the contract interface to implement it.
  pub contract Test: ITest { // So we add ITest to implement the contract interface.
    pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    self.number = 5
  }
                                     //Remove local resource Interface.
  pub resource Stuff: Itest.IStuff { //And implement the resource interface from the ITest contract interface.
    pub var favouriteActivity: String

    init() {
      self.favouriteActivity = "Playing League of Legends."
    }
  }

  init() {
    self.number = 0
  }
}
```
