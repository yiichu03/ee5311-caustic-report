# English Interpretation with Chinese Line-by-line Translation

# Task 3 Visualization and Main Result Interpretation
# Task 3 可视化与主结果解读



## Run Configuration
## 运行设置

- Grid resolution N: 72
- 网格分辨率 N: 72

- Epochs: 300
- 训练轮数 Epochs: 300

- Learning rate: 0.01
- 学习率: 0.01

- TV regularization weight: 0.005
- TV 正则权重: 0.005

- GIF capture interval: one frame every 20 epochs
- GIF 取帧间隔: one frame every 20 epochs

- Focus pattern: EE5311
- 重点展示图案: EE5311



## File Guide
## 文件说明

- `*_main_result.png`: the aligned four-panel summary figure containing the target, rendered caustics, height map, and difference heatmap.
- `*_main_result.png`：对齐后的四联图，包含目标图案、模拟焦散、高度图和差值热图。

- `*_surface_3d.png`: the optimized 3D lens surface.
- `*_surface_3d.png`：优化得到的三维透镜表面。

- `*_difference_heatmap.png`: the spatial error distribution after normalization.
- `*_difference_heatmap.png`：归一化后的空间误差分布。

- `*_loss_curve.png`: the optimization loss history.
- `*_loss_curve.png`：优化损失随 epoch 的变化历史。

- `*_optimization.gif`: the visual convergence process.
- `*_optimization.gif`：可视化收敛过程。

- `metrics_summary.json`: quantitative metrics for each pattern.
- `metrics_summary.json`：每个 pattern 的定量指标。



## Main Takeaways
## 核心结论

- The loss falls rapidly in the early epochs and then enters a slower refinement stage, suggesting that the optimizer first establishes the coarse energy layout before polishing local details.
- 损失在前期快速下降，随后进入较慢的细化阶段，说明优化器先建立粗粒度的能量布局，再逐步修正局部细节。

- The rendered caustics concentrate around the target strokes, which supports the claim that differentiable optimization can infer a lens surface from a desired light intensity pattern.
- 模拟焦散会集中到目标笔画附近，这支持“可微优化能够从目标光强分布反推出透镜表面”的结论。

- The recovered lens surface is smooth at the global scale, which is consistent with the TV regularizer and makes the result more physically plausible than a noisy high-frequency solution.
- 恢复出的透镜表面在整体尺度上较平滑，这与 TV 正则项的作用一致，也比高频噪声解更符合物理直觉。

- The remaining errors are concentrated near thin strokes, boundaries, and corners, indicating that the simplified model captures the global structure better than the finest local details.
- 剩余误差主要集中在细笔画、边界和拐角附近，说明这个简化模型更擅长恢复整体结构，而不是最细微的局部细节。

- The GIF makes the convergence behavior easy to explain in a presentation because it shows the light pattern gradually tightening around the target geometry.
- GIF 很适合展示时解释收敛过程，因为它直观展示了光图案如何逐渐收缩到目标几何结构附近。



## Pattern-wise Interpretation
## 分 pattern 解读



### GROUP23 (supporting case)
### GROUP23 (supporting case) 的中文理解

- The final loss drops from 1664.0129 to 457.7230, a reduction of about 72.49%.
- 最终 loss 明显下降，说明这组参数能够稳定推动优化收敛。

- The normalized difference heatmap reports a mean error of 0.1198 and a peak error of 0.9499.
- 差值热图给出了平均误差和峰值误差，可用来衡量最终图案与目标图案的接近程度。

- The height map ranges from -0.5292 to 0.7546, with a standard deviation of 0.1848, indicating a smooth but structured refractive surface rather than random noise.
- 高度图的数值范围和标准差说明优化学到的是有结构的表面起伏，而不是随机噪声。

- The main result image shows that bright caustic energy is redirected toward the target strokes, which means the optimizer has learned an effective lens profile for the desired pattern.
- 主结果图说明亮度确实被重定向到了目标笔画附近，说明优化方向是对的。

- The largest residuals remain near thin strokes, corners, and high-curvature regions, which is consistent with the low spatial resolution, Gaussian spot blur, and simplified refraction model used here.
- 误差最大的地方仍然是细笔画和拐角区域，这是当前简化模型最难处理的部分。

- The 3D surface plot is dominated by broad ridges and valleys instead of isolated spikes, matching the role of the TV regularizer in suppressing unstable high-frequency oscillations.
- 三维表面图显示的是大尺度起伏而不是孤立尖峰，这更像一个合理的折射表面。



### NUS (supporting case)
### NUS (supporting case) 的中文理解

- The final loss drops from 1765.3395 to 486.3742, a reduction of about 72.45%.
- 最终 loss 明显下降，说明这组参数能够稳定推动优化收敛。

