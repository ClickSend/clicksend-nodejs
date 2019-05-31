# The official nodejs library for ClickSend v3 REST API

This is the official [ClickSend](https://clicksend.com) SDK. Documentation can be found [here](https://developers.clicksend.com/docs/rest/v3/?nodejs#introduction).

## Requirements
  
- [Sign Up](https://www.clicksend.com/signup) for a free ClickSend account.
- Copy your API key from the [API Credentials](https://dashboard.clicksend.com/#/account/subaccount) area.

## Installation

### Downloading Package

To download the SDK into your package run the command:

```shell
npm i clicksend
```

### Install TypeScript

You will need to install typescript to compile the code.

```shell
sudo npm install typescript
```

### Compile the TypeScript into JavaScript

Run the following commands to compile typescript into javascript:

```shell
sudo npm add request http bluebird @types/node
tsc --target es5 /node_modules/clicksend/api.ts
```

### Adding SDK into your project

Copy the api.js file along with the node_modules directory into your project to use the library, and include this in your file to use the SDK:

```shell
var api = require('./node_modules/clicksend/api.js');
```

## Documentation

Documentation for our SDK and REST API can be found [here](https://developers.clicksend.com/docs/rest/v3/?nodejs#introduction).

## Getting Started (sms/send example)

Please follow the [installation](#installation) procedure and then run the following code:
```nodejs
var api = require('./api.js');

var smsMessage = new api.SmsMessage();

smsMessage.from = "myNumber";
smsMessage.to = "+0451111111";
smsMessage.body = "test message";

var smsApi = new api.SMSApi("username", "api_key");

var smsCollection = new api.SmsMessageCollection();

smsCollection.messages = [smsMessage];

smsApi.smsSendPost(smsCollection).then(function(response) {
	console.log(response.body);
}).catch(function(err){
	console.error(err.body);
});

```

