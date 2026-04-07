# Task 3 Main Result Interpretation
# Task 3 主结果解读

## Scope
## 范围

This note focuses on what the final images reveal about optimization quality and lens-surface structure. It is intentionally concise and emphasizes shared conclusions before case-specific differences.

这份说明聚焦于最终图像能够反映出的优化效果和透镜表面结构特征。它刻意保持简洁，先讲共同结论，再讲各个 case 的差异。

## Shared observations across all cases
## 三个 case 的共同点

- All three cases show clear convergence. The loss drops by about 61.10% for `GROUP23`, 60.27% for `NUS`, and 52.44% for `EE5311`, and the GIFs show a consistent coarse-to-fine optimization trend.
- 三个 case 都表现出清晰的收敛趋势。`GROUP23` 的 loss 下降约 `61.10%`，`NUS` 下降约 `60.27%`，`EE5311` 下降约 `52.44%`，而 GIF 也都显示出从粗到细的统一优化过程。

- In every case, the rendered caustics recover the main stroke layout of the target. This means the optimizer is not producing arbitrary brightness blobs; it is learning a surface that redirects energy toward the desired pattern.
- 在每个 case 中，生成的焦散图都恢复了目标图案的主要笔画布局。这说明优化器不是随便生成亮斑，而是在学习一个能够把光能重新引导到目标结构上的表面。

- The height maps and 3D surfaces are smooth but structured. They contain broad ridges and valleys rather than isolated spikes, which is consistent with TV regularization and supports the interpretation that the learned surface is physically meaningful.
- 高度图和三维表面都呈现出“平滑但有结构”的特点。它们主要由大尺度的隆起和沟槽组成，而不是零散尖峰，这和 TV 正则项的作用一致，也支持“学到的是有物理意义的表面结构”这一解释。

- The remaining errors are concentrated near thin strokes, corners, and crowded boundaries. This suggests that the current simplified model captures global geometry better than the finest local details.
- 剩余误差主要集中在细笔画、拐角和拥挤边界区域。这说明当前的简化模型更擅长恢复整体几何结构，而不是最细小的局部细节。

## Case-specific differences
## 各个 case 的独特点

### GROUP23
### GROUP23

- `GROUP23` is the strongest reconstruction in this run, with the lowest mean difference error of `0.1208`.
- `GROUP23` 是这次实验里重建效果最好的 case，它的平均差值误差最低，为 `0.1208`。

- Its target is spatially separated into upper and lower regions, and the optimized result preserves that separation well. This makes it a good example of successful large-scale energy routing.
- 它的目标图案在空间上分成上下两个区域，而优化结果较好地保留了这种分离结构，因此它是“大尺度能量重分配成功”的典型例子。

### NUS
### NUS

- `NUS` is the middle case, with a mean difference error of `0.1390`.
- `NUS` 处于中间水平，平均差值误差为 `0.1390`。

- The main letter skeleton is recovered clearly, but some local rounding remains along edges and thinner connections. This makes it a useful example of stable reconstruction with moderate detail loss.
- 它的主要字母骨架恢复得比较清楚，但边缘和较细连接处仍然有一些圆化和模糊，因此它适合用来说明“整体稳定恢复，但细节略有损失”的情况。

### EE5311
### EE5311

- `EE5311` is the most challenging case here, with the highest mean difference error of `0.1703`.
- `EE5311` 是这里最有挑战性的 case，平均差值误差最高，为 `0.1703`。

- Its repeated tall strokes and dense right-side structure make it harder to sharpen cleanly, so the residual blur and boundary mismatch are more visible than in the other two cases.
- 它包含重复的高竖笔画和右侧更密集的结构，因此更难被锐利地恢复出来，残余模糊和边界不匹配也比另外两个 case 更明显。

- Even so, the dominant silhouette is still recovered well, which makes `EE5311` a good focus case for discussing both success and limitation at the same time.
- 即便如此，它的主轮廓仍然恢复得不错，因此 `EE5311` 很适合作为重点案例，因为它能同时体现方法的成功之处和当前局限。

## Final summary
## 最终总结

Overall, the three cases tell a consistent story. The optimization successfully learns smooth refractive surfaces that reproduce the global target patterns, while the main limitations remain concentrated in thin, high-curvature, and crowded regions. In other words, the method is already strong enough to demonstrate structured inverse design, but not yet accurate enough to fully recover the sharpest local details.

整体来看，这三个 case 说明的是同一个结论：优化过程能够成功学到平滑的折射表面，并重建目标图案的整体结构；但它的主要局限仍然集中在细笔画、高曲率和拥挤区域。换句话说，这个方法已经足够展示“结构化逆向设计”这一核心能力，但还没有精确到能完整恢复最尖锐的局部细节。
