<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Unraveling_the_Shift_of_Visual_Information_Flow_in_MLLMs__From_Phased_Interaction_to_Efficient_Inference

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper conducts thorough analyses to understand how visual tokens contribute to prediction outcomes and how pruning them can accelerate inference. However, two important ablation studies appear to be missing. First, although the authors propose a hierarchical modality‐aware pruning (HiMAP) strategy that prunes image tokens at distinct network depths, they do not compare this adaptive, layer‐specific pruning approach with a simpler uniform pruning baseline (i.e. pruning the same fraction of image tokens at every layer). Such an experiment would validate that the hierarchical design indeed benefits the trade-off between computational savings and performance retention.

Second, the pruning method relies on specific importance criteria (ϕsh and ϕdp) based on the sum of attention scores. An ablation study that replaces these ranking functions with alternative token importance criteria (e.g., using the norm of token embeddings, random ranking, or gradient‐based measures) would help assess the sensitivity of the pruning performance to the token ranking design and further validate the effectiveness of the proposed criteria.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Uniform vs. Hierarchical Pruning Strategy Ablation
- **Ablated Part**: The dynamic hierarchical token pruning mechanism that prunes image tokens at different layers based on interaction shifts
- **Action**: REPLACE
- **Replacement**: 
  - Uniform pruning (same pruning ratio across all layers)
  - Random pruning across layers
- **Metrics**: TFLOPs, A-OKVQA Accuracy, Sci-VQA Accuracy, POPE Accuracy

### Token Importance Criterion Ablation
- **Ablated Part**: The attention-based token ranking functions (ϕsh and ϕdp) used to select image tokens for pruning
- **Action**: REPLACE
- **Replacement**: 
  - Embedding Norm ranking
  - Random ranking
  - Gradient-based ranking
- **Metrics**: TFLOPs, A-OKVQA Accuracy, Sci-VQA Accuracy, CIDEr, POPE Accuracy

</div>