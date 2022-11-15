# _⚠️ MOVED TO [OpenFn/adaptors](https://github.com/OpenFn/adaptors)! ⚠️_

**N.B.: New versions are available at:
https://github.com/OpenFn/adaptors/tree/main/packages/progres**

# Language Progres (Archived) [<img src="https://avatars2.githubusercontent.com/u/9555108?s=200&v=4)" alt="alt text" height="20">](https://www.openfn.org) [![Build Status](https://travis-ci.org/OpenFn/language-progres.svg?branch=master)](https://travis-ci.org/OpenFn/language-progres)

An OpenFn **_adaptor_** for building integration jobs for use with the UNHCR ProGres v4 API.

## Design notes

- Integration must run through UNHCR's DTP, a middleware layer that provides a public API for UNHCR internal software.
- An API token _and_ a self-signed certificate must be provided for communication with UNHCR's DTP.
- Two-way sync must be possible between Primero and ProGres
- Teams still in discussion about whether the most common use-case will be a timed sync or real-time/event-based sync.

## Documentation

- View the documentation at https://openfn.github.io/language-progres/
- To update the documentation site, run: `./node_modules/.bin/jsdoc --readme ./README.md ./lib -d docs`

### sample configuration

```json
{
  "url": "https://endpoint/To/DTP",
  "key": "-----BEGIN PRIVATE KEY-----SOMETYPEOFPRIVATEVALUE-----END PRIVATE KEY-----",
  "cert": "-----BEGIN CERTIFICATE-----SOMETYPEOFVALUE-----END CERTIFICATE-----",
  "token": "[REDACTED]"
}
```

### Posting data to an endpoint with SSL cert authentication

```js
postData({
  url: urlDTP,
  body: { a: 1 },
  headers: {
    'Subscription-Key': configuration['token'],
  },
  agentOptions: {
    key,
    cert,
  },
});
```

## Development

Clone the repo, run `npm install`.

Run tests using `npm run test` or `npm run test:watch`

Build the project using `make`.

To build the docs for this repo, run `./node_modules/.bin/jsdoc --readme ./README.md ./lib -d docs`.
