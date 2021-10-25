# EE4C06 Networking

## Graph Theory

### Week 1
- Adjacency matrix: $A$
  - walk成为一个 path 需要所有的顶点都不相同。它是 trail 需要所有的边不相同。一个图是连通的需要对任意两个顶点，有 path 连接它们。一个 cycle 是一个闭的 path，一个 tree 是不含 cycle 的连通图。
  - complementary Adjacency matrix: $A^c=u\cdot u^T - I - A$
  - subgraph Adjacency matrix, $A = \begin{bmatrix}A_s & B \\ C & A_{G\setminus S}\end{bmatrix}$, $C=B^T$
  - Number of k-hop walks between node $i$ and $j$: $(A^k)_{ij}$
  - Total number of k-hop walks in G: $N_k=u^TA^ku=\Sigma_{i=1}^N\Sigma_{j=1}^N(A^k)_{ij}$
  - Total number of closed k-hop walks in G: $W_k=\Sigma_{j=1}^N(A^k)_{jj}=trace(A^k)$
- Incidence matrix: $B$, $u^T\cdot B=0$
- Laplacian matrix: $Q=B\cdot B^T$
- degree of nodes: $d=A \cdot u$
  - Regular graph: all nodes have the same degree
  - degree & #link: $u^Td = u^TAu=\Sigma_{j=1}^N d_j = 2L$ \
    $\to 2-\frac{2}{N} \leq E[D]=\frac{1}{N}\Sigma_{j=1}^N d_j = \frac{2L}{N} \leq N-1$ (connected graph)
  - degree of Adjacency matrix: $d_j = (A^2)_{jj}$ 
  - At least two nodes in G have the same degree
  - The number of nodes with odd degree is even
- links of graph:
    - Tree: $L = N - 1$
    - Ring: $L = N$
    - Complete graphL $L=N(N-1)/2$
