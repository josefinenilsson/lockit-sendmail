# Email functions for lockit

work in progress - come back later

## Installation

`npm install ...`

```js
var adapter = require('....');
```

## What's included

 - responsive email template (created by [mailchimp](https://github.com/mailchimp/Email-Blueprints))
 - inline css styles for proper formatting even in GMail and Outlook (CSS inlined with [juice](https://github.com/LearnBoost/juice))
 - html email templates for verify email address, email taken, forgot password and resend verification
 - works with the same configuration as [nodemailer](https://github.com/andris9/Nodemailer)

## Methods

### Verify email address

After user has signed up an email is sent to his email address.
A unique token is included within a link pointing back to our app.
When the user clicks on this link we know that the given email address exists und belongs to the right user.

`sendmail.emailVerification(username, email, token, callback)`

 - `username`: String - i.e. 'john' - used in the email body
 - `mail`: String - i.e. 'john@email.com' - recipient email address
 - `token`: String - i.e. 'abc123' - secret token for email address verification
 - `callback`: Function - callback(err, message) - callback function when email was sent

```js
var sendmail = require('sendmail');

sendmail.emailVerification('john', 'john@email', 'abc123', function(err, message) {
  if (err) console.log(err);
  // ...
})
```

### Email taken when duplicate email address signs up

When a user tries to sign up with an email address that already exists we send a hint to the right owner to indicate
this happening. Never expose to a user whether an email address exists or not

`sendmail.emailTaken(username, email, callback)`

 - `username`: String - i.e. 'john' - used in the email body
 - `email`: String - i.e. `john@email.com` - recipient email address
 - `callback`: String - callback(err, message) - callback function when email was sent

```js
var sendmail = require('sendmail');

sendmail.emailTaken('john', 'john@email', function(err, message) {
  if (err) console.log(err);
  // ...
})
```

## Setup

... config files

## Test

`grunt`

## License

Copyright (C) 2013 [Mirco Zeiss](mailto: mirco.zeiss@gmail.com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.