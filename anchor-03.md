Simple Summary 🔗

This SEP defines a protocol for enabling payments between two financial accounts that exist outside the Stellar network

API Endpoints 🔗

1.   GET /info  (Allows an anchor to communicate basic info about what currencies their DIRECT_PAYMENT_SERVER supports receiving from partner anchors.)
2.   POST /transactions     (This request initiates a payment. The Sending and Receiving Client must be registered via SEP-12 if required by the Receiving Anchor.)
3.  GET /transactions/:id   (GET DIRECT_PAYMENT_SERVER/transactions/:id
The transaction endpoint enables Sending Clients to fetch information on a specific transaction with the Receiving Anchor.)
4.  PATCH /transactions/:id ()
5.  PUT /transactions/:id/callback
