# 2015

1. spectral radius of adjacency matrix

$$E[D]\sqrt{1+\frac{Var[D]}{E^2[D]}} \leq \lambda_1 \leq d_{\max}$$

2. Head of the line (HoL) with non-preemptive mode

3. Erdos-Renyi, Betweenness

    $E(B_l)=\frac{1}{L}\cdot\frac{N(N-1)}{2}E(H_N)=\frac{1}{L}\cdot\frac{N(N-1)}{2}\cdot(\Pr[H_N=1]+2\Pr[H_N=2])$

    $=\frac{1}{\frac{N(N-2)}{2}\rho}\cdot\frac{N(N-1)}{2}\cdot(\rho(1-\rho)+2(1-\rho)(1-(1-\rho^2)^{N-2}))$

    $\lim_{N\to\infty} =\frac{1}{\rho}(\rho+2(1-\rho))=\frac{2-\rho}{\rho}$

4. diameter, clustering coefficient, connectivity

   diameter = the longest shortest path
   clustering coefficient = $\frac{2y}{d_v(d_v-1)}$

   higher connectivity $\sim$ higher $\mu_{N-1}$ 

5. R-model/R-value: $R=\sum_{k=1}^m s_tt_k$
   
   R is between [0,1]

   R model is linear

   All the $m$ metrics should be orthogonal to each other (Ideally)

6. K-hop walk, closed walk
   
   k-hop walk: $N_k=\sum_i\sum_j(A^k)_{ij}$

   closed k-hop walk: $W_k=\sum_j(A^k)_{jj}=\sum_idiag(A^k)_i$

7. token bucket, burstiness

8. Erdos-Renyi

9. CAC = Connection Admission Control

10. electrical graph, effective resistance

11. graph, histogram

12. different between walk and path
    - walk: Vertices may repeat. Edges may repeat (Closed or Open)
    - path: Vertices cannot repeat. Edges cannot repeat (Open)
  
13. complete graph, the spectrum of the Laplacian matrix
    
    $\mu=[N, N, N,...,0]$

14. Tree


# 2016

1. spectral radius of adjacency matrix

$$E[D]\sqrt{1+\frac{Var[D]}{E^2[D]}} \leq \lambda_1 \leq d_{\max}$$

   regular graph 取下界 (Var=0), complete graph 取上界

2. Erdos-Renyi degree distribution
   
   Degree distribution: Binomial distribution, when $N \to \infty$ it becomes Gaussian distribution 

3. spectrum of adjacency matrix
   
   the sum of the eigen values of A is 0

4. **complete graph**, spectrum of adjacency matrix
   - number of triangles:
      $$\sum_{j=1}^N \lambda_j^3=N(N-1)(N-2)=6#triangle$$
   - number of links:
      $$\sum_{j=1}^N \lambda_j^2=N(N-1)=2L$$
   - $\sum_{j=2}^N \lambda_j = -\lambda_1=1-N$

5. DPR, assortative 
6. average eigenvalue $E[\mu]$ 
   
   代入法, suppose that $p=1$, only A is correct
7. PBS 
   - Below threshold T: identical to FIFO and sequence order is preserved
   - Above threshold T: only a high priority cell regime until buffer is full
8. clustering coefficient, average clustering coefficient

   $$C_G(V)=\frac{2y}{dv(dv-1)}$$

   $$\frac{1}{10}(6*\frac{2\times1}{2\times1}+3*\frac{2\times1}{3\times2}+1\frac{2\times0}{3\times2})=0.7$$

9. Laplacian matrix
   - $Q=BB^T=\Delta-A$, $\Delta=diag(d1,d2,...,d_N)$
   - $Q$ is symmetric
   - $Qu=0$ $u$ is an eigenvector of $Q$ belonging to eigenvalue $\mu=0$

10. electrical graph, effective resistance
11. electrical graph, potential voltage
12. Laplacian matrix
13. Star graph, spectrum of the Laplacian 
   
    $\mu={N, 1, 1, ..., 1, 0}$

14. star graph, wheel graph, cycle graph, spectrum
15. Robustness envelopes
16. K-hop walk
17. Erdos-Renyi graph, number of triangles
    - expected number of triangles incident of one vertex is $\begin{pmatrix}N-1 \\ 2\end{pmatrix}\rho^3$
    - expected number of triangles in the graph is $\begin{pmatrix}N \\ 3\end{pmatrix}\rho^3$
18. 看不懂
19. degree, spectrum of the adjacency matrix, boundary
20. Erdos-Renyi graph

# 2018 (1)
1. disconnected graph, spectral radius
   - If the graph is disconnected, its complementary graph is connected
   - If $d_min = \min_{1\leq k\leq N}\lambda_k^2(A)$, the graph is disconnected
   - Increasing assortativity creates more disconnected components 

2. remove one link in the graph
   - disconnected graph, $\mu_{N-1}(G)=0$
3. delay
   
   $D_{\max} < \frac{\sigma}{\lambda}$

4. Laplacian properties:
   - symmetric
   - sum of any rows or columns equals 0

5. degree, connected graph
   - The number of nodes with odd degree is even
   - At least two nodes in G have the same degree
   - if connected, $2-\frac{2}{N}\leq E(D)\leq N-1$

6. robustness
7. effective resistance matrix
   - symmetric
   - all diagonal elements are 0s
   - triangular inequality: $w_{ij}\leq w_{ik}+w_{kj}$
