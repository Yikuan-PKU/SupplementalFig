## Supplementary Figures

All experiments use a deeper MLP (784–50–50–50–50–10) trained on MNIST with CE loss for 100 epochs with 100% training accuracy (Bs=50, Lr=0.1).

### Figure 1: Per-layer C–H loglog plot 

![Figure 1](Fig1.png)

**Figure 1.** Log-log plots (in Hessian eigenbasis) of the diagonal elements computed separately for each layer. (a) directly numerically computed covariance $C$ against the Hessian $H$. Each layer exhibits a clean power-law relationship $C \propto H^\gamma$ with $R^2 > 0.99$. The magnitude ranges of the diagonal elements of $C$ and $H$ overlap strongly across layers. The fitted exponent $\gamma$ decreases from $\approx 1.39$ (Layer 1, blue) to $\approx 1.11$ (Layer 4, purple), but remains within $(1,2)$ across all layers, consistent with our theoretical prediction. (b) the AWD-based $C_{\text{AWD},ij}=E_p \left[\sum_m (\kappa_m^{(p)})^2 (u_m^{(p)} \cdot v_i)(u_m^{(p)} \cdot v_j)\right]$ (the 2nd moment of persample hessian) against the Hessian H which reproduces the empirical slopes faithfully. (c) directly numerically computed covariance $C$ against the AWD-based $C_{\text{AWD}}$, showing almost straight lines with slope = 1.

### Figure 2: Approximate commutativity at the Multi-layer level

![Figure 2](Fig3.png)

**Figure 2.** Top row: numerically computed covariance $C$. Bottom row: the AWD-based $C_{\text{AWD}}$ (the 2nd moment of persample hessian). Left column: the matrix represented in the Hessian eigenbasis (Top 300 dimensions plotted). Middle column: the scale-invariant correlation matrix $R_{\mathrm{real}}$ (Top 2500 dimensions plotted), normalized by diagonal elements (mean $\mu$ and variance $\sigma^2$ shown). Right column: the randomized baseline $R_{\mathrm{rand}}$ (Top 2500 dimensions plotted), constructed by randomly rotating the matrix while preserving its eigenvalue spectrum. For both $C$ and $C_{\text{AWD}}$, the true-eigenbasis correlation $R_{\mathrm{real}}$ has substantially smaller mean and variance than the randomized baseline $R_{\mathrm{rand}}$, confirming that approximate commutativity holds at the multi-layer level.

### Figure 3: Multi-layer C–H loglog plot

![Figure 3](Fig2.png)

**Figure 3.** Log-log plots (in Hessian eigenbasis) of the diagonal elements. (a) directly numerically computed covariance $C$ against the Hessian $H$. Unlike the per-layer plots, the Multi-layer log-log curves do not follow a clean linearity: the local slope varies across the eigenvalue range. (b) the AWD-based $C_{\text{AWD}}$ (the 2nd moment of persample hessian) against the Hessian H which reproduces the shape of the curve faithfully. (c) directly numerically computed covariance $C$ against the AWD-based $C_{\text{AWD}}$, showing a nearly straight line. This demonstrates that Theorem 3.4 faithfully captures the directly numerically computed covariance $C$ at the Multi-layer level, even though neither $C$ nor $C_{\text{AWD}}$ follows a clean power law against Hessian.


### Figure 4: Non-negligible off-diagonal coupling

![Figure 4](Fig4.png)

**Figure 4.** Layerwise decomposition of the joint Hessian $\mathbf{H}\in\mathbb{R}^{D\times D}$ ($D=\sum_{l}d_{l}$) for a 3-hidden-layer MLP with the output layer. Let $\hat{H}^{(l)}$ be the single-layer Hessian of layer $l$ with eigenbasis $V^{(l)}$, and define the block-diagonal rotation matrix $Q=\mathrm{blkdiag} \bigl(V^{(1)},V^{(2)},V^{(3)},V^{(4)}\bigr)$. (a) The rotated Hessian $H_{\text{rot}} = Q^{\top} H Q$. While each diagonal block is approximately diagonalised, the off-diagonal blocks remain substantial, indicating non-negligible inter-layer coupling. (b) the effect normalized coupling $|| H_{\text{rot},L_i,L_j}||\_F / (||H_{\text{rot},L_i,L_i}||\_F ||H_{\text{rot},L_j,L_j}||\_F)^{1/2}$ defined by normalized Frobenius Norm of each blocks $H_{\text{rot},L_i,L_j}$.
