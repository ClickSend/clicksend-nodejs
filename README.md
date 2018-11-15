# The official nodejs library for ClickSend v3 REST API

 This is the official [ClickSend](https://clicksend.com) SDK.  *You'll need to create a free account to use the API. You can register [here](https://www.clicksend.com/signup).*  You can use our API documentation along with the SDK. Our API docs can be found [here](https://developers.clicksend.com). 

## Installation

### Install typescript

You will need to install typescript to compile the code.

```shell
sudo npm install typescript
```

### Compile the TypeScript into JavaScript

Run the following commands to compile typescript into javascript:

```shell
sudo npm add request http bluebird @types/node
tsc --target es5 api.ts
```

### Adding SDK into your project

Copy the api.js file along with the node_modules directory into your project to use the library, and include this in your file to use the SDK:

```shell
var api = require('./api.js');
```

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

