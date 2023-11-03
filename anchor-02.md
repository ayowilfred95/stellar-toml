SUMMARY 🔗

Deposit and Withdrawal API #

.   Deposit external assets with an anchor
.   Withdraw assets from an anchor
.   Communicate deposit/withdrawal fee structure for an anchor to the user
.   Handle anchor KYC needs
.   Check the status of ongoing deposits or withdrawals involving the user
.   View history of deposits and withdrawals involving a user

N:B
    Before continuing deposit and withdrawal process, make sure that you,ve already the Anchor Platfrom installed and configured necessary features


## The complete customer experience a deposit and withdrawal goes something like this:

1.  The customer opens the SEP-24 wallet application of their choice
2.  The customer selects an asset to deposit and the wallet finds an anchor (clients   could also chose the specific anchor)
3.  Once the wallet authenticates with the anchor, the customer begins entering their KYC and transaction information requested by the anchor
4.  The wallet provides instructions, and the customer deposits real fiat currency(Naira) with the anchor (e.g. makes a bank transfer)
5.  Once the wallet receives the deposit, the customer receives the tokenized asset on the Stellar network from the anchor's distribution account


API Endpoints 🔗

POST /transactions/deposit/interactive
POST /transactions/withdraw/interactive
GET /info
GET /fee: 
GET /price endpoint should be used to communicate fees and exchange rates.
GET /transactions
GET /transaction


Asset Exchanges 🔗
### Exchange between off-chain and on-chain non equivalent assets like NGN <> USDC

#### To support the exchange of non-equivalent assets using this protocol, the anchor must allow users to select the off-chain asset they would like to provide or receive (for deposit and withdrawal, respectively) within the anchor's interactive flow. The anchor should then display an exchange rate to the user in addition to any fees charged for facilitating the transaction. Whether this exchange rate is binding or an estimate is up to the anchor, but this distinction must be communicated to the user.
