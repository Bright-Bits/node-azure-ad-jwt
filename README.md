# azure-ad-jwt-v2
This component makes it super simple to validate a JWT token issued by the Azure Active Directory (AAD), for both v1 and v2 in your node service. This is a fork of 'azure-ad-jwt' that supported AAD v1. This package adds support for AAD 2.0 tokens, including Microsoft Accounts (MSA's), such as @live.com or @hotmail.com, along with support for work and school accounts.

Currently the version is not using caching, which means the certificates will be downloaded from Mirosoft with every verification request. If you are using Azure AAD tokens in every request against your API additional caching would make sense. 

## Usage

```javascript
var aad = require('azure-ad-jwt-v2');

var jwtToken = '<<yourtoken>>';

aad.verify(jwtToken, null, function(err, result) {
    if (result) {
        console.log("JWT is valid");
    } else {
        console.log("JWT is invalid: " + err);
    }
});
```

## JsonWebToken 
The library is a wrapper around the [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) module so the options field can be used as described in this project. The following example checks if it is a valid graph API token: 

```javascript
aad.verify(jwtToken, { audience: 'https://graph.windows.net'}, function(err, result) ...
```
