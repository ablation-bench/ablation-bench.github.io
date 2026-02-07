<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Unlocking_the_Power_of_Representations_in_Long_term_Novelty_based_Exploration

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents RECODE, a non-parametric method for novelty-based exploration that uses clustering-based online density estimation. The key components are:

1. The memory mechanism that stores clusters of states and their visitation counts
2. The representation learning method (either AP or CASM)

Looking at the existing ablations in the paper:
- They test different removal strategies for clusters (1/c^2, 1/c, smallest count)
- They analyze the effect of discount factor γ
- They compare AP vs CASM representations
- They test different memory sizes and insertion probabilities η
- They evaluate RECODE with different base representations (AP, CASM, BYOL)

However, I notice two important missing ablations:

1. The effect of the kernel function choice - they use a specific kernel in Eq. 3 but don't justify this choice or compare to alternatives. This is important since the kernel determines how similarity between states is measured.

2. The effect of the cluster count redistribution strategy - when removing a cluster, they redistribute its count to the nearest neighbor, but don't evaluate alternative redistribution strategies which could affect the long-term memory properties.

These are important aspects that could significantly impact the method's performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Kernel Function Ablation
- **Ablated Part**: Kernel function used for computing state similarities (Eq. 3)
- **Action**: REPLACE
- **Replacement**: 
  - Gaussian kernel
  - Exponential kernel
  - Cosine similarity
- **Metrics**: Human Normalized Score, Mean Capped HNS, AUC

### Count Redistribution Ablation
- **Ablated Part**: Strategy for redistributing counts when removing clusters
- **Action**: REPLACE
- **Replacement**: 
  - Distribute to k nearest neighbors
  - Distribute proportionally to similarity
  - No redistribution
- **Metrics**: Human Normalized Score, Mean Capped HNS, AUC

</div>