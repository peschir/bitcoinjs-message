# bitcoinjs-message

[![NPM Package](https://img.shields.io/npm/v/bitcoinjs-message.svg?style=flat-square)](https://www.npmjs.org/package/bitcoinjs-message)
[![Build Status](https://img.shields.io/travis/bitcoinjs/bitcoinjs-message.svg?branch=master&style=flat-square)](https://travis-ci.org/bitcoinjs/bitcoinjs-message)
[![Dependency status](https://img.shields.io/david/bitcoinjs/bitcoinjs-message.svg?style=flat-square)](https://david-dm.org/bitcoinjs/bitcoinjs-message#info=dependencies)

[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

## Example Usage

``` javascript
var bitcoin = require('bitcoinjs-lib') // v2.x.x
var bitcoinMessage = require('bitcoinjs-message')
```

Sign a Bitcoin message

``` javascript
var keyPair = bitcoin.ECPair.fromWIF('5KYZdUEo39z3FPrtuX2QbbwGnNP5zTd7yyr2SC1j299sBCnWjss')
var privateKey = keyPair.d.toBuffer(32)
var message = 'This is an example of a signed message.'
var messagePrefix = bitcoin.networks.bitcoin.messagePrefix

var signature = bitcoinMessage.sign(message, messagePrefix, privateKey, keyPair.compressed)
console.log(signature.toString('base64'))
// => 'G9L5yLFjti0QTHhPyFrZCT1V/MMnBtXKmoiKDZ78NDBjERki6ZTQZdSMCtkgoNmp17By9ItJr8o7ChX0XxY91nk='
```

Verify a Bitcoin message

``` javascript
var address = '1HZwkjkeaoZfTSaJxDw6aKkxp45agDiEzN'
var signature = 'HJLQlDWLyb1Ef8bQKEISzFbDAKctIlaqOpGbrk3YVtRsjmC61lpE5ErkPRUFtDKtx98vHFGUWlFhsh3DiW6N0rE'
var message = 'This is an example of a signed message.'
var messagePrefix = bitcoin.networks.bitcoin.messagePrefix

console.log(bitcoinMessage.verify(message, messagePrefix, address, signature))
// => true
```

## License

MIT
