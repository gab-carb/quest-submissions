Chapter 2 - Day 1 - Our First Smart Contract

img width="778" alt="smart_2-1" src="https://user-images.githubusercontent.com/104936636/167443700-dfe2ae10-d945-4f6a-8f89-ee91abe59260.png">

Smart contract:
pub contract JacobTucker {

pub let is: String

  init() {
  self.is = "the best"
  }
}

<img width="797" alt="script_2-1" src="https://user-images.githubusercontent.com/104936636/167444116-b47cf617-3a8a-40b1-9c65-3ca2f5874c9e.png">

Script:
import JacobTucker from 0x03

pub fun main(): String {
    return JacobTucker.is
}

<