- The normalized difference heatmap reports a mean error of 0.1320 and a peak error of 0.8369.
- 差值热图给出了平均误差和峰值误差，可用来衡量最终图案与目标图案的接近程度。

- The height map ranges from -0.4884 to 0.7398, with a standard deviation of 0.1652, indicating a smooth but structured refractive surface rather than random noise.
- 高度图的数值范围和标准差说明优化学到的是有结构的表面起伏，而不是随机噪声。

- The main result image shows that bright caustic energy is redirected toward the target strokes, which means the optimizer has learned an effective lens profile for the desired pattern.
- 主结果图说明亮度确实被重定向到了目标笔画附近，说明优化方向是对的。

- The largest residuals remain near thin strokes, corners, and high-curvature regions, which is consistent with the low spatial resolution, Gaussian spot blur, and simplified refraction model used here.
- 误差最大的地方仍然是细笔画和拐角区域，这是当前简化模型最难处理的部分。

- The 3D surface plot is dominated by broad ridges and valleys instead of isolated spikes, matching the role of the TV regularizer in suppressing unstable high-frequency oscillations.
- 三维表面图显示的是大尺度起伏而不是孤立尖峰，这更像一个合理的折射表面。



### EE5311 (focus case)
### EE5311 (focus case) 的中文理解

- The final loss drops from 1858.0432 to 689.5040, a reduction of about 62.89%.
- 最终 loss 明显下降，说明这组参数能够稳定推动优化收敛。

- The normalized difference heatmap reports a mean error of 0.1655 and a peak error of 0.9020.
- 差值热图给出了平均误差和峰值误差，可用来衡量最终图案与目标图案的接近程度。

- The height map ranges from -0.5967 to 0.7498, with a standard deviation of 0.1748, indicating a smooth but structured refractive surface rather than random noise.
- 高度图的数值范围和标准差说明优化学到的是有结构的表面起伏，而不是随机噪声。

- The main result image shows that bright caustic energy is redirected toward the target strokes, which means the optimizer has learned an effective lens profile for the desired pattern.
- 主结果图说明亮度确实被重定向到了目标笔画附近，说明优化方向是对的。

- The largest residuals remain near thin strokes, corners, and high-curvature regions, which is consistent with the low spatial resolution, Gaussian spot blur, and simplified refraction model used here.
- 误差最大的地方仍然是细笔画和拐角区域，这是当前简化模型最难处理的部分。

- The 3D surface plot is dominated by broad ridges and valleys instead of isolated spikes, matching the role of the TV regularizer in suppressing unstable high-frequency oscillations.
- 三维表面图显示的是大尺度起伏而不是孤立尖峰，这更像一个合理的折射表面。



## Report-ready Paragraph
## 可直接放入报告的段落

With the learning rate set to 0.01, the caustic optimization is able to recover the main strokes of the target pattern in a stable way. The main result figure and the optimization GIF jointly show that the solver first establishes the large-scale light distribution and then progressively sharpens the target strokes. The 3D surface figure indicates that the learned lens profile is a continuous and interpretable refractive structure instead of irregular noise. Meanwhile, the difference heatmap shows that the residual errors mainly appear near edges and high-curvature regions, which is consistent with the finite grid resolution, Gaussian spot approximation, and simplified refraction model used in this demo. Overall, the results support the central claim that differentiable optimization can invert a desired caustic pattern into a structured lens surface.
学习率设为 0.01 时，优化能够较稳定地恢复目标图案的主轮廓。主结果图和 GIF 共同说明，算法先建立大尺度亮度分布，再逐步强化目标笔画。三维表面图表明学到的是连续且可解释的折射结构，而差值热图说明误差主要集中在边缘和高曲率区域。这与有限网格分辨率、Gaussian 光斑近似和简化折射模型是一致的。整体上，这组结果支持“可微优化能够把目标焦散图案反推出结构化透镜表面”这一核心结论。



## Short Caption Suggestions
## 简短图注建议

- `EE5311_main_result.png`: Four aligned views of the target, the rendered caustics, the learned height map, and the residual error map.
- 这张图适合作为正文主图。

- `EE5311_surface_3d.png`: The optimized lens surface forms smooth large-scale ridges and valleys that steer light toward the target pattern.
- 这张图适合作为结构解释图。

- `EE5311_difference_heatmap.png`: Residual errors are mainly concentrated along thin strokes and sharp corners.
- 这张图适合作为误差解释图。

- `EE5311_loss_curve.png`: The loss decreases quickly at first and then gradually converges.
- 这张图适合作为优化稳定性说明图。

- `EE5311_optimization.gif`: The light distribution progressively contracts onto the target structure during optimization.
- 这段 GIF 适合作为动态展示材料。
