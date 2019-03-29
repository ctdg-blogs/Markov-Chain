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
    <td>CTMC, eg: Wiener process</td>
</tr>
</table>


+ DTMC
   + state space S={P[X<sub>i</sub>]}
   + described by a sequence of directed graphs
     + edge of n := P[X<sub>n</sub> -> X<sub>n+1</sub>]
     + omit edges with 0 transition probability

+ Time-homogeneous/Stationary Markov Chain
   + P[ X<sub>n+1</sub> = x | X<sub>n</sub> = y ] = P[ X<sub>n</sub> = x | X<sub>n-1</sub> = y ]
   + the transition probability is independent of n

+ Markov chain with memory 
   + order m := [#finite states the probability depends on]
   + Markov chain Y<sub>n</sub>=(X<sub>n</sub>,X<sub>n-1</sub>,...,X<sub>n-m+1</sub>)


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
<img align=center src="./StockMarket.png" alt="not found"></img>
   + transition matrix 

   <script type="text/javascript"
src="./MathJax.js">
</script>
<script type="text/x-mathjax-config">
var mathId = document.getElementsByClassName("math");
MathJax.Hub.Config({
tex2jax: {
   inlineMath: [['$','$'], ['\(','\)']],
   displayMath: [['$$','$$'], ["\\[","\\]"]]
}
});
MathJax.Hub.Queue(["Typeset",MathJax.Hub,mathId]);
</script>

<p class="math">
   $$
   \begin{bmatrix}
   \multirow{3}[0]{*}{P=}&
      & 0.9 & 0.075 & 0.025\\
      & 0.15 & 0.8 & 0.05\\
      & 0.25 & 0.25 & 0.5 
   \end{bmatrix}
   $$
</p>
   + distribution over states == stochastic row vector x 
   <br></br>
   <p class="math">
   $x^{\left(n+m\right)}=x^{\left(n\right)}\dot P^{m}$
  </p>

#### `applications`
##### describe systems that follow a chain of linked events, where what happens next depends only on the current state of the system
* cruise control systems in motor vehicles
* queues or lines of customers arriving at an airport
* exchange rates of currencies
* storage systems such as dams, and population growths of certain animal species.
* The PageRank algorithm for the internet search engine Google. 

