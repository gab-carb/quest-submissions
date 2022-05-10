Chapter 2 Day 2 - Transactions and Scripts

-Explain why we wouldn't call changeGreeting in a script:

Because a script is only used to read the data in the smart contract, so we can change anything.
To change something we need to use a transaction.


-What does the AuthAccount mean in the prepare phase of the transaction?:

Once a user confirms a transaction, AuthAccount is used to have access to the data in the user account, to confirm that the transaction can go thru. 


-What is the difference between the prepare phase and the execute phase in the transaction?:

The prepare phase is used to access the data in the user account, before going forward with the transaction.
The execute phase is used to change data on the blockchain. But to change anything in a transaction the codes needs to be written to allow it.
The pepare and execute sections is there to seperate the code and make it more clear for everyone.


-Add two new things inside your contract:

A variable named myNumber that has type Int (set it to 0 when the contract is deployed):
A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber:
<img width="701" alt="contrat_2-2" src="https://user-images.githubusercontent.com/104936636/167460621-77054d7d-f7b9-4945-9470-0134bf64056e.png">

Add a script that reads myNumber from the contract:
<img width="766" alt="script_2-2-1" src="https://user-images.githubusercontent.com/104936636/167460651-92274cd3-b9ef-40b5-8c62-6b5828b7ad34.png">

Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function
(tested 2 ways to write the code):

<img width="774" alt="transaction_2-2-2" src="https://user-images.githubusercontent.com/104936636/167460691-daa6acac-acc4-4bb2-a3e3-2bf3c48302a1.png">
<img width="427" alt="transaction_2-2-3" src="https://user-images.githubusercontent.com/104936636/167460896-00d9801f-3e37-4d3f-aa0e-8e075075d38d.png">

Verify that your number changed by running the script again:
<img width="792" alt="script_2-2-2" src="https://user-images.githubusercontent.com/104936636/167460744-df449a5f-4c27-4b3e-b594-9085e7862363.png">
<img width="772" alt="script_2-2-3" src="https://user-images.githubusercontent.com/104936636/167460918-28a8b01b-1dcd-4e17-b345-eb63ee8aaee6.png">

