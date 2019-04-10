<script src="//www.90168.org cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## PageRank

---

#### `definition`
<p> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a way of measuring the importance of website pages.
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;works by counting the <b>number</b> and <b>quality</b> of links to a page, assuming that the more important a page is, the more likely it would <b>receive links</b> from other website.
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;numerical weight of element E: PR(E)
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;influenced by <b>citation analysis</b> and <b>Hyper Search</b>.
</p>

---

#### `importance`

<p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;developed in 1996 as part of a research about a new kind of search machine.<a href="#q2"><sup>[1]</sup></a>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;order websites in a hierarchy by "link popularity".
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;initial prototype of the Google search engine.
</p>

---

#### `algorithm`
<p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;outputs a probability distribution ~ the likelihood that a person randomly clicking on links will ultimately arrive at any particular page.
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;the distribution is evenly divided at the beginning of the computational process.
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;require several "iterations" to adjust approximate PR values to a close reflection of theoretical PR value.
</p>

+ pre-settings
   + ignore self-linking $L_{i\rightarrow i}$
   + multiple $L_{i\rightarrow j}$ == a single link
   + sink: a page with no outbound links $\rightarrow$ pick another URL at random $\rightarrow$ link out to all other pages.
+ PageRank for A,B,C,D
   + initial probability distribution

   | PR(A) | PR(B) | PR(C) | PR(D) |
   | ---- | ---- | ---- | ---- |
   | 0.25 | 0.25 | 0.25 | 0.25 |

   + iteration
      + PageRank trnasfered from a outbound link: the linking document's score divided by number of its outbound links <b>L( )</b>.
      + PR(A)=$\frac{PR(B)}{L(B)}+\frac{PR(C)}{L(C)}+\frac{PR(D)}{L(D)}$
      
   + damping factor d
      + the probability, at any step, that the random visitor will continue
      + the residual probability is estimated from the frequency that an average surfer uses the bookmark feature.
      + it is generally assumed that d $\approx$ 0.85.[$^{[2]}$](#q2)
      + PR(A)=$\frac{1-d}{N}+d(\frac{PR(B)}{L(B)}+\frac{PR(C)}{L(C)}+\frac{PR(D)}{L(D)})$
      + N denotes the number of documents
      + Page and Brin confused this formula in their most popular paper "The Anatomy of a Large-Scale Hypertextual Web Search Engine".


+ connection to Markov Chain
   + states $\rightarrow$ pages
   + transition $\rightarrow$ links, all equally probable
   + <span id="eigenvector">stochastic row vector</span> $R=  
     \begin{bmatrix}
      PR(p_1) \\
      PR(p_2) \\
      \vdots \\
      PR(p_n)
     \end{bmatrix}
     $
   + <span id="adjacency-matrix">transition rate matrix</span>
     $$
     R_{new}=\begin{bmatrix}
      \frac{1-d}{N} \\
      \frac{1-d}{N} \\
      \vdots \\
      \frac{1-d}{N}
     \end{bmatrix}
     +d
     \begin{bmatrix}
       l(p_1,p_1) & l(p_1,p_2) & \cdots &l(p_1,p_n)\\
       l(p_2,p_1) & \ddots & & \vdots\\
       \vdots & & l(p_i,p_j) & & \\
       l(p_n,p_1) & \cdots & & l(p_n,p_n)
     \end{bmatrix}R
     $$
   + adjacency function $l_a(p_i,p_j)=\left\{
        \begin{aligned}
           \frac{L_{j\rightarrow i}(j)}{L(j)}, & L_{j\rightarrow i}(j)\neq 0\\
           0, & L_{j\rightarrow i}(j)=0\\
        \end{aligned}
      \right.$
   + $l(p_i,p_j)$ is obtained by normalizing $l_a(p_i,p_j)$, such that
   $$\sum_{i=1}^{N}l(p_i,p_j)=1$$
   + a variant of the eigenvector centrality measure used commonly in network analysis.
   + a large eigengap of the [modified adjacency matrix](#adjacency-matrix), values of PageRank [eigenvector](#eigenvector) can be approximated to within a high degree of accuracy within only a few iterations.[$^{[3]}$](#q3)
   time complexity is roughly linear in O(log n).
   + As a result of Markov theory, the probability of arriving at A after a large number of clicks —— PR(A) = $t^{-1}$
   where t is the expectation of the number of clicks (or random jumps) required to get from A back to itself.
+ strategies to accelerate the compution of PageRank.[$^{[4]}$](#q4)
+ disadvantage
   + favor old pages, since new pages may not have many links
   + needs further improving search results rankings and monetizing advertising links

---
#### `computation`




---
#### `topics`

+ identify the most important page (the most likely page, which a random visitor would eventually arrive at) among UMJI official websites.

---
#### `source`
<blockquote>
<span id="q1">
Page, Larry, <a href="PageRank-Bringing Order to the Web.pdf">"PageRank: Bringing Order to the Web"</a>. Archived from the original on May 6, 2002. Retrieved 2016-09-11., Stanford Digital Library Project, talk. August 18, 1997 (archived 2002)
</span>
<br>
<span id="q2">
Brin, S.; Page, L. (1998). <a href="./The Anatomy of a Search Engine.pdf">"The anatomy of a large-scale hypertextual Web search engine"</a>. 
Computer Networks and ISDN Systems. 30 (1–7): 107–117. CiteSeerX 10.1.1.115.5930. doi:10.1016/S0169-7552(98)00110-X. ISSN 0169-7552. Archived from the original on 2015-09-27.
</span>
<br>
<span id="q3">
Taher Haveliwala & Sepandar Kamvar (March 2003). <a href="./The Second Eigenvalue of the Google Matrix.pdf">"The Second Eigenvalue of the Google Matrix"</a>. Stanford University Technical Report: 7056. arXiv:math/0307056. Bibcode:2003math......7056N. Archived from the original on 2008-12-17.
</span>
<br>
<span id="q4">
Gianna M. Del Corso; Antonio Gullí; Francesco Romani (2005). <a href="Fast PageRank Computation via a Sparse Linear System.pdf">"Fast PageRank Computation via a Sparse Linear System"</a>. Internet Mathematics. Lecture Notes in Computer Science. 2. pp. 118–130. CiteSeerX 10.1.1.58.9060. doi:10.1007/978-3-540-30216-2_10. ISBN 978-3-540-23427-2. Archived from the original on 2014-02-09.
</span>
</blockquote>


