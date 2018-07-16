# getsmscode

> Allows you to spoof SMS number verification.

[![NPM](https://img.shields.io/npm/v/getsmscode.svg)](https://www.npmjs.com/package/getsmscode) [![Build Status](https://travis-ci.org/transitive-bullshit/getsmscode.svg?branch=master)](https://travis-ci.org/transitive-bullshit/getsmscode) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

- meant for automated systems that need to bypass SMS number verification
- handles hundreds of known services (wechat, google, facebook, whatsapp, uber, twitter, etc...)
- thorough test suite
- great for bots...


## Install

This module requires `node >= 8`.

```bash
npm install --save getsmscode
```


## Usage

```js
const SMSNumberVerifier = require('getsmscode')

const smsVerifier = new SMSNumberVerifier('plivo')

// fetch a number to use for a new verification request
const number = await smsVerifier.getNumber()

// give request.number to third-party service such as google...
// third-party service sends SMS code to the given number

// check for valid codes received via SMS from the google service
const codes = await request.getAuthCodes({ service: 'google' })
// codes = [ '584125' ]
```

**Note**: there may be multiple auth codes returned since the SMS numbers being used are publicly shared. We filter the results down to only those codes that could possibly be associated with your request, and most of the time you will only receive one code back. In the case of multiple codes, we recommend you try the codes in-order (the most recently received code will be first).

**Note**: there may be variable amounts of latency between giving your number to the service and the SMS code being received. If no valid codes are returned, it is recommended that you retry `request.getAuthCodes` with an exponential timeout.


## API

**TODO**

## Todo

- [ ] support country selection
- [ ] support more providers
  - paid
    - [ ] https://sms-verification.net
    - [ ] https://receive-sms.com
    - [ ] twilio
    - [ ] [plivo](https://plivo.com)
    - [ ] [nexmo](https://www.nexmo.com/pricing)
  - anonymous / free
    - [ ] https://freephonenum.com/us
    - [ ] https://receive-smss.com/
    - [ ] https://sms-online.co/receive-free-sms
    - [ ] [trash mobile](https://www.spoofbox.com/en/tool/trash-mobile)
    - [ ] [misc](https://drfone.wondershare.com/message/receive-message-online.html)
  - [aggregate](https://www.reddit.com/r/privacytoolsIO/comments/8bz1j6/receive_anonymous_sms_online_without_giving_away/)
- how can you tell if a number has been banned?


## Related

- [parse-otp-message](https://github.com/transitive-bullshit/parse-otp-message) - Parses OTP messages for a verification code and service provider.
- [smsprivacy](https://smsprivacy.org/) - Allows you to sign up for anonymous SMS numbers via bitcoin.


## Disclaimer

Using this software to violate the terms and conditions of any third-party service is strictly against the intent of this software. By using this software, you are acknowledging this fact and absolving the author or any potential liability or wrongdoing it may cause. This software is meant for testing and experimental purposes only, so please act responsibly.


## License

MIT © [Travis Fischer](https://github.com/transitive-bullshit)
