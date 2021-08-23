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



  