## Challenge 4 Observation

### Transaction(Hello World vs Break Solana Game)

The difference beween hello world program and break game programe is that the break game has 3 parts(web client frontend, web server backend and on-chain solana program) while the hello world program olny has a web server backend and on-chain solana pgogram. It doesnt have a front end to interact with.

When it comes to creating a transaction, for hello world program, the transcation contains the connection, the instruction and the payer(generated keypair).But for the break example, there are lot of arguments passed into the function like trackingId, blockhash, bitId and many more. And with break example, after creating the transaction, it returns a promise with a response message and the serialize transaction will be send to web socket. Since the break program is more complex than hello world that just send hello data, there are also data that are being send to the server like encoded signature and subscription.

### Accounts

For accounts, first thing i saw was there are 5 accounts type(initializing, inactive, creating, closing and active). The initial state of account is "initializing".

For closing accounts, it can only be close if the current creation lock is true and it requires the wallet as an argument. After successfully closing the accout, it will be inactive again and the current creation lock will be set to false.

For creating accounts, it can create new account when the current account is inactive and creation lock is true. For creating account, the required data are the connection, breakprogramId, wallet, cost, and parallelization. Inactive account then will be newly created and active account.

There are also calculation like program space and transaction per account that are correlated with each other.

There is also a function that can create accounts by batch. For this function, the maximum tries to create an accounts will be 3 times. Each failed attempts will throw an error along with the number of tries left.

An account also has maximum transaction depending on the program space which depends on client configuration.
