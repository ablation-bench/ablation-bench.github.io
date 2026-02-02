<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/GROOT_2__Weakly_Supervised_Multimodal_Instruction_Following_Agents

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "GROOT-2: Weakly Supervised Multimodal Instruction Following Agents" introduces a method for training instruction-following agents using a combination of large amounts of unlabeled data and smaller amounts of labeled data. The core idea is to use a latent variable model with two main training objectives: "constrained self-imitating" (`L_dem`) for learning diverse behaviors from unlabeled data, and "human intention alignment" (`L_lab`) for aligning the latent space with human intentions using labeled data.

The paper includes several ablation studies:
1.  Scaling the proportion of unlabeled data.
2.  Scaling the proportion of labeled data.
3.  Evaluating different backbone initializations (ViT, BERT).
4.  Removing the entire `L_lab` loss.
5.  Removing the entire `L_dem` loss.

While these ablations demonstrate the importance of the overall framework and the presence of both loss terms, they do not fully explore the impact of the hyperparameters that balance the different components within these losses. Specifically, the `L_dem` loss includes a KL divergence term weighted by `β1`, designed to constrain the latent space and prevent mechanical imitation. The `L_lab` loss includes an MLE alignment term weighted by `β2`, designed to explicitly align the video-encoded latent space with the label-encoded latent space. The paper sets `β1 = 0.1` and `β2 = 0.1` but does not ablate these values.

Understanding how varying `β1` affects the trade-off between reconstruction accuracy and latent space structure (related to the "mechanical imitation" vs. "posterior collapse" spectrum discussed in the paper) is crucial for validating the "constrained self-imitating" mechanism. Similarly, investigating the impact of `β2` would clarify the specific contribution of the explicit MLE alignment term versus the implicit alignment achieved through policy reconstruction conditioned on label latents.

Therefore, two important missing ablation studies are:
1.  Varying the weight `β1` of the KL divergence term in the `L_dem` loss. This directly tests the effect of the constraint on the latent space learned from unlabeled data.
2.  Varying the weight `β2` of the MLE alignment term in the `L_lab` loss. This directly tests the effect of the explicit alignment mechanism between video and label latents.

These ablations would provide deeper insights into how the proposed loss components and their relative weights contribute to learning a controllable and human-aligned latent space, which is a central claim of the paper. The metrics used in the paper across different environments (Success Rate, Human-normalized Score, IQM Score) would be appropriate for evaluating the performance under different hyperparameter settings.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Beta1
- **Ablated Part**: Weight (β1) of the KL divergence term in the constrained self-imitating loss (L_dem)
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.01
  - 0.1
  - 1.0
- **Metrics**: Success Rate, Human-normalized Score, IQM Score

### Ablation on Beta2
- **Ablated Part**: Weight (β2) of the MLE alignment term in the human intention alignment loss (L_lab)
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.01
  - 0.1
  - 1.0
- **Metrics**: Success Rate, Human-normalized Score, IQM Score

</div>