- Clustering coefficient: $C_G(V)=\frac{2y}{d_v(d_v-1)} \leq 1$, where y is the number of links between neighbors. If $d_v=1$, $C_G(V)=0$
  - It measures the local density around node $v$
  - The clustering coefficient of a graph G: $C_G=\frac{1}{N}\Sigma_{v=1}^N C_G(v)$
  - Another definition: $C_G=\frac{6 \times \# triangles}{N_2-W_2}=\frac{trace(A^3)}{d^Td-2L}=\frac{\Sigma_{j=1}^N(A^3)_{jj}}{\Sigma_{i=1}^Nd_i(d_i-1)}$
- Hopcount: Hopcount from node $i$ to node $j$: $H_{i\to j}=h(P^*_{i\to j})$ where $P^*_{i\to j}$ is the shortest hop path from $i$ to $j$
  - diameter $\rho$ of $G$: hopcount of the longest shortest path in $G$. The average hopcount $E[H]$ reflects "efficiency" of transport in $G$.
  - The shortest walk between $i$ and $j$ is also a shortest path, $H_{ij}=k$
  - faster test of $\rho$: test till $(1+A)^\rho$ contains no zero
- Betweenness: The betweenness $B_l$ / $B_n$ of a link $l$ / node $n$ equals the number of shortest paths traversing link $l$ / node $n$ in $G$
  - The average betweenness: $H_G=\Sigma_{i=1}^N\Sigma_{j=i+1}^NH_{ij}=\Sigma_{l=1}^LB_l$ \
  $\to E[B_l]=\frac{1}{L}\Sigma_{l=1}^LB_l=\frac{1}{L}\begin{pmatrix}N \\ 2\end{pmatrix}E[H_G]$, where $H$ is the distance matrix
- Degree Assortativity: $\rho_D=\frac{N_1N_3-N_2^2}{N_1\Sigma_{j=1}^Nd_j^3-N_2^2}$
  - A network is (degree) assortative if $\rho_D>0$
  - A network is (degree) disassortative if $\rho_D<0$
  - Degree-preserving rewiring (DPR) only changes Degree Assortativity rather than the degree itself.
- Connectivity of a Graph: $\lambda(G)$ (or $\mathcal{k}(G)$): the minimum number of links (or nodes) whose removal disconnects G
  - Menger's Theorem: The maximum number of Link(node)-disjoint paths between A and B is equal to the minimum number of links(nodes) disconnecting A and B
  - If the graph G is disconnected, then its complement $G^c$ is connected

### Week 2

- Spectrum of A:
  - $d_{max}\geq \lambda_1\geq \frac{2L}{N}=E[D]$
    - $\lambda_1 \geq E[D]\sqrt{1+\frac{Var[D]}{E^2[D]}}$
  - all eigenvalues lie in the interval $(-d_{max},d_{max}]$
  - $\Sigma_{j=1}^N\lambda_k^k=trace(A^k)=\Sigma_{i=1}^N(A^k)_{ii}=W_k$ (total number of closed walks)
    - $\Sigma_{j=1}^N \lambda_j = 0$ 
    - $\Sigma_{j=1}^N \lambda_j^2 = 2L$ 
    - $\Sigma_{j=1}^N \lambda_j^3 = 6\times triangles$
  - $\lambda_1$ and components of eigenvector $x_1$ are non-negative (when reducible, $\equiv 0$)
  - The radius is bounded: $E[D]\sqrt{1+\frac{Var[D]}{E^2[D]}} \leq \lambda_1 \leq d_{\max}$ 
- Spectrum of Q:
  - any eigenvalue $\mu_k$ is non-negative and smallest $\mu_N=0$
  - complexity (number of spanning tree) is $\xi(G)=\frac{1}{N}\prod_{k=1}^{N-1}\mu_k$
  - algebraic connectivity $a(G)=\mu_{N-1}$. The graph $G$ is only connected if and only if $a(G)=\mu_{N-1}>0$. The graph $G$ with larger $a(G)$ is more difficult to disconnect
- The number of links between $G_1$ and $G_2$: $R=\frac{1}{4}y^TQy$, $y_i=1$ if $i\in G_1$, else $y_i=-1$ if $i\in G_2$\
  - $R=\frac{1}{4}\Sigma_{j=1}^N \alpha_k^2u_j$
  - $R \geq \frac{1}{4}(y^Tz_{N-1})^2\mu_{N-1}$
- Degree-preserving rewiring:
  - Largest eigenvalue of adjacency increases with degree assortativity $\rho_D$
  - while algebraic connectivity decreases which implies that increasing assortativity creates more disconnected components.
---
- Erdos-Renyi random graph
  - $a_{ij}$ is a bernoulli random variable with mean $\rho$
  - $E[a_{ij}]=\rho$
  - the complement graph of $G_p(N)$ is $G_{1-p}(N)$
  - the average number of links: $E[L]=\frac{N(N-1)}{2}\rho$
  - the average cluster coefficient is $E[C_{G_p(N)}]=\rho$
  - $Pr[D=k]=\begin{pmatrix}N-1 \\ k\end{pmatrix}p^k(1-p)^{(N-1-k)}\approx \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{(k-\mu)^2}{2\sigma^2}}$
    - $\mu=(N-1)\rho$ and $\sigma^2=(N-1)\rho(1-\rho)$
    - $\rho$ constant, $N\rightarrow\infty$ => tendency towards a regular graph
    - $E[D]$ constant, $N\rightarrow\infty$ => $Pr[D=k]$ becomes Poisson distribution
    - the critical link density: $\rho_c \sim logN/N$
    - $\rho_c$ small, compact $f_\lambda(x)$, high spike at zero, graph tends to be disconnected; $\rho_c$ large, disperse $f_\lambda(x)$, lower spike at zero, graph tends to be connected.
  - rewiring makes clustering coefficient and average hotcount lower
  - $f_\lambda(-x)=f_\lambda(x)$ refers a tree graph

- Power-law graph (scale-free)
  - $Pr[D=k]=ck^{-\tau}$
  - The mean is not representative, because the variance is (very) large
  - robustness to random node failure
  - vulnerability to targeted hub attacks and cascading failures


## Electrical Networks

### Week 3
- Kirchhoff's Current Law: $By=x$, if no current injections, then $By=0$
- Ohm's Law: $diag(\frac{1}{r_l})B^Tv=y$, if all resistance is 1 $\omega$, then $B^Tv=y$
- Deductions:
  $$
  B(B^Tv)=x \to BB^Tv=x \to Qv=x \text{ (unit resistance)}
  $$
  
  $$
  B(diag(\frac{1}{r_l})B^Tv)=x \to \widetilde{Q} v=x \text{ (non-unit resistance)}
  $$
- Heterogeneous Resistance:
  $$x=\widetilde{Q}v$$
  - $\widetilde{Q}=Bdiag(\frac{1}{r_l})B^T$
  - $\widetilde{Q}=\widetilde{\Delta}-\widetilde{A}$ ($\widetilde{a}_{ij}=\frac{1}{r_{ij}}a_{ij}$)
