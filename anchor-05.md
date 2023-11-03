Summary 🔗

## This SEP defines the standard way for anchors and wallets to interact on behalf of users. This improves user experience by allowing wallets and other clients to interact with anchors directly without the user needing to leave the wallet to go to the anchor's site.

.   Deposit external assets with an anchor
.   Withdraw assets from an anchor
.   Execute deposit/withdraw between non-equivalent assets.
.   Communicate deposit & withdrawal fee structure for an anchor to the user
.   Handle anchor KYC needs, including transmitting KYC information about the user to  the anchor via SEP-12
.   Check the status of ongoing deposits or withdrawals involving the user
.   View history of deposits and withdrawals involving the user


API Endpoints 🔗

.   GET /deposit: required
.   GET /withdraw: required
.   GET /deposit-exchange: optional
.   GET /withdraw-exchange: optional
.   GET /info: required
.   GET /transactions: required
.   GET /transaction: required
