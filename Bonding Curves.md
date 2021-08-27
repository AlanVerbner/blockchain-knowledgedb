# Bonding Curves

> ⚠ TODO: This is a WIP, I'm still learning about this

Recently - yes a little bit late ️🤦‍♀️ as the concept dates from 2017 - I got curious about [[Continuous Tokens]] and [[Curation Markets]] due to a tweet where someone mentioned that some funds were raised to fund medical research program in exchange for a participation in the Intellectual Property rights. Going down the rabbit hole I found [this article](https://medium.com/@simondlr/tokens-2-0-curved-token-bonding-in-curation-markets-1764a2e0bee5) written by Simon de la Rouviere which leds to this page as the main concept behind them are Bonding Curves.

Bonding curves are an interesting construction with multiple use cases being automatic market making the most common one. One of the first DApps that introduced this concepts (at least as far as I remember, but I would need to do more research) is [Bancor](https://bancor.network/).

A high level explainer would be: 

- There is a curve (linear, quadratic, exponential) that defines a relationship between price and token supply.
- Given an `A` amount of `TokenA` the contract would mint or return an amount `B` of `TokenB` such that the the price is determined by this curve. For example: 
    - If the curve is `y = m * x²` where
      - y = token price
      - x = token supply
      - n = exponent parameter
      - m = slope parameter
  	- When someone deposits the `A` will get in return as much as `B` tokens based on the pricing defined by the curve or, in other words, the buying / selling price is determined by the defined curve.
- As the curves are continuous and every time someone is buying or selling the price changes _a little bit_ the way to determine the amount of `TokensA` required to buy `TokensB` (or the other way around) requires to calculate the area under the curve, ie the integral. Implementing this process in solidity is not trivial and Bancor has defined something named Connector Weight which is an equivalent way to get the same result. [This](https://billyrennekamp.medium.com/converting-between-bancor-and-bonding-curve-price-formulas-9c11309062f5) is a really good reading material.
- Picking a different curve shape makes the price evolve differently achieving different goals, for example, making the price to react faster (exponential), to have a cap (logarithmic). More examples can be found [here](https://medium.com/thoughtchains/on-single-bonding-curves-for-continuous-token-models-a167f5ffef89)


As mentioned before, one of the most straightforward use cases is automatic market making, ie, there is a contract that's always willing to buy and sell at the current price. But there are other interesting ways to take advantages of this mechanism, for example, [[curation markets]] to measure users interest or [DAICOs](https://ethresear.ch/t/explanation-of-daicos/465) to raise fund for a specific project. 


## Reading material

- [An excellent bonding curve explainer](https://yos.io/2018/11/10/bonding-curves/)
- [An Aragon fundraising explainer](https://github.com/AragonBlack/fundraising/blob/master/docs/untitled-1.md)

