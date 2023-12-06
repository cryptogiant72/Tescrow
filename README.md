#Install and deploy

1. clone this repo
```
git clone https://github.com/JackBekket/escrow-eth.git
```
2. ```npm install``` and make sure that you have truffle installed globally.
3. ```truffle migrate --reset ``` will deploy contract with some demodata defined in migration sript.
migration script can be found here:
(https://github.com/JackBekket/escrow-eth/blob/master/migrations/2_deploy_contracts.js)
4. ```npm run build ``` will build your dapp frontend with webpack builder. Make sure that you have your contract deployed.
5. You can interact with your dapp by simply open ```index.html``` from ```build``` directory after previous command.


# Contract Interaction

```
var contr = EscrowAdvansed.deployed();
```

# Truffle 2.x or standart web3 Javascript-console

  if you are using standart web3 Javascript-console or ``` truffle ver 2.x ``` you should type:

```
contr.somefunction(args);
```
like:

```
contr.start(0,'bla',1,{from: web3.eth.accounts[1], value:100});

```
or you can call variable like:

```
contr.totalEscrows.call();

```

# Truffle 3.x

Cause of new break-changes in new version of truffle (http://truffleframework.com/tutorials/upgrading-from-truffle-2-to-3#contract-abstractions-deployed-is-now-thennable)

you should use the next sintax instead of above one.:

```
contr.then(function(res){return res.somefunction(args)});

```
  like:

  ```
contr.then(function(res){return res.start(0,'bla',1,{from: web3.eth.accounts[1], value:100})});
```
and call variable like this:

```
contr.then(function(res){return res.totalEscrows.call()});
```