8. spectrum, tree/bipartite graph
   - Peaks refer to a specific structure or pattern in the graph
   - A broader, bell-shape form of fl(x) around the origin (x=0) is a fingerprint of randomness
   - A tree/bipartite graph has a symmetric spectrum (Any tree can be represented as a bipartite graph)

9. Envelope definitions
10. line graph: two nodes in I(G) are connected by a link if the corresponding two links in G have a node in common
11. Spectrum of Q:
    - complexity (number of spanning tree) is $\xi(G)=\frac{1}{N}\prod_{k=1}^{N-1}\mu_k$
    - $\prod_{k=1}^{N-1}\mu_k$ is an integer

12. Watts-Strogatz small world graph
    - with the increase of the rewiring probability:
      - the average clustering coefficient decreases
      - the average hop count decreases
    - the degree distribution is scale-free degree distribution (A scale-free network is a network whose degree distribution follows a power law)
    - robustness to random node failure
    - vulnerability to targeted hub attacks and cascading failures

13. path, walk, connected graph
14. Pseudoinverse of the Laplacian
    - The best spreader minimizes the sum of potential differences between its own and all other node potentials
      - the best spreader is the node $k$ with minimum $Q^\dag_{kk}\leq Q^\dag_{ii}$ for all $i$
    - diagonal elements $Q^\dag_{ii}>0$, but the off-diagonal elements $Q^\dag_{ij}>0$ can be negative as well as non-negative, thus, $Q^\dag$ is not always a Laplacian!  
    - the effective graph resistance $R_G = N\times Trace(Q^\dag) = Nu^Tdiag(Q^\dag)$
15. edge (node) connectivity:  the minimum number of links (or nodes) whose removal disconnects G
16. degree
17. power law
18. $L(u,t)\leq max_{\tau\in[u,t]}\lambda(\tau)(t-u)$
19. R-model: difficult to build a general theory
20. assortativity
   - only numerator changes when DPR
   $$\rho_D=1-\frac{\sum_{i\sim j}(d_i-d_j)^2}{\sum_jd_j^3-\frac{1}{2L}(\sum_jd_j^2)^2}$$

# 2018(2)
1. line graph of the complete graph
   - node: $\frac{N(N-1)}{2}$
   - link: $2(N-2)$
2. real-world complex network
   - small-world property
   - scale-free degree distribution
   - clustering and community structure (peaks in the spectrum of adjacency matrix)
   - robustness to random node failure
   - vulnerability to targeted attacks
3. complement graph
4. power law, moment
   - $E[D^m]$ only exist for $\tau>m+1$ when $N\to\infty$
5. spectrum
6. subgraph, spectral radius
   - The spectral radius of a graph G is larger than or equal to the spectral radius of any subgraph of G
7. electrical network
8. adjacency matrix of bipartite graph
9. degree
10. tree graph
11. Erdos-Renyi
12. 
13. Robustness envelope
    - Low sensitivity, High energy, most desirable
14. effective graph resistance:
    - $R_G=\frac{1}{2}u^T\omega u$
15. loss-less multiplexing
    - stability requires: $\sum\lambda_k<\mu$, $\mu$ is the constant link rate
    - $Q_t\leq G$ 
16. token bucket
17. effective graph resistance of complete graph
    - $R_G \geq N-1$, with equality for the complete graph
18. the spectrum of the adjacency matrix
19. electrical network
20. FIFO POB: the first entered low priority cell is discarded

# 2019(1)
1. degree
2. FIFO, PBS
3. Burstiness constraint
   $$\lim_{t\to\infty}\frac{L(u,t)}{t-u}=\lambda+\lim_{t\to\infty}\frac{\sigma}{t-u}$$
4. measurement for burstiness $B=\frac{max~S}{E[S]}$
5. Burstiness constraint
6. Linearity of R-model
7. weighted Laplacian:
   $$\tilde{Q}=\tilde{\Delta}-\tilde{A},~\tilde{a}_{ij}=\frac{1}{r_{ij}}a_{ij}$$
8. spectrum of adjacency matrix, number of triangles
   $\sum_{j=1}^N \lambda_j^3 = 6\#triangle$
9. spectrum of adjacency matrix
   - $\lambda_1-\lambda_2\leq N$
   - $\lambda_1\leq N-1$
   - $\sum_k\lambda_k=0$

10. the effective graph resistance for a complete graph with $N$ nodes is $N-1$
11. degree
12. A positive semidefinite matrix is a Hermitian matrix all of whose eigenvalues are nonnegative.
13. Erdos-Renyi
14. R-model: the more independent m metrics are, the better robustness measure R for network is
15. small-world compared with random graph p.73
16. spectrum of adjacency matrix
   - $\Sigma_{j=1}^N \lambda_j = 0$
   - $\Sigma_{j=1}^N \lambda_j^2 = 2L$
   - $\Sigma_{j=1}^N \lambda_j^3 = 6\times triangles$

17. token bucket
18. Robustness envelope
19. electrical network, current on the link
20. line graph, assortativity, path graph
    - line graph of path graph is still path graph only removing one node from original graph
    - path graph assortativity is $-\frac{1}{N-2}$
    - so, line graph of path graph assortativity is $-\frac{1}{N-3}$

# 2019(2)
1. 