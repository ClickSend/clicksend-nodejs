# The official nodejs library for ClickSend v3 REST API

> [!WARNING]
> **This package is deprecated and no longer actively maintained.**
> Please migrate to the latest ClickSend Node.js SDK: [ClickSend/clicksend-nodejs-v2](https://github.com/ClickSend/clicksend-nodejs-v2).

This is the official [ClickSend](https://clicksend.com) SDK for Node.js. Complete documentation can be found [here](https://developers.clicksend.com/docs/rest/v3/?nodejs#introduction).

## Requirements
  
- [Sign Up](https://www.clicksend.com/signup) for a free ClickSend account.
- Obtain your API credentials from the [API Credentials](https://dashboard.clicksend.com/#/account/subaccount) area.
- Node.js v12 or higher

## Installation

### Install the ClickSend SDK

To install the SDK in your project, run:

```shell
npm install clicksend
```

That's it! No compilation or additional setup needed.

## Documentation

Full documentation for the SDK and REST API is available [here](https://developers.clicksend.com/docs/rest/v3/?nodejs#introduction).

## Quick Start

### 1. Basic Setup

Create an `index.js` file and require the ClickSend library:

```javascript
const ClickSend = require('clicksend');

// Initialize the SMS API
const smsApi = new ClickSend.SMSApi();

// Set up authentication with your ClickSend credentials
smsApi.authentications.BasicAuth.username = 'YOUR_USERNAME';
smsApi.authentications.BasicAuth.password = 'YOUR_API_KEY';
```

### 2. Send an SMS

```javascript
function sendSMS() {
  const smsMessage = new ClickSend.SmsMessage();
  smsMessage.to = '+1234567890';      // Recipient phone number
  smsMessage.body = 'Hello from ClickSend!';

  const smsCollection = new ClickSend.SmsMessageCollection();
  smsCollection.messages = [smsMessage];

  smsApi.smsSendPost(smsCollection)
    .then((response) => {
      console.log('SMS sent successfully:', response);
    })
    .catch((error) => {
      console.error('Error sending SMS:', error.message);
    });
}

sendSMS();
```

### 3. Get SMS History

```javascript
function getSMSHistory() {
  smsApi.smsHistoryGet()
    .then((response) => {
      console.log('SMS History:', response);
    })
    .catch((error) => {
      console.error('Error retrieving SMS history:', error.message);
    });
}

getSMSHistory();
```

## Running the Example

To run the included example:

1. Update the credentials in `index.js`:
   ```javascript
   smsApi.authentications.BasicAuth.username = 'your_username';
   smsApi.authentications.BasicAuth.password = 'your_api_key';
   ```

2. Update the phone number and message as needed

3. Run the script:
   ```shell
   node index.js
   ```

## Available Methods

The SMSApi provides the following methods:

- **smsSendPost()** - Send SMS messages
- **smsHistoryGet()** - Retrieve SMS history
- **smsHistoryExportGet()** - Export SMS history

## Error Handling

Always wrap API calls in try-catch blocks or handle promise rejections:

```javascript
smsApi.smsSendPost(smsCollection)
  .then((response) => {
    console.log('Success:', response);
  })
  .catch((error) => {
    console.error('Failed:', error.message);
  });
```

## Support

For issues, feature requests, or support, visit the [ClickSend Developer Portal](https://developers.clicksend.com).

## License

ISC