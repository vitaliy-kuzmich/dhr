# dhr
blockchain "double hashed request" pattern, ethereum, solidity<br>
<br>
This pattern solves the next problem: you need to store actions at the blockchain, that client did, this actions:<br>
1. can not be modified after client published it(for example movement in a game)<br>
2. this actions must be published just after everyone published<br>
3. this actions could be published just within some period of time<br>
<br>
But you can't store actions as is at the blockchain because blockchain is open and everyone can see what is the competitor doing.<br>
<br>
Solution:<br>
first request: <br>
1. generate unique number/string at client, concat it with actions<br>
2. take the hash from the step 1(this would guarantee that client will not modify the request at the same time it will be in the hidden condition at the blockchain)<br>
3. send and store that hash at the blockchain<br>
second step:<br>
1. after the last client published its hash, notify everyone to send original actions with temporary generated keys, since now all of the actions can be opened, to make the blockchain calculate the result<br>
2. validate actions: take the hash of received actions and compare it to previous received hash<br>
3. process the business logic<br>

