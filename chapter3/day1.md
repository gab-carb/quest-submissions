1-In words, list 3 reasons why structs are different from resources.

Structs can be changed, ressources cannot be overwritten. 
You can have multiple copies of structs, while you can only have a single copy of a ressource being moved around.
Structs can be part of contracts, transactions and scripts but ressources can only be created in contracts.

2-Describe a situation where a resource might be better to use than a struct.

If you are minting a unique NFT it would be better to have it handled as a ressource, because you can only have a unique copy
of the NFT. And if you wanted to transfert it to someone else, you would know there is still only one copy of this NFT.

3-What is the keyword to make a new resource?

Create

4-Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?

No, it needs to be created in a contrat.

5-What is the type of the resource below?

pub resource Jacob {

}

A resource type named Jacob, so @Jacob.

6-Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.

pub contract Test {

    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob {
        let myJacob <- create Jacob()
        return <- myJacob
    }
}
    
