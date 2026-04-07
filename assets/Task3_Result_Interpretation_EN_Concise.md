# Task 3 Main Result Interpretation

## Scope

This note focuses on what the final images reveal about optimization quality and lens-surface structure. It is intentionally concise and emphasizes shared conclusions before case-specific differences.

## Shared observations across all cases

- All three cases show clear convergence. The loss drops by about 61.10% for `GROUP23`, 60.27% for `NUS`, and 52.44% for `EE5311`, and the GIFs show a consistent coarse-to-fine optimization trend.
- In every case, the rendered caustics recover the main stroke layout of the target. This means the optimizer is not producing arbitrary brightness blobs; it is learning a surface that redirects energy toward the desired pattern.
- The height maps and 3D surfaces are smooth but structured. They contain broad ridges and valleys rather than isolated spikes, which is consistent with TV regularization and supports the interpretation that the learned surface is physically meaningful.
- The remaining errors are concentrated near thin strokes, corners, and crowded boundaries. This suggests that the current simplified model captures global geometry better than the finest local details.

## Case-specific differences

### GROUP23

- `GROUP23` is the strongest reconstruction in this run, with the lowest mean difference error of `0.1208`.
- Its target is spatially separated into upper and lower regions, and the optimized result preserves that separation well. This makes it a good example of successful large-scale energy routing.

### NUS

- `NUS` is the middle case, with a mean difference error of `0.1390`.
- The main letter skeleton is recovered clearly, but some local rounding remains along edges and thinner connections. This makes it a useful example of stable reconstruction with moderate detail loss.

### EE5311

- `EE5311` is the most challenging case here, with the highest mean difference error of `0.1703`.
- Its repeated tall strokes and dense right-side structure make it harder to sharpen cleanly, so the residual blur and boundary mismatch are more visible than in the other two cases.
- Even so, the dominant silhouette is still recovered well, which makes `EE5311` a good focus case for discussing both success and limitation at the same time.

## Final summary

Overall, the three cases tell a consistent story. The optimization successfully learns smooth refractive surfaces that reproduce the global target patterns, while the main limitations remain concentrated in thin, high-curvature, and crowded regions. In other words, the method is already strong enough to demonstrate structured inverse design, but not yet accurate enough to fully recover the sharpest local details.
