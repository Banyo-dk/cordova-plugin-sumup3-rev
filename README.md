# This is a fork

Original: https://github.com/thomascube/cordova-plugin-sumup3

Android lib updated to version 3.4.0

# cordova-plugin-sumup3

Cordova plugin for native acces to the SumUp payment system via the SumUp SDK v3.x

This plugin permits interconnection beetween native SumUp SDK and hybrid mobile apps (cordova/phonegap).

## Platforms

-   iOS 9+ (not updated)
-   Android

## Installation

```
$ cordova plugin add https://github.com/Banyo-dk/cordova-plugin-sumup3-rev.git --variable SUMUP_API_KEY=<YOUR_AFFILIATION_KEY>
```

You can add your affiliation key here: https://me.sumup.com/developers
You have to add your cordova package ID in the 'Application identifiers'

## API

The plugin exposes an interface object to `cordova.SumUp` for direct interaction
with the SDK functions. See `www/sumup.js` for details about the available
functions and their arguments. All API functions are asynchronous and return a
[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises).

## Usage Example

```js
  // perform a (mandatory) merchant login
  cordova.Sumup.login()
    .then(function(res) {
      /*
      res: {
        currencyCode: {String},
        merchantCode: {String}
      }
      */
    }).catch(function(error) {
      // handle error
    });

  // initiate payment with a SumUp card reader
  cordova.Sumup.pay(amount, currency (e.g. 'EUR'), title, transactionId)
    .then(function(res) {
      /*
      res: {
          txcode: {String} // transaction code from sumup
          amount: {Number}  // result code from sumup, more info here : https://github.com/sumup/sumup-android-sdk#1-response-fields
          currency: {String} // message from sumup
          status: {String}
        }
      */
    }.catch(function(error) {
      // handle error
    });
```

## License

[MIT License](http://ilee.mit-license.org)

## Credits

Original: https://github.com/thomascube/cordova-plugin-sumup3

Inspired by https://github.com/Oupsla/cordova-sumup-plugin

## Original SumUp plugins

iOS: https://github.com/sumup/sumup-ios-sdk

Android: https://github.com/sumup/sumup-android-sdk
