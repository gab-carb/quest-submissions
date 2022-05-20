Chapter 4 Day 1 - Account Storage


1.Explain what lives inside of an account.

Inside an account you have the contracts that have been deployed to the account 
and the data that's been stored in the account storage.


2.What is the difference between the /storage/, /public/, and /private/ paths?

-Storage can only be accessed by the owner of the account.

-Public can be access by anyone.

-Private can be accessed by the owner of the account and people the account owner give access to.


3.What does .save() do? What does .load() do? What does .borrow() do?

-.save() is to store the data to the account.

-.load() is to take the data out of the account.

-.borrow() is to look at the data in the account, without removing it.


4.Explain why we couldn't save something to our account storage inside of a script.

You can only use a transaction to save something to your account because you need the AuthAccount to access your account.
A script can only be used to read data, it is not possible to write.


5.Explain why I couldn't save something to your account.

Because the storage in an account can only be accessed by the owner of the account.
So saving, taking out, and viewing data in the account storage can only be done by the owner.


6.Define a contract that returns a resource that has at least 1 field in it. Then, write 2 transactions:
<img width="605" alt="Capture d’écran, le 2022-05-20 à 11 53 02" src="https://user-images.githubusercontent.com/104936636/169568768-4039df99-18fc-412c-9f9c-f73ea10d0019.png">

i.A transaction that first saves the resource to account storage, then loads it out of account storage, logs a field inside the resource, and destroys it.

<img width="775" alt="Capture d’écran, le 2022-05-20 à 12 05 02" src="https://user-images.githubusercontent.com/104936636/169569052-15519e7f-ff2a-4870-8ac8-75a3c0a5277b.png">

ii.A transaction that first saves the resource to account storage, then borrows a reference to it, and logs a field inside the resource.
<img width="789" alt="Capture d’écran, le 2022-05-20 à 12 08 07" src="https://user-images.githubusercontent.com/104936636/169568818-e6ca057a-2741-4417-bc56-d0cb5e72a880.png">

  
