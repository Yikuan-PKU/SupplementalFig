## Supplementary Figures

All experiments use a deeper MLP (784–50–50–50–50–10) trained on MNIST with CE loss for 100 epochs with 100% training accuracy (Bs=50, Lr=0.1).

### Figure 1: Per-layer C–H loglog plot

![Figure 1](Fig1.pdf)

**Figure 1.** Log-log plots (in Hessian eigenbasis) of the diagonal elements of the empirical noise covariance Covar (left) and the AWD-based (the 2nd moment of persample hessian) H_2 (right) against the Hessian H, computed separately for each layer. Top row: data points are mean-centered and vertically shifted for visualization, which isolates the scaling relationship from absolute magnitude differences across layers. Bottom row: raw data plotted directly. Each layer exhibits a clean power-law relationship $C \propto H^\gamma$ with $R^2 > 0.99$. The magnitude ranges of the diagonal elements of C and H overlap strongly across layers. The fitted exponent $\gamma$ decreases from $\approx 1.39$ (Layer 1, blue) to $\approx 1.11$ (Layer 4, purple), but remains within $(1,2)$ across all layers, consistent with our theoretical prediction. The AWD-based H_2 reproduces the empirical slopes faithfully.

### Figure 2: Multi-layer Covar vs. Hessian (left) and H_2 vs. Hessian (right)

![Figure 2](Fig2.pdf)

**Figure 2.** Log-log plots (in Hessian eigenbasis) of the diagonal elements. Left: empirical covariance. Right: AWD-based H_2 (the 2nd moment). Unlike the per-layer plots, the Multi-layer log-log curves do not follow a clean linearity: the local slope varies across the eigenvalue range.

### Figure 3: Empirical Covar vs. AWD-based H_2 (Multi-layer level)

![Figure 3](Fig3.pdf)

**Figure 3.** Log-log plot (in Hessian eigenbasis) of the diagonal elements of the empirical Covar against the AWD-based H_2 (the 2nd moment). The fitted slope is $\approx 1.11$ with $R^2 \approx 0.997$, indicating near-perfect agreement. This demonstrates that Theorem 3.4 faithfully captures the empirical covariance structure at the Multi-layer level, even though neither Covar nor H_2 follows a clean power law against Hessian (cf. Figure 2).

### Figure 4: Approximate commutativity at the Multi-layer level

![Figure 4](Fig4.pdf)

**Figure 4.** The same as Fig 1 in the paper, but for the multi-layer level instead of per-layer. Top row: empirical covariance (Covar). Bottom row: AWD-based approximation H_2 (the 2nd moment). Left column: the matrix represented in the Hessian eigenbasis. Middle column: the scale-invariant correlation matrix $R_{\mathrm{real}}$, normalized by diagonal elements (mean $\mu$ and variance $\sigma^2$ shown). Right column: the randomized baseline $R_{\mathrm{rand}}$, constructed by randomly rotating the matrix while preserving its eigenvalue spectrum. For both Covar and H_2, the true-eigenbasis correlation $R_{\mathrm{real}}$ has substantially smaller mean and variance than the randomized baseline $R_{\mathrm{rand}}$, confirming that approximate commutativity holds at the multi-layer level.
