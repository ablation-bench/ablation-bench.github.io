<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Effective_Text_to_Image_Alignment_with_Quality_Aware_Pair_Ranking

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Effective Text-to-Image Alignment with Quality Aware Pair Ranking" proposes a method to improve text-to-image diffusion model alignment by fine-tuning on a quality-ranked subset of preference pairs. The core idea is that not all human preference data is equally valuable, and filtering or prioritizing high-quality pairs can lead to better and more efficient fine-tuning.

The method introduces a quality metric Q for each preference pair (caption, winning image, losing image) based on an AI reward model (specifically HPSv2). The formula used is Q(c, xw, xl) = ψ(xw/c) * (1 - ψ(xl/c)). The dataset is then ranked by this quality score, and the model is fine-tuned using Diffusion-DPO (or other methods) on the top K% of the ranked data.

The paper includes several important ablation studies:
1.  **Amount of Data:** Demonstrates that fine-tuning on the top 5.33% of the data significantly outperforms using the full dataset, validating the core hypothesis.
2.  **Different Fine-tuning Methods:** Shows that the quality-aware ranking approach is effective when applied to other fine-tuning loss functions like SLIC-HF and ORPO, indicating the generalizability of the data ranking.
3.  **Effect of Different Scoring Models:** Compares using HPSv2, Laion Aesthetics, PickScore, and ImageReward as the underlying AI reward model (ψ) for calculating the quality metric, showing HPSv2 performs best.
4.  **Effect of LoRA Rank:** Investigates the impact of LoRA capacity on performance and efficiency, confirming the benefits of QSD across different ranks.

While these ablations cover important aspects like the amount of data, the choice of the underlying reward model, and the fine-tuning method, there are two key components of the proposed method that are central but not fully ablated:

1.  **The specific formula for the Quality Metric Q:** The paper proposes Q(c, xw, xl) = ψ(xw/c) * (1 - ψ(xl/c)) and provides an interpretation. However, it does not compare this specific multiplicative formula against other plausible ways to combine the winning and losing scores from the reward model (e.g., simple difference, ratio, or using only the winning score). Ablating this would clarify if the specific mathematical form of the quality metric is crucial or if other formulations yield similar or better results.
2.  **The strategy for using the Quality Score:** The paper's main finding relies on selecting the *top K%* of the ranked data. While effective, this is one specific way to leverage the quality score. Alternative strategies, such as weighted sampling (where pairs are sampled with probability proportional to their quality score) or thresholding (training on all pairs above a certain quality score threshold), could potentially offer different trade-offs or performance characteristics. Ablating this would help understand if the "top K%" selection is optimal compared to other methods of incorporating the quality information into the training data selection.

Based on their importance to the core method, the ablation of the Quality Metric Formula is slightly more fundamental as it defines *what* quality means in this context, while the Usage Strategy defines *how* that defined quality is applied. Therefore, I prioritize the Quality Metric Formula ablation. The Usage Strategy ablation is also important as it explores alternative ways to leverage the quality information.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Quality Metric Formula Ablation
- **Ablated Part**: The specific mathematical formula used to combine the AI reward model scores for the winning and losing images into a single quality score for the pair.
- **Action**: REPLACE
- **Replacement**: 
  - psi(xw/c) - psi(xl/c)
  - psi(xw/c)
- **Metrics**: Aesthetic Score, Image Reward, PickScore, HPSv2

### Quality Score Usage Strategy Ablation
- **Ablated Part**: The strategy for using the quality score to select/weight training data (currently top K% subset).
- **Action**: REPLACE
- **Replacement**: 
  - Weighted sampling based on Q
  - Thresholding based on Q
- **Metrics**: Aesthetic Score, Image Reward, PickScore, HPSv2

</div>