GETTING STARTED WITH ANCHOR 🔗

Installation #
## The easiest way to install the Anchor Platform is to pull the docker image.

Configuration #
## hosting a stellar.toml file at a standardized URL path. This file allows applications to find information about your business, the assets your services utilize, as well as the root URL paths for these services. We can host this file using the Anchor Platform.


STELLAR.TOML 🔗

## The stellar.toml file is used to provide a common place where the Internet can find information about your organization's Stellar integration. By setting the home_domain of your Stellar account to the domain that hosts your stellar.toml, you can create a definitive link between this information and that account. Any website can publish Stellar network information, and the stellar.toml is designed to be readable by both humans and machines.


https://DOMAIN/.well-known/stellar.toml



STELLAR AUTHENTICATION 🔗

## This SEP defines the standard way for clients such as wallets or exchanges to create authenticated web sessions on behalf of a user who holds a Stellar account. A wallet may want to authenticate with any web service which requires a Stellar account ownership verification, for example, to upload KYC information to an anchor in an authenticated

## Clients can use memos or muxed accounts to distinguish users or sub-accounts of shared accounts.

### Endpoint
 GET <WEB_AUTH_ENDPOINT>  

 This endpont must return two(2) fields

 {
  "transaction": "AAAAAgAAAADIiRu2BrqqeOcP28PWCkD4D5Rjjsqh71HwvqFX+F4VXAAAAGQAAAAAAAAAAAAAAAEAAAAAXzrUcQAAAABfOtf1AAAAAAAAAAEAAAABAAAAAEEB8rhqNa70RYjaNnF1ARE2CbL50iR9HPXST/fImJN1AAAACgAAADB0aGlzaXNhdGVzdC5zYW5kYm94LmFuY2hvci5hbmNob3Jkb21haW4uY29tIGF1dGgAAAABAAAAQGdGOFlIQm1zaGpEWEY0L0VJUFZucGVlRkxVTDY2V0tKMVBPYXZuUVVBNjBoL09XaC91M2Vvdk54WFJtSTAvQ2UAAAAAAAAAAfheFVwAAABAheKE1HjGnUCNwPbX8mz7CqotShKbA+xM2Hbjl6X0TBpEprVOUVjA6lqMJ1j62vrxn1mF3eJzsLa9s9hRofG3Ag==",
  
  "network_passphrase": "Public Global Stellar Network ; September 2015"
}

