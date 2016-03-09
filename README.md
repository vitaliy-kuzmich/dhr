# dhr
blockchain "double hashed request" pattern, ethereum, solidity

This pattern solves the next problem: you need to store actions at the blockchain, that client did, this actions:
1. can not be modified after client published it(for example movment in a game)
2. this actions must be published just after everyone publish
3. this actions could be published just within some period of time

But you can't store actions as is at the blockchain because blockchain is open and everyone can see what is the competitor doing.

Solution:
first request: 
1. generate unique number/string at client, concat it with actions
2. take the hash from the step 1(this would guarantee that client will not modify the request at the same time it will be in the hidden condition at the blockchain)
3. send and store that hash at the blockchain
second step:
1. after the last client publish its hash, notify everyone to send original actions with temporary generated keys, since now all of the actions can be opened, to make the blockchain calculate the result
2. validate actions: take the hash of received actions and compare it to previous received hash
3. process the bussiness logic

