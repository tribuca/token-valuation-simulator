# Token Price Appreciation Simulator
We are working deeply on how BUCA would be valued as a means of exchange, store of value, and unit of account. Therefore, we've been researching on simulating tokenized Tribuca ecosystem. One starting point is the agent-based modeling that’s coming out of the fields of complexity science and artificial general intelligence. Another is modeling as a set of differential equations (DEs).

One of the theories of research is about a dynamic asset pricing model of cryptocurrencies/tokens that allows users to conduct peer-to-peer transactions on digital platforms. We’ve been reviewing and getting references from research is Tokenomics: Dynamic Adoption and Valuation [1].

> [1] Cite: Lin William Cong, Ye Li, Neng Wang, Tokenomics: Dynamic Adoption and Valuation, The Review of Financial Studies, Volume 34, Issue 3, March 2021, Pages 1105–1155, https://doi.org/10.1093/rfs/hhaa089 

This research models agents’ gain from blockchain transactions as a flow utility that depends on agent-specific transaction needs, the size of the blockchain community, and the current productivity of blockchain platform (“productivity” broadly interpreted) that loads on exogenous shocks.

A key innovation of this model is that not only does one user’s adoption exhibit externality on others, but the investment motive also introduces an inter-temporal complementarity in the user base. The key driver is again the agents’ investment motive— their decision to participate depends on their expectation of future token price appreciation. The economic mechanism of this model is depicted following figure.

[Figure: Adoption-accelerating effect of tokens](https://academic.oup.com/view-large/figure/228030102/hhaa089f1.tif)

> “The green arrows point to the increases of the current and future (expected) levels of productivity A, which lead to higher flow utilities of tokens, and in turn, larger user bases N as highlighted by the black arrows. The blue arrows show that increases in user base result in even higher flow utility due to the contemporaneous network externality. Finally, more users push up the token prices P in future dates, which feed into a current expectation of token price appreciation, leading to greater current adoption.”

Based on this model, an open-source application has been developed by [Junki Yuasa](https://github.com/melonattacker). So that we commit to further developing this model both incorporating token market illiquidity and serving as a means of payment among platform users that tokens can compensate resource contributors and reward platform founders and entrepreneurs.

Since tokens affect the user-base dynamics, endogenous adoption is critical for understanding major asset pricing issues surrounding tokens, the model employs the ordinary differential equation for token valuation.

We run the application to simulate a token price appreciation according to the below parameters
| Parameters | Type(python) | Default value | Description |
|:---|:---:|:---:|:---:|
|period | int | 365 | Period(days) you simulate the price.|
|agents | int | 1000 | Number of people who may hold tokens. |
|times | int | 1 | Number of simulations. |
|beta | float | 0.3 | productivity beta (systematic risk) - generates an initial rise of token price followed by a decline and eventual stabilization, broadly consistent with the observed “bubbly” price dynamics. |
|chi | float | 1.0 | Scaling effect on Productivity. |
|interest_rate | float | 0.005 | Risk-free rate. |
|token_supply | int | 1000000000 | Token supply amount (fixed). |
|BUCA (price) | float | 0.003 | Expected rate of return. |
|initial_value (productivity) | float | 100.0 | Initial value of productivity. |
|BUCA (productivity) | float | 0.0025 | Average of productivity. |
|sigma (productivity) | float | 2.0 | The standard deviation of productivity - is a unit to express failure rate. |
|BUCA (utility) | float | 1.0 | Average utility of agents. |
|sigma (utility) | float | 10.0 | The standard deviation of the utility of the agents - gives insight into what happens to worst-case/n-sigma performance when controllable variables get changed. |

When we increase the user (agent) numbers, it may indicate that a lower adoption now means more agents can be brought onto the platform in the future. Agents expect stronger token price appreciation, therefore, inducing them to adopt and hold tokens. 

Similarly, a positive productivity shock increases adoption by increasing the flow utility. However, as the pool of potential newcomers shrinks, the expected token price appreciation declines, discouraging agents from joining the platform and holding tokens. Apparently, through the token price that reflects agents’ expectations, the popularity of a platform in the future increases the present user base.
