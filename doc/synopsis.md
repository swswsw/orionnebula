Synopsis
========

Code name: Orion Dex

Orion Dex is a decentralized token and contract exchange.  Orion Dex has no custodial or counterparty risk.  The user controls their own fund.  Orion Dex never controls the user's fund.  By using decentralized smart contract, Orion Dex cannot maliciously inappropriate user's fund.

## Uniqueness

Orion Dex is an exchange based on "discrete unit contract" (DUC), a concept that is created here.  In "discrete unit contract" exchange, a user who creates a maker order creates a new contract.  The contract is deployed to the network.  Each make order exists as its own contract.  Another users who wishes to take the contract can simply sends money to this contract address to receive the other side of token.  

## Advantages

One of the biggest issue with smart contract is hacking and unintended use.  A DUC contract will be very compact.  The less code on smart contract, the better.  In addition to reduce the attack surface, DUC contract will be easier to maintain and upgrade.  DUC also provide transparency to order book.

## Prose Description

The market maker (seller) creates the contract.  The contract will lock the selling token.  When buyer sends the required buying amount to the contract, the swap will take place.

## Structure

Pseuocode of an DUC contract

```
var tokenSell = {
  amount:
  type:
}

var tokenBuy = {
  amount:
  type:
}

function constructor() {
  lock the tokenSell
}


function exchange() {
  check if coin to buy are received
  send the tokenSell to buyer
  send tokenBuy to seller
}

function cancel() {
  return tokenSell to seller
  delete contract
}
```

## User Experience

### Creating the maker order

Although our contract source code will be open source and provided to public for their examination, it is unlikely that the user will create the contract by copy and paste our contract code.  Instead, an open source website will be provided for the user to create an order at the push of a button.  On the website's frontend, it will create and deploy the contract.  Since the contract is created on the frontend, it retain the complete decentralization and does not rely on trusting a middleman.  It is decentralized and non-proprietary, third-party can also create the website to provide the same service.  The user does not need to know how to create and deploy the contract.  The user can still view the contract created and verify the contract on other websites.  These other websites are called verifier websites.  A separate service will constantly running to check the integrity of the exchange website.  

### View the existing order

Service and website will browse the blockchain and display the orders to the user.  Providing an experience that is similar to either OTC site (eg. Huobi OTC) or exchanges (eg. GDAX)

An index service built by us or third parties can browse the blockchain and aggregate the orderbook.  Making it easier for the service or website to display the orders to the user.  More info about this on ## Index service section.  Website do not need to use the index service, but the index service makes things easier.

## Index service and API

An index service can look at the blockchain and aggregate the orderbook.  This is an optional component.  This service may be built by us or provided by a third party.  We define the contract spec.  A third party could index it from the public blockchain data.  The index service will provide an API that shows the orderbook and volume.  The index service API spec will be drafted.
