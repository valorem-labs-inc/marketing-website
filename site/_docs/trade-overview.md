---
date: 2023-06-02 00:00:00
title: Trade overview
description: Overview of Valorem Trade, a decentralized exchange for DeFi options.
---

[Valorem](https://valorem.xyz/) Trade is a decentralized exchange for
Valorem Clear options, settled on chain via
[Seaport](https://github.com/ProjectOpenSea/seaport). With Valorem Trade, users
can access professional market maker liquidity via an off chain
request-for-quote (RFQ) system. This professional market maker liquidity
allows users to trade options with low price impact and low fees. Valorem Trade
presents both a web interface and a gRPC API for interacting with the exchange.
It functions primarily as a signature relay between makers and takers in a given 
market.

The public endpoint for the exchange is `https://exchange.valorem.xyz`.

## How it works

Users connect to Valorem Trade via a web interface or gRPC API. They can then
act as a maker or taker. Takers sends requests for quotes (RFQs) to
makers, who then optionally respond with a signed offer, with some period of
validity, providing a look-back option for execution to the taker. The taker
then has the option to execute the offer, which is accomplished by submitting
the offer to the Seaport smart contract. The Seaport smart contract then
performs the requisite asset transfers.

### Off chain price discovery

This design allows options price discovery to occur off chain, while providing 
the security of on chain settlement.