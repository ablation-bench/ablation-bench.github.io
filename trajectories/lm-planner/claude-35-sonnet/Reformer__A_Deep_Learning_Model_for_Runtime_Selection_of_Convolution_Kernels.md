<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Reformer__A_Deep_Learning_Model_for_Runtime_Selection_of_Convolution_Kernels

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

First, let me identify the key components of the method and existing ablations:

1. The main contribution is the Reformer model which uses Γ-blocks instead of transformer blocks for kernel selection
2. The paper shows comparison between Γ-block and transformer block on IMDB and Reuters datasets (Table 1)
3. The model uses a novel probability assignment approach for training based on kernel runtimes ratios

Looking at missing important ablations:

1. The paper doesn't ablate the number of Γ-blocks used. The model uses 3 blocks (Fig 3A) but there's no justification for this choice. Testing different numbers of blocks would help understand the trade-off between model capacity and inference speed.

2. The paper proposes a novel runtime-ratio based probability assignment for training (equation on page 6) but doesn't compare it against simpler alternatives like one-hot or softmax probabilities which are mentioned in Table 2. This is a critical missing ablation since this is one of their key contributions.

These ablations would help validate two of the main design choices in the paper. I'll rank them by importance, with the probability assignment ablation being more critical since it's a key claimed contribution without empirical validation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Runtime Probability Ablation
- **Ablated Part**: Runtime-ratio based probability assignment for training
- **Action**: REPLACE
- **Replacement**: 
  - one-hot probabilities
  - softmax probabilities
- **Metrics**: kernel selection accuracy, average speedup, inference time

### Block Count Ablation
- **Ablated Part**: Number of Γ-blocks in Reformer
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 4
  - 5
- **Metrics**: kernel selection accuracy, inference time, model size

</div>