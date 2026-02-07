<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Learning_with_Instance_Dependent_Label_Noise__Balancing_Accuracy_and_Fairness

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a two-stage approach for learning with instance-dependent label noise, leveraging a small set of "alignment points" with known ground truth labels. The method involves pre-training a main classifier network (θ) and an auxiliary label confidence network (ϕ) on the alignment points (Stage 1), followed by fine-tuning both networks on the complete dataset (Stage 2). Stage 2 uses a weighted cross-entropy loss (L'θ) on the non-alignment points, where the weights depend on the predicted label confidence (βˆϕ) from the auxiliary network ϕ and the estimated clean rate per group. Stage 2 alternates between training θ (freezing ϕ) and training ϕ (freezing θ), incorporating continued supervision from the alignment points via losses Lθ and Lϕ.

The paper includes an ablation study in Appendix E (Figure 5) that examines the contribution of different loss terms and data usage in Stage 2, starting from only using Stage 1. This ablation shows the benefit of adding the noisy data (via L'θ) and the continued use of alignment points (via Lθ and Lϕ) during fine-tuning.

However, the existing ablation does not fully explore the necessity of two key structural components:
1.  **The auxiliary network (ϕ) and its learned instance-dependent confidence (βˆϕ):** This is the core mechanism proposed to handle *instance-dependent* noise by learning the noise pattern. The existing ablation shows that using the weighted loss L'θ (which relies on βˆϕ) is better than just Stage 1, but it doesn't isolate the benefit of the *learned* βˆϕ compared to, for example, using a fixed weighting or no weighting derived from a separate network.
2.  **The two-stage training procedure:** The method explicitly separates training into a pre-training stage on clean data (alignment points) and a fine-tuning stage on noisy data. This structural choice is significant. An ablation is needed to determine if this pre-training is essential or if training end-to-end on the full dataset from the start could achieve similar or better performance.

Based on this analysis, I propose two missing ablation studies focusing on these critical components. The metrics used will be consistent with the paper: AUROC, AUEOC, and their Harmonic Mean (HM).

**Ablation 1: No Learned Confidence Weighting**
This ablation aims to understand the contribution of the auxiliary network ϕ and the instance-dependent weighting (βˆϕ) it provides to the loss. By removing ϕ and the βˆϕ weighting from L'θ, we can assess if the performance gains are due to learning this specific confidence score or other aspects of the method.

**Ablation 2: End-to-End Training**
This ablation tests the importance of the two-stage training structure. By training the model (both θ and ϕ) on the complete dataset from the beginning, we can see if the explicit pre-training phase on clean alignment points is necessary for robust learning in the presence of instance-dependent noise.

These two ablations target fundamental design choices of the proposed method that are not fully addressed by the existing ablation study, making them important for understanding the method's success.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: No Learned Confidence Weighting
- **Ablated Part**: Auxiliary network (ϕ) and the use of its output (βˆϕ) for instance-dependent weighting in the loss L'θ.
- **Action**: REMOVE
- **Metrics**: AUROC, AUEOC, Harmonic Mean

### Ablation: End-to-End Training
- **Ablated Part**: The two-stage training procedure (separate pre-training on alignment points).
- **Action**: REPLACE
- **Replacement**: 
  - Train θ and ϕ end-to-end on the complete dataset using a combined loss (L'θ on non-alignment points + γLθ on alignment points + α2Lϕ on alignment points) from the start.
- **Metrics**: AUROC, AUEOC, Harmonic Mean

</div>