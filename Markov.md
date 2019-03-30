<script type="text/javascript"
       src="/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>


## Markov Chain

---
### [Markov Property](https://en.wikipedia.org/wiki/Markov_property)

* the momoryless property of a stochastic/ramdom process
* the `conditional probability distribution` Y|X=t<sub>0</sub>  of future states of the process `depends only upon the present state`, not on the sequence of events that preceded it. 
* P(X<sub>n</sub>=x<sub>n</sub>|X<sub>n-1</sub>=x<sub>n-1</sub>,...,X<sub>0</sub>=x<sub>0</sub>)=P(X<sub>n</sub>=x<sub>n</sub>|X<sub>n-1</sub>=x<sub>n-1</sub>)

---

### [Markov Chain](https://en.wikipedia.org/wiki/Markov_chain)

#### `definition`
* A discrete-time stochastic process satisfying the Markov property
* a type of Markov process that has either a discrete state space or a discrete index set (often representing time), regardless of other variables.

#### `classification`
<table>
<tr>
    <th></th>
    <th>Countable state space</th>
    <th>Continuous/General state space</th>
</tr>
<tr>
    <th>Discrete Time</th>
    <td>DTMC</td>
    <td>Harris Chain</td>
</tr>
<tr>
    <th>Continuous Time</th>
    <td>Markov jump process</td>
    <td>Any continuous stochastic process with the Markov property, eg: Wiener process</td>
</tr>
</table>


+ DTMC
   + state space S={P[X<sub>i</sub>]}
   + described by a sequence of directed graphs
     + edge of n := P[X<sub>n</sub> -> X<sub>n+1</sub>]
     + omit edges with 0 transition probability
     + $\sum_{i=1}^{dim S}$ [$p_{ai}$] = 1, $\forall a$
+ Time-homogeneous/Stationary Markov Chain
   + P[ X<sub>n+1</sub> = x | X<sub>n</sub> = y ] = P[ X<sub>n</sub> = x | X<sub>n-1</sub> = y ]
   + the transition probability is independent of n

+ Markov chain with memory 
   + order m := [#finite states the probability depends on]
   + Markov chain Y<sub>n</sub>=(X<sub>n</sub>,X<sub>n-1</sub>,...,X<sub>n-m+1</sub>)

+ CTMC $X_t\vert _{t\geq0}$
   + finite/countable state space S
   + transition rate matrix Q, dim Q = dim S
      + $q_{ij}$ = P[state i -> state j]
      + $q_{ii}$ = 0 - $\sum$ [$q_{ij}$ in the row]
   + infinitesimal definition
      + P[$X_{t+h}$= $j$ | $X_{t}$ = $i$ ] = $\delta_{ij}$ + $q_{ij}h$ + $o(h)$
      + Kronecker delta $\delta_{ij}=
      \left\{
        \begin{aligned}
           0, & i\neq j\\
           1, & i = j\\
        \end{aligned}
      \right.
      $
      + $q_{ij}$ := how quickly i -> j happens
   + jump-chain/holding-time definition 
      + $Y_n$ := DTMC denoting the nth jump of the process
      + $S_i$ := holding times in each of the states, following exponential distribution with rate parameter $-q_{Y_i Y_i}$
   + transition probability definition
      + P[$X_{t_{n+1}}=i_{n+1}$ | $X_{t_0}=i_0$,...,$X_{t_n}=i_n$]=$p_{i_ni_{n+1}}$ ($t_{n+1}-t_n$)
      + $p_{i_ni_{n+1}}$ is elements of the matrix of solution of the equation: P'(t)=P(t)Q, with IC : P(0)= $I$

#### `examples`

+ Gambling
   + fair coin toss
   + start with $10
   + X<sub>n</sub> := [#dollar you got]
   + DTMC

+ Birth-death process
   + 100 popcorn
   + each poping at an indipendent exp-distributed time
   + X<sub>t</sub> := [#corns popped up to time t]
   + CTMC -- Poisson point process

+ Hypothetical stock market
<img align=center src="./StockMarket.png" width="500px" height="auto" alt="not found"></img>
   $$P=
   \begin{bmatrix}
      & 0.9 & 0.075 & 0.025\\
      & 0.15 & 0.8 & 0.05\\
      & 0.25 & 0.25 & 0.5 
   \end{bmatrix}
   $$

   + distribution over states == stochastic row vector x 
   $x^{\left(n+m\right)}=x^{\left(n\right)}\times P^{m}$
   + steady-state probability
   $$\lim_{n\rightarrow +\infty}P^N=
   \begin{bmatrix}
      & 0.625 & 0.3125 & 0.0625\\
      & 0.625 & 0.3125 & 0.0625\\
      & 0.625 & 0.3125 & 0.0625 
   \end{bmatrix}
   $$
   which indicates that 62.5% will be a bull market, 31.25% bear market, and 6.25% stagnant.
  

#### `applications`
##### describe systems that follow a chain of linked events, where what happens next depends only on the current state of the system
* cruise control systems in motor vehicles
* queues or lines of customers arriving at an airport
* exchange rates of currencies
* storage systems such as dams, and population growths of certain animal species.
* The PageRank algorithm for the internet search engine Google. 

