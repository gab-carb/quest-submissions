Chapter 5 Day 1 - Pre/Post Conditions & Events

1-Describe what an event is, and why it might be useful to a client:

Events is a way to inform others when something happened with the contract, instead of having to constantly check the contract to see if something happened.

2-Deploy a contract with an event in it, and emit the event somewhere else in the contract indicating that it happened:



3-Using the contract in step 2), add some pre conditions and post conditions to your contract to get used to writing them out:



4-For each of the functions below (numberOne, numberTwo, numberThree), follow the instructions:


``` cadence
pub contract Test {

  // TODO
  // Tell me whether or not this function will log the name.
  // name: 'Jacob'
  // Answer: Yes it will log, since the name 'Jacob' is 5 caracters in length.
  pub fun numberOne(name: String) {
    pre {
      name.length == 5: "This name is not cool enough."
    }
    log(name)
  }

  // TODO
  // Tell me whether or not this function will return a value.
  // name: 'Jacob'
  // Answer: Yes this function returns "Jacob Tucker", since Jacob is greater than or equal to 0 in length. And since result is "Jacob Tucker".
  pub fun numberTwo(name: String): String {
    pre {
      name.length >= 0: "You must input a valid name."
    }
    post {
      result == "Jacob Tucker"
    }
    return name.concat(" Tucker")
  }

  pub resource TestResource {
    pub var number: Int

    // TODO
    // Tell me whether or not this function will log the updated number.
    // Also, tell me the value of `self.number` after it's run.
    // Answer: No it doesn't log, because the post equation can't ever be right, so it panics. When it panics the value of `self.number` resets to 0.
    pub fun numberThree(): Int {
      post {
        before(self.number) == result + 1
      }
      self.number = self.number + 1
      return self.number
    }

    init() {
      self.number = 0
    }

  }

}

