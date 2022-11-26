# p2p Fiat
p2p Fiat aims to build trustless fiatcoins over the Lightning Network. 

Humanity deserves a trustless permissionless technology with fiat stability. 

While prices are set in fiat terms, many people cannot afford the sort term volatility of bitcoin.  A few solutions are emerging to enable stability in fiat terms - on the basis of perpetual swaps with trusted counterparties - see at the bottom of this page for examples.  Ultimate decentralisation would envision a fully decentralised exchange on which people can take derivative positions to achieve stability in fiat terms. Potentially a p2p protocol such as [Holepunch](https://holepunch.to/) could help here or (with the risk of swearing in church) a type of lightning network gossip. Any wallet would offer fiatcoin conversion and on the other hand the ability to take leveraged long bitcoin positions. Through a p2p protocol (such as [Holepunch](https://holepunch.to/) or lightning network gossip), someone looking to buy bitcoin backed fiatcoin, would issue an offer to sell a short swap. Others, or liquidity providers, for example [LN Markets](https://lnmarkets.com/), would make make bids to lock in bitcoin at a certain fiat price.  

![Trustless_fiatcoin2](https://user-images.githubusercontent.com/67538415/200856550-a8f41962-4775-4709-9c74-48e84a8a6d3c.svg)

Sellers and buyers would be matched on the basis of local book building. Once a seller and a buyer agree on a certain exchange rate, both parties would enter into a fully collateralised swap smart contract - in which one party has effectively bought the ‘fiatcoin’ value and the other party has a leveraged long bitcoin position - the respective satoschis of both parties would be locked up - very similar to a lightning channel. Most likely, [Discrete Log Contracts](https://adiabat.github.io/dlc.pdf), [RGB](https://www.youtube.com/watch?v=Uy-JH7eOkk4) or [Taro](https://lightning.engineering/posts/2022-9-28-taro-launch/) can help to establish these fully collateralised swap smart contracts. An essential input is the exchange rate, which is an input to the smart contract. The established swap can ensure stable fiat value up to half the original exchange rate.  Swap rollover logic can help to automatically roll over the positions to protect the position at all time, e.g. after a 25% drop versus the locked in exchange rate. 

This project requires three building blocks - the exchange rate 'oracle' can work based on a simple api call for the MVP - only needs development for robust production deployment: 

# p2p messaging protocol

Messages to exchange offers and bids: 
- Node x offers short at exchange rate y for volume z satoshis
- Node a buys short at exchange rate b for volume c satoshis

![p2p2](https://user-images.githubusercontent.com/67538415/201062363-06678e6a-4e64-431c-9a3c-c89f1d77f650.svg)

# Fully collateralised smart contract swaps on the lightning network

Locks up agreed satoshi volume of both parties

Describes position closing dynamics, e.g. 
- At agreed exchange rate (buy / sell prices communicated between parties)
- Fallback based on external oracle

![contract](https://user-images.githubusercontent.com/67538415/201618153-60a8def4-c849-4167-8a0a-85cebdfe3cc6.svg)

Can RGB and Taro contracts be made to be compatible? 

# Decentralised oracles

Oracles are the remaining trust element.  
Bitcoin is secured and considered trustless on the basis that 51% of miners can be trusted. Trustless is trustverymany.  
The values transacted are on L1 large and hence require verymany untrusted counterparties for trust. 

Users looking for fiat stability, will probably peg for a small value, so most probably the number of counterparties can be smaller. So instead of trustverymany, one may be ok with trustmany.  

For simplicity, we will use here the example of 3 oracles - the oracle outcome can then be structured as a 2 of 3 key. Scaling to larger numbers of oracles is likely relatively trivial.  
A team of researcher has already described this in the [Paper 2022/499 - Practical Decentralized Oracle Contracts](https://eprint.iacr.org/2022/499). 

Multiple approaches can be used - one possible approach may be that people who exchange satoshis for fiat stability (typically in the background of the app) - also serve themselves as oracle. 

As inputs for the various oracles a stream of agreed exchanges / unwindings of swaps can be sent of the p2p signaling layers - effectively transmitting to the network the exchange rates approved by users.  

# Local order book building and swap rollover logic

- Can be custom built for each wallet
- Provides for wallet competitive advantage
- Builds local order book, based on information from p2p messaging protocol
- Continuously looks to improve swap position
- Ensures timely rollover to manage rollover risk
- Building requires little protocol knowledge, but significant financial understanding

![logic](https://user-images.githubusercontent.com/67538415/201326940-2588e171-d300-4e72-80b3-1afe38962320.svg)

# MVP

The MVP can compromise on the permissionless nature of p2p Fiat: an MVP can build on a centralised exchange book building - and focus on establishing the fully collaterlised smart contract swaps.  

# Thank you - inspiration

This project is inspired by [Galoy](https://galoy.io/) [Stablesats](https://stablesats.com/).  You can test that project in the [Bitcoin Beach Wallet](https://www.bbw.sv/).  p2p Fait aims to make the swaps fully p2p trustless and permissionless, whereas [Stablesats](https://stablesats.com/) depends on perpetual swaps by their [Dealer](https://github.com/GaloyMoney/dealer) through the [CryptoCurrency eXchange Trading Library](https://github.com/ccxt/ccxt) with [OKX](https://www.okx.com/) at this stage - albeit with an ambition to diversify and partner with [Kollider](https://kollider.xyz/), who are building a (custodial) [browser plugin wallet](https://kollider.xyz/wallet). 

It seems the [Human Rights Foundation](https://hrf.org/) and [Strike](https://strike.me/) have launched a [bounty challenge](https://hrf.org/strike-hrf-bounty) on December 20, 2021 with exactly the challenge as described above.  This is an open call for anyone to team up.  