- Pseudo inverse of the Laplacian: $Q^+=\Sigma_{k=1}^{N-1}\frac{1}{\mu_k}z_kz_k^T$
  - $Q^+x=v-v_{avg}u$
- effective resistance matrix:
  - $\omega = u\xi^T + \xi u^t - 2Q^+$
    - $\xi=diagonal(Q^+)$
  - $R_G=\frac{1}{2}u^T\omega u=N\times trace(Q^+)=N\Sigma_{k=1}^{N-1}\frac{1}{u_k}$


## Robustness of Networks

### Week 4

- R-model: $R=\Sigma_{k=1}^m s_kt_k = s^Tt$, $0 \leq R \leq 1$
  - $s$: the service vector with m components (interpreted as weights)
  - $t$: the topology vector where each of the m components is a graph metric
  - R model is linear
  - Normalize $s$ and $t$, $R=\frac{s^Ts}{\sqrt{(s^Ts)(t^Tt)}}$
  - R = 0 (absence of network robustness); R = 1 (perfect robustness)

- Robustness Envelopes
  - Stochastic approach:
  ![](./images/stochastic-approach.png)
  - Envelope definitions:
  ![](./images/envelope-definitions.png)
    - Low sensitivity (blue area) results in better stability
    - High energy (red area) results in better average R-value
  - Different attacks (different strategies to remove links) influence differently:
    - targeted attacks: coreness, betweenness, closeness, degree, elgenvector
    - betweenness, pseudo-inverse laplacian, closeness often impact most

- Failure recovery:
  - Scenario A: adding links uniformly at random in the complementary graph after attack until the normalized R-value reaches 1: $\eta=\frac{K_{attack}}{K_{recovery}}$
  - Scenario B: adding links which are removed in the attack process until the network returns to the original: $\eta=\frac{S_{recovery}}{S_{attack}}$
  ![](./images/scenarioB.png)

## Traffic Management

### Week 4

- Statistical Multiplexing: multi sources use the same bandwidth simultaneously to reduce the PCR (Peak Cell Rate)
- On-Off source:
  ![](./images/on-off-source.png)
- Burstiness Constraint: $L(u,t)=\int_u^t\lambda(\tau)d(\tau)\leq\overline{\sigma}+\overline{\lambda}(t-u)$
  - $L(u,t)\leq max_{\tau\in[u,t]}\lambda(\tau)(t-u)$
  - $\lim_{t\to\infty}\frac{L(u,t)}{t-u}=\overline{\lambda}+\lim_{t\to\infty}\frac{\overline{\sigma}}{t-u}$
- Input Control:
  - This is the result of input control:
    ![](images/input-control.png)
  - This is the method of input control:
    ![](images/token-bucket.png)
- QoS (quality of service)
  - Loss
  - Delay
- Connection Admission Control (CAC): Acceptance rules for new connection requests in order to guarantee the quality of service (QoS) for multimedia services in B-ISDN
- Congestion: 
  System buffers fill up $\to$ Loss and retransmission $\to$ More traffic, more loss $\to$ **Positive feedback** $\to$ System collapse

## Scheduling

### Week 6
- Head of the Line (HoL) vs. Partial Buffer Sharing (PBS) vs. Push-Out Buffer (POB)
  - HoL: always serves high priorities in the buffer before low priorities
  - PBS: below the threshold T: identical to FIFO and sequence order is preserved; above threshold T: only a high priority accepted until buffer is full
  - POB: when an arrival of high priority cell,
    - LIFO POB: the last entered low priority cell is discard
    - Random POB: a randomly chosen low priority cell is pushed out
    - FIFO POB: the first entered low priority cell is discard

- Multiplexing of regulated flows:
  $$Q_t=\sup_{s<t}[\sum_{k=l}^K L_k(s,t) - \mu(t-s)] \leq \sup_{s<t>}[\sum_{k=l}^K L_k(s,t) - \lambda_k(t-s)] \leq \sum_{k=l}^K \sigma_k = G] $$

- N*D/D/1 queue:
  $$Pr(N_s>G)=clr$$
  $$Pr[N_s>x]=\exp(-\frac{2x^2}{N})\exp(-\frac{2x(1-\rho)}{\rho})$$
  In the worst case scenario $\rho\to 1$, then $clr\approx\exp(-\frac{2x^2}{N})$

  If the buffer size x = G, then the number Ns of flows is approximately,
  $$N_s=\frac{2G^2}{-\ln(clr)}$$