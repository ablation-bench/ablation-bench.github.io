<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Motion_Inversion_for_Video_Customization

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces two distinct and critical components: the Motion Query-Key Embedding (MQK) and the Motion Value Embedding (MV). While the ablation study reported in the paper investigates different spatial configurations for these embeddings and compares inference strategies, it does not evaluate the individual contributions of each major component by completely removing one of them. Understanding the individual impact of MQK and MV is essential because they play different roles – the MQK modulates the attention map to capture global temporal relationships while the MV, along with its debiasing operation, captures fine-grained local motion and suppresses static appearance. Assessing the performance drop when either component is removed would further clarify how each contributes to metrics such as text similarity, motion fidelity, temporal consistency, FID, and user preference. Therefore, the two most important missing ablation studies are: one where the MQK is removed and another where the MV is removed.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Motion Query-Key Embedding
- **Ablated Part**: Motion Query-Key Embedding responsible for modulating the temporal attention map to capture global inter-frame relationships
- **Action**: REMOVE
- **Metrics**: Text Similarity, Motion Fidelity, Temporal Consistency, FID, User Preference

### Ablation: Remove Motion Value Embedding
- **Ablated Part**: Motion Value Embedding responsible for encoding spatially varying motion and applying the debias operation to filter static appearance
- **Action**: REMOVE
- **Metrics**: Text Similarity, Motion Fidelity, Temporal Consistency, FID, User Preference

</div>