# LNFiat
LNFiat aims to build trustless fiatcoins over the Lightning Network. 

Ultimate decentralisation would envision a fully decentralised exchange on which people can take derivative positions. Potentially a p2p protocol such as Holepunch could help here or (with the risk of swearing in church) a type of lightning network gossip. Any wallet would offer fiatcoin conversion and on the other hand the ability to take leveraged long bitcoin positions. Through a p2p protocol (such as Holepunch or lightning network gossip), someone looking to buy bitcoin backed fiatcoin, would issue an offer to sell a short swap. Others, or liquidity providers, for example LN Markets, would make make bids to lock in bitcoin at a certain fiat price.

![Trustless_fiatcoin2](https://user-images.githubusercontent.com/67538415/200856550-a8f41962-4775-4709-9c74-48e84a8a6d3c.svg)

Sellers and buyers would be matched - the dynamics are beyond the scope of this consideration. Once a seller and a buyer agree on a certain price, both parties would enter into a smart contract - in which one party has effectively bought the ‘fiatcoin’ value and the other party has a leveraged bitcoin position - the respective satoschis of both parties would be locked up - very similar to a lightning channel. Most likely, RGB or Taro can help to establish these smart contracts. An essential input is the exchange rate, which is an input to the smart contract. Again, the dynamics of the smart contract exchange rate is again beyond the scope of this consideration. Full trustless operation would be in a first instance be limited to protection against the exchange rate doubling or halving versus the original lock in exchange rate. One can conceive dynamics through which the wallet would automatically roll over the positions to protect the position at all time, e.g. after a 25% drop versus the locked in exchange rate. One would also have to evaluate the dynamics of the swap liquidation - again this is beyond the scope of this consideration.

This project requires three building blocks - the exchange rate 'oracle' can work based on a simple api call for the MVP - only needs development for robust production deployment: 

# p2p messaging protocol

Messages to exchange offers and bids: 
- Node x offers short at exchange rate y for volume z satoshis
- Node a buys short at exchange rate b for volume c satoshis

# Smart contract swaps on the lightning network

Locks up agreed satoshi volume of both parties
Describes position closing dynamics, e.g. 
- At agreed exchange rate (buy / sell prices communicated between parties)
- Fallback based on external oracle
Can RGB and Taro contracts be compatible? 

# Local order book building and swap rollover logic

- Can be custom built for each wallet
- Provides for wallet competitive advantage
- Builds local order book, based on information from p2p messaging protocol
- Continuously looks to improve swap position
- Ensures timely rollover to manage rollover risk
- Building requires little protocol knowledge, but significant financial understanding


