<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Resolving_Lexical_Bias_in_Edit_Scoping_with_Projector_Editor_Networks

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents PENME, a model editing approach that uses a projection network trained via contrastive learning to address lexical bias issues. The key components are:

1. A projection network that maps model representations to a new space where paraphrases are close together while irrelevant prompts are far apart
2. A key-value memory system for storing edits and retrieving them efficiently
3. A thresholding mechanism for determining when to apply edits

The paper already includes ablations on:
- Different margin values (m) in the contrastive loss function
- Different threshold values (τ) for controlling the trade-off between generalization and locality
- Different layers for applying the projection network
- Different model architectures (T5, GPT2-XL, Llama)

However, I notice two important missing ablations:

1. The architecture of the projection network itself - the paper uses a 2-layer network with ReLU and batch norm, but doesn't justify this choice or explore alternatives

2. The contrastive learning objective - while the paper uses a specific contrastive loss formulation, it doesn't explore alternative formulations that could potentially work better

These ablations would help understand the importance of these design choices and potentially improve the method further.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Projection Network Architecture Ablation
- **Ablated Part**: The 2-layer architecture of the projection network
- **Action**: REPLACE
- **Replacement**: 
  - single layer network
  - 3-layer network
  - transformer-based projection network
- **Metrics**: Edit Success, Locality, Generalization, Score

### Contrastive Loss Ablation
- **Ablated Part**: The contrastive learning objective
- **Action**: REPLACE
- **Replacement**: 
  - triplet loss
  - InfoNCE loss
  - supervised contrastive loss
- **Metrics**: Edit Success, Locality, Generalization, Score

</div>