# Task 3 Visualization and Main Result Interpretation

## Run Configuration
- Grid resolution N: 72
- Epochs: 300
- Learning rate: 0.01
- TV regularization weight: 0.005
- GIF capture interval: one frame every 20 epochs
- Focus pattern: EE5311

## File Guide
- `*_main_result.png`: the aligned four-panel summary figure containing the target, rendered caustics, height map, and difference heatmap.
- `*_surface_3d.png`: the optimized 3D lens surface.
- `*_difference_heatmap.png`: the spatial error distribution after normalization.
- `*_loss_curve.png`: the optimization loss history.
- `*_optimization.gif`: the visual convergence process.
- `metrics_summary.json`: quantitative metrics for each pattern.

## Main Takeaways
- The loss falls rapidly in the early epochs and then enters a slower refinement stage, suggesting that the optimizer first establishes the coarse energy layout before polishing local details.
- The rendered caustics concentrate around the target strokes, which supports the claim that differentiable optimization can infer a lens surface from a desired light intensity pattern.
- The recovered lens surface is smooth at the global scale, which is consistent with the TV regularizer and makes the result more physically plausible than a noisy high-frequency solution.
- The remaining errors are concentrated near thin strokes, boundaries, and corners, indicating that the simplified model captures the global structure better than the finest local details.
- The GIF makes the convergence behavior easy to explain in a presentation because it shows the light pattern gradually tightening around the target geometry.

## Pattern-wise Interpretation

### GROUP23 (supporting case)
- The final loss drops from 1664.0129 to 457.7230, a reduction of about 72.49%.
- The normalized difference heatmap reports a mean error of 0.1198 and a peak error of 0.9499.
- The height map ranges from -0.5292 to 0.7546, with a standard deviation of 0.1848, indicating a smooth but structured refractive surface rather than random noise.
- The main result image shows that bright caustic energy is redirected toward the target strokes, which means the optimizer has learned an effective lens profile for the desired pattern.
- The largest residuals remain near thin strokes, corners, and high-curvature regions, which is consistent with the low spatial resolution, Gaussian spot blur, and simplified refraction model used here.
- The 3D surface plot is dominated by broad ridges and valleys instead of isolated spikes, matching the role of the TV regularizer in suppressing unstable high-frequency oscillations.

### NUS (supporting case)
- The final loss drops from 1765.3395 to 486.3742, a reduction of about 72.45%.
- The normalized difference heatmap reports a mean error of 0.1320 and a peak error of 0.8369.
- The height map ranges from -0.4884 to 0.7398, with a standard deviation of 0.1652, indicating a smooth but structured refractive surface rather than random noise.
- The main result image shows that bright caustic energy is redirected toward the target strokes, which means the optimizer has learned an effective lens profile for the desired pattern.
- The largest residuals remain near thin strokes, corners, and high-curvature regions, which is consistent with the low spatial resolution, Gaussian spot blur, and simplified refraction model used here.
- The 3D surface plot is dominated by broad ridges and valleys instead of isolated spikes, matching the role of the TV regularizer in suppressing unstable high-frequency oscillations.

### EE5311 (focus case)
- The final loss drops from 1858.0432 to 689.5040, a reduction of about 62.89%.
- The normalized difference heatmap reports a mean error of 0.1655 and a peak error of 0.9020.
- The height map ranges from -0.5967 to 0.7498, with a standard deviation of 0.1748, indicating a smooth but structured refractive surface rather than random noise.
- The main result image shows that bright caustic energy is redirected toward the target strokes, which means the optimizer has learned an effective lens profile for the desired pattern.
- The largest residuals remain near thin strokes, corners, and high-curvature regions, which is consistent with the low spatial resolution, Gaussian spot blur, and simplified refraction model used here.
- The 3D surface plot is dominated by broad ridges and valleys instead of isolated spikes, matching the role of the TV regularizer in suppressing unstable high-frequency oscillations.

## Report-ready Paragraph
With the learning rate set to 0.01, the caustic optimization is able to recover the main strokes of the target pattern in a stable way. The main result figure and the optimization GIF jointly show that the solver first establishes the large-scale light distribution and then progressively sharpens the target strokes. The 3D surface figure indicates that the learned lens profile is a continuous and interpretable refractive structure instead of irregular noise. Meanwhile, the difference heatmap shows that the residual errors mainly appear near edges and high-curvature regions, which is consistent with the finite grid resolution, Gaussian spot approximation, and simplified refraction model used in this demo. Overall, the results support the central claim that differentiable optimization can invert a desired caustic pattern into a structured lens surface.

## Short Caption Suggestions
- `EE5311_main_result.png`: Four aligned views of the target, the rendered caustics, the learned height map, and the residual error map.
- `EE5311_surface_3d.png`: The optimized lens surface forms smooth large-scale ridges and valleys that steer light toward the target pattern.
- `EE5311_difference_heatmap.png`: Residual errors are mainly concentrated along thin strokes and sharp corners.
- `EE5311_loss_curve.png`: The loss decreases quickly at first and then gradually converges.
- `EE5311_optimization.gif`: The light distribution progressively contracts onto the target structure during optimization.
