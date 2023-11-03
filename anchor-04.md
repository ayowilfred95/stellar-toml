SUMMARY 🔗
### Summary of what to implement

This protocol enables anchors to accept off-chain assets in exchange for different on-chain assets, and vice versa. Specifically, it enables anchors to provide quotes that can be referenced within the context of existing Stellar Ecosystem Proposals. How the exchange of assets is facilitated is outside the scope of this document.

SPECIFICATION 🔗

stellar.toml 🔗

## An anchor must define the location of their ANCHOR_QUOTE_SERVER in their stellar.toml. This is how a wallet knows where to find the anchor's server.

Authentication 🔗

## This endpoints use authentication in the form of a (SEP-10) JSON Web Token (JWT) in the Authorization header of the request.

Authentication is mandatory for POST /quote and GET /quote/:id, but optional for the remaining endpoints. When optional, if authentication is provided it can be used to personalize the respective responses.

## Authenticated type
### Authorization: Bearer <jwt>


Asset Identification Format 🔗

## This can be used to provide quotes for any class of asset in exchange for a Stellar asset. The following format is used to identify an asset in API requests and responses.

<scheme>:<identifer>

## For example, Stellar USDC would be identified as:

### stellar:USDC:GA5ZSEJYB37JRC5AVCIA5MOP4RHTM335X2KGX3IHOJAPP5RE34K4KZVN

## Fiat NGN would be identified as:
### iso4217:NGN


Endpoints 🔗

##   GET /info

{
  "assets":  [
    {
      "asset": "stellar:USDC:GA5ZSEJYB37JRC5AVCIA5MOP4RHTM335X2KGX3IHOJAPP5RE34K4KZVN"
    },
    {
      "asset": "stellar:NGN:GDVKY2GU2DRXWTBEYJJWSFXIGBZV6AZNBVVSUHEPZI54LIS6BA7DVVSP"
    },
    {
      "asset": "iso4217:GNG",
      "country_codes": ["NGN"],
      "sell_delivery_methods": [
        {
          "name": "cash",
          "description": "Deposit cash NGN at one of our agent locations."
        },
        {
          "name": "ACH",
          "description": "Send NGN directly to the Anchor's bank account."
        },
        {
          "name": "PIX",
          "description": "Send NGN directly to the Anchor's bank account."
        }
      ],
      "buy_delivery_methods": [
        {
          "name": "cash",
          "description": "Pick up cash NGN at one of our payout locations."
        },
        {
          "name": "ACH",
          "description": "Have NGN sent directly to your bank account."
        },
        {
          "name": "PIX",
          "description": "Have NGN sent directly to the account of your choice."
        }
      ]
    }
  ]
}




##   GET /prices
{
  "buy_assets": [
    {
      "asset": "stellar:USDC:GA5ZSEJYB37JRC5AVCIA5MOP4RHTM335X2KGX3IHOJAPP5RE34K4KZVN",
      "price": "5.42",
      "decimals": 7
    }
  ]
}

##   GET /price
{
  "total_price": "5.42",      // 542/100
  "price": "5.00",            // 542/(100+8.40)
  "sell_amount": "542",
  "buy_amount": "100",
  "fee": {
    "total": "8.40",
    "asset": "stellar:USDC:GA5ZSEJYB37JRC5AVCIA5MOP4RHTM335X2KGX3IHOJAPP5RE34K4KZVN",
    "details": [
      {
        "name": "Service fee",
        "amount": "8.40"
      }
    ]
  }
}


##  POST /quote
##   GET /quote/:id

{
  "id": "de762cda-a193-4961-861e-57b31fed6eb3",
  "expires_at": "2021-04-30T07:42:23",
  "total_price": "5.42",        // 542/100
  "price": "5.00",              // (542-42)/100
  "sell_asset": "iso4217:NGN",
  "sell_amount": "542",
  "buy_asset": "stellar:USDC:GA5ZSEJYB37JRC5AVCIA5MOP4RHTM335X2KGX3IHOJAPP5RE34K4KZVN&",
  "buy_amount": "100",
  "fee": {
    "total": "42.00",
    "asset": "iso4217:BRL",
    "details": [
      {
        "name": "PIX fee",
        "description": "Fee charged in order to process the outgoing PIX transaction.",
        "amount": "12.00"
      },
      {
        "name": "Nigeria conciliation fee",
        "description": "Fee charged in order to process conciliation costs with intermediary banks.",
        "amount": "15.00"
      },
      {
        "name": "Service fee",
        "amount": "15.00"
      }
    ]
  }
}
