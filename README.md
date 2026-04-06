# Follow-up Response to Reviewer UvQQ

We sincerely thank the reviewer for the continued and thoughtful engagement. We are grateful that the reviewer acknowledges the generality of the AWD argument and appreciates the additional hyperparameter experiments. We have now conducted further experiments that directly address the reviewer's two main concerns, namely cross-layer consistency and off-block coupling, and we believe the results substantially strengthen the paper.

**New cross-layer experiments.** Following the reviewer's suggestion, we extended the MNIST MLP (using CE loss) from 784×50×50×10 to a deeper 784×50×50×50×50×10 architecture and performed per-layer $C$–$H$ spectral analysis. Every layer exhibits a clean empirical power law $C \propto H^\gamma$. The exponent $\gamma$ varies across layers, decreasing from $\approx 1.4$ in early layers to $\approx 1.1$ near the output layer, but remains consistently within $(1, 2)$, in agreement with our theoretical prediction. The AWD-based theoretical $C$ closely matches the empirical $C$ (i.e., the predicted $\gamma$ values agree with the measured ones), confirming that the AWD approximation faithfully captures the per-layer noise–curvature structure.

**Multi-layer (whole-model) analysis.** We also computed $C$ and $H$ treating all layers jointly. The approximate commutativity $[C, H] \approx 0$ continues to hold at the multi-layer level. However, the whole-model $C$ vs. $H$ log-log plot does not exhibit a single clean linear relationship. Two factors likely contribute to this deviation: (1) the per-layer $\gamma$ values differ (ranging from $\approx 1.4$ to $\approx 1.05$) while the magnitude ranges of the diagonal elements of $C$ and $H$ overlap strongly across layers; and (2) the off-block inter-layer couplings may be non-negligible, as the reviewer suggested. Nevertheless, the relationship remains superlinear throughout, with the log-log curve being approximately monotonic, which is precisely the core prediction of our theory. We emphasize that our central theoretical result is that the noise covariance $C$ is determined by second moments of per-sample Hessians while $H$ itself is a first moment (Theorem 3.4), from which the superlinear relationship follows. Notably, our theory does not predict a power law itself; the per-layer power-law scaling $C \propto H^\gamma$ with $\gamma > 1$ is an empirical observation at the layer-wise level, fully consistent with the absence of a single global power law at the whole-model level. Crucially, the log-log plot of empirical $C$ against AWD-based $C$ (second moments of per-sample Hessians) is approximately linear with slope $\approx 1$, directly demonstrating that Theorem 3.4 faithfully captures the empirical covariance structure not only per layer but also at the whole-model level. We also note that the theoretical bound $\gamma \in (1, 2)$ is derived under the assumption that a power law holds, which is precisely what we observe empirically at the per-layer level; we do not extend this bound to the whole-model log-log plot where a single power law does not hold.

We will clarify in the revised introduction that Theorem 3.4 (the AWD approximation) is our core result, that the per-layer empirical power law corroborates but is not required by the theory, and that a single whole-model power law is not expected. We will also add a discussion section addressing whole-model behavior and inter-layer coupling.

We hope these new results, which provide the cross-layer and whole-model evidence the reviewer requested, address the empirical scope concern. We greatly value the reviewer's feedback, which has led to what we believe is a meaningfully stronger paper.

---

## Supplementary Figures

All experiments use a deeper MLP (784–50–50–50–50–10) trained on MNIST with CE loss for 100 epochs with 100% training accuracy.

### Figure 1: Per-layer Covar–H loglog plot

![Figure 1](Fig1.png)

**Figure 1.** Per-layer $Covar$–$H$ spectral analysis. Log-log plots (in Hessian eigenbasis) of the diagonal elements of the empirical noise covariance $Covar$ (left) and the AWD-based $H_2 = \frac{2C}{\sigma_w^2} = \mathbb{E}_p \left[ \sum_{m} (\kappa_m^{(p)})^2 (\mathbf{u}_m^{(p)} \cdot \mathbf{v}_i)^2 \right]$ (right) against the Hessian $H$, computed separately for each layer. Top row: data points are mean-centered and vertically shifted for visualization, which isolates the scaling relationship from absolute magnitude differences across layers. Bottom row: raw data plotted directly. Each layer exhibits a clean power-law relationship $C \propto H^\gamma$ with $R^2 > 0.99$. The magnitude ranges of the diagonal elements of $C$ and $H$ overlap strongly across layers. The fitted exponent $\gamma$ decreases from $\approx 1.39$ (Layer 1, blue) to $\approx 1.11$ (Layer 4, purple), but remains within $(1,2)$ across all layers, consistent with our theoretical prediction. The AWD-based $H_2$ reproduces the empirical slopes faithfully.

### Figure 2: Multi-layer (Whole-model) Covar vs. Hessian and H₂d vs. Hessian

![Figure 2](Fig2.png)

**Figure 2.** Multi-layer (Whole-model) $Covar$ vs. Hessian and $H_{2,d}$ vs. Hessian. Log-log plots (in Hessian eigenbasis) of the diagonal elements. Left: empirical covariance. Right: AWD-based $H_{2,d} = \frac{2C}{\sigma_w^2} = \mathbb{E}_p \left[ \sum_{m} (\kappa_m^{(p)})^2 (\mathbf{u}_m^{(p)} \cdot \mathbf{v}_i)^2 \right]$. Unlike the per-layer plots, the whole-model log-log curves do not follow a single clean linear relationship: the local slope varies across the eigenvalue range.

### Figure 3: Empirical C vs. AWD-based C (Whole-model level)

![Figure 3](Fig3.png)

**Figure 3.** Empirical $C$ vs. AWD-based $C$ (Multi-layer (Whole-model) level). Log-log plot (in Hessian eigenbasis) of the diagonal elements of the empirical covariance Covar against the AWD-based $H_{2,d}$. The fitted slope is $\approx 1.11$ with $R^2 \approx 0.997$, indicating near-perfect agreement. This demonstrates that Theorem 3.4 faithfully captures the empirical covariance structure at the whole-model level, even though neither $Covar$ nor $H_{2,d}$ follows a clean power law against $H$ (cf. Figure 2).

### Figure 4: Approximate commutativity [C, H] ≈ 0 at the whole-model level

![Figure 4](Fig4.png)

**Figure 4.** Approximate commutativity $[C, H] \approx 0$ at the whole-model level. The same as Fig 1 in the paper, but for the whole-model (multi-layer) level instead of per-layer. Top row: empirical covariance (Covar). Bottom row: AWD-based approximation $H_{2,d}$. (a) Left column: the matrix represented in the Hessian eigenbasis. (b) Middle column: the scale-invariant correlation matrix $R_{\mathrm{real}}$, normalized by diagonal elements (mean $\mu$ and variance $\sigma^2$ shown). (c) Right column: the randomized baseline $R_{\mathrm{rand}}$, constructed by randomly rotating the matrix while preserving its eigenvalue spectrum. For both Covar and $H_{2,d}$, the true-eigenbasis correlation $R_{\mathrm{real}}$ has substantially smaller mean and variance than the randomized baseline $R_{\mathrm{rand}}$, confirming that approximate commutativity holds at the multi-layer (whole-model) level.
