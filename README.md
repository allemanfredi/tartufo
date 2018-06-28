# tartufo

A super light version of truffle!

## Installation

```sh
$ npm install --save tartufo
```

## API

```js
const { connect, compileDeploy } = require('tartufo');
const web3 = await connect(socket);
const myContract = await compileDeploy(web3, pathFolder, pathContract);
```

### How to use it:

```js
const { connect, compileDeploy } = require("tartufo");

const main = async () => {
    try {
        const socket = "ws://localhost:7545";
        const web3 = await connect(socket);
        
        //pathFolder must contains all contracts to be imported
        const [ pathFolder, pathContract ] = [ 'contracts/', 'Example.sol'];
        
        const myContract = await compileDeploy(web3, pathFolder, pathContract);

        myContract.methods.myMethod(123).call({from: web3.eth.defaultAccount}, (error, result) => { /* ... */});

    } catch(err) {
        console.log(err);
    }
}

main();
```

#### Requirements

[Node.js](http://nodejs.org/) 6.3.1+


## License

[MIT](LICENSE)