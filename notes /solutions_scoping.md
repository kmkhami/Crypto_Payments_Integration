# Solutions Scoping 

## Coinbase Integration 
Same steps for binance or any other competitor 

#### Pros 
* Easiest and fastest solution 
* Liability removal 
* Minimal logistics 

#### Cons
* Would require merchants to use Coinbase 
* Coinbase transaction fees 
* Low flexibility 
* Requires users to add Payment Methods to Coinbase if they want to buy/sell crypto

#### High Level Steps 
1. [Integrate Coinbase connect OAuth2](https://developers.coinbase.com/docs/wallet/coinbase-connect/integrating) - **Required for MVP**
    * Would need to CoinBase userID token to user data in PaymentSpring db
    * Need to specify scopes needed 
    * Need front-end form to handle this 
2. [Integrate Users resource endpoints](https://developers.coinbase.com/api/v2?shell#users) -- Optional for MVP
    * This is public information like name, username, bio, avatar, etc. 
    * Mostly a front-end task of displaying the information 
3. [Integrate Accounts Endpoint](https://developers.coinbase.com/api/v2?shell#accounts) -- Optional for MVP
    * Users can have multiple accounts/wallets for different currencies 
    * We would need to fetch the primary account and display its information 
    * Mostly a front-end task of information display
4. [Integrate Address Endpoint](https://developers.coinbase.com/api/v2?shell#address-resource) - **Required for MVP**
    * One time use wallet addresses for payments 
    * Transactions can be queried for just a single address 
5. [Integrate Transactions Endpoint](https://developers.coinbase.com/api/v2?shell#transactions) - Optional for MVP 
    * Query and display transaction history 
    * Allows users to send funds 
    * Allows users to request funds via emails and can be re-requested or canceled 
6. [Integrate Buy/Sell/Deposit/Withdrawal Endpoints](https://developers.coinbase.com/api/v2?shell#sells) - Very Optional for MVP 
    * Allows users to buy/sell crypto from Coinbase 
    * Any combination of the endpoints could be integrated or none
    * Payment method are also a part of this

## CryptoAPI Integration 
Middle-End Solution 
Same steps as coinbase after the list

#### Pros 
* Middleground solution 
* More flexibility 
* Lower fees 

#### Cons
* Requires more infrastrucure building 
* Doesn't allow for purchase/sale of coins 
* No way for payment method integration/continuation 
* Makes PaymentSpring responsible for things like wallet passwords, transaction speed, transaction fees, omni layer, etc.  
* Heavy logistics 

#### High Level Steps 
1. [Allow merchants to create a deposit address](https://developers.cryptoapis.io/technical-documentation/wallet-as-a-service/generating/generate-deposit-address) 
    * Associate deposit address with user data 
    * Front end form to allow customers to create these 
    * Would replicate the Coinbase wallet 
    * This can be repurposed for multiple currencies like Coinbase ```Accounts```
2. [Forwarding Endpoint](https://developers.cryptoapis.io/technical-documentation/blockchain-automations/automatic-tokens-forwarding/create-automatic-tokens-forwarding)
    * When accepting payment, generate another address and enable automatic forwarding for privacy reasons 
3. [Create Transactions View](https://developers.cryptoapis.io/technical-documentation/blockchain-data/unified-endpoints/list-transactions-by-address)
4. [Set Up Wallet Service](https://cryptoapis.io/products/wallet-as-a-service)
    * Need to schedule a meeting with Cryptoapi to talk about this 
    * Seems to be supported, but not in their public APIv2 docs 
5. Broadcast Transaction and locally sign transaction 
    * Need to talk to CryptoAPI about this

## Building from scratch 

### Pros
* Full control 
  
### Cons 
* Is the hardest 

### Requirements 
1. It must generate the required Bitcoin addresses.
2. The wallet needs to recognize transactions and be able to send funds to the above-mentioned addresses.
3. At the other end of the spectrum, the wallet needs to recognize and process Bitcoin transactions being received from other addresses.
4. The wallet must store the transaction history, and be able to show it when needed. Remember, Bitcoins are basically just digital transaction histories.
5. The wallet needs to be able to handle the impacts of the Bitcoin blockchain database reorgs and other conflict resolution actions undertaken by the Bitcoin community.
6. Bitcoin transaction fees vary, based on several factors. The wallet should be able to dynamically calculate the fees based on the latest rates.
7. Must be able to build and sign Bitcoin transactions.
8. Upon completion of the transaction, the wallet needs to broadcast the transaction to the Bitcoin blockchain.

### Rough High Level Steps 
1. Do 'Initial Blockchain Downloading' or IBD 
2. Start a new Node 
3. Pick an [RPC](https://developer.bitcoin.org/reference/rpc/)

### General Notes
* Pieces 
  * Public key distribution program (on the node)
  * Signing Program 
  * Networked Program 
* [Setup Local Monero Node/Wallet From Scratch](https://freedomnode.com/blog/how-to-install-and-set-up-full-monero-node-on-linux/)