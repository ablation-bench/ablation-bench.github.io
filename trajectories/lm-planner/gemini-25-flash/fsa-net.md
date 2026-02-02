<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/fsa-net

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The FSA-Net paper proposes a compact model for head pose estimation using soft stagewise regression (SSR-Net-MD) and a novel fine-grained structure aggregation module. The core components identified are the SSR-Net-MD base architecture, the fine-grained structure mapping which spatially groups features using attention maps, the scoring function that generates these attention maps, the two-stream network architecture, and the number of stages in the SSR process.

To understand the contribution of these components, we propose five ablation studies, ranked by their importance in validating the paper's claims and understanding the model's performance drivers.

1.  **Ablation: Fine-Grained Mapping:** This is the central novelty of the paper. Ablating this module by replacing it with a more standard pooling mechanism before the final regression layers will directly show the performance gain attributed to the proposed fine-grained structure mapping.
2.  **Ablation: SSR Head:** The paper builds upon SSR-Net for compactness and stagewise regression. Replacing the SSR head with a standard direct regression head (e.g., fully connected layers predicting angles directly) will demonstrate the effectiveness and potential benefits (like compactness or performance) of using the SSR approach for this task.
3.  **Ablation: Scoring Function Type:** The paper explores different methods for generating the attention maps used in the fine-grained mapping (learnable 1x1 Conv, non-learnable Variance, constant Uniform). Comparing models trained with each of these scoring functions individually is crucial to understand which type of attention is most effective and if learned attention is necessary.
4.  **Ablation: Single Stream:** The network uses a two-stream architecture with different properties (ReLU/AvgPool vs. Tanh/MaxPool). Ablating one of the streams will show whether the combination of these two streams is necessary for optimal performance or if a single stream is sufficient. This also impacts model size.
5.  **Ablation: Number of Stages:** The SSR-Net-MD uses K=3 stages. Varying the number of stages will reveal the sensitivity of the model's performance and size to the granularity of the stagewise regression and multi-scale feature aggregation.

The primary metrics used in the paper are Mean Absolute Error (MAE) for yaw, pitch, and roll angles. Model size is also a key claim of the paper, so it's included where relevant (for ablations affecting the overall architecture size).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Fine-Grained Mapping
- **Ablated Part**: Fine-Grained Structure Mapping module (S=CM) and its dependence on attention maps
- **Action**: REPLACE
- **Replacement**: 
  - Standard Pooling (e.g., Global Average Pooling or fixed grid pooling) before final aggregation
- **Metrics**: MAE (yaw), MAE (pitch), MAE (roll)

### Ablation: SSR Head
- **Ablated Part**: Soft Stagewise Regression (SSR) head
- **Action**: REPLACE
- **Replacement**: 
  - Standard Direct Regression Head (Fully Connected Layers)
- **Metrics**: MAE (yaw), MAE (pitch), MAE (roll)

### Ablation: Scoring Function Type
- **Ablated Part**: Type of Scoring Function (Attention Mechanism) used to generate attention maps A^k
- **Action**: REPLACE
- **Replacement**: 
  - 1x1 Convolution (Learnable)
  - Variance (Non-learnable)
  - Uniform (Constant)
- **Metrics**: MAE (yaw), MAE (pitch), MAE (roll)

### Ablation: Single Stream
- **Ablated Part**: Two-Stream Architecture
- **Action**: REPLACE
- **Replacement**: 
  - Single Stream (BR layers)
  - Single Stream (BT layers)
- **Metrics**: MAE (yaw), MAE (pitch), MAE (roll), Model Size (MB)

### Ablation: Number of Stages
- **Ablated Part**: Number of Stages (K) in the SSR-Net-MD architecture
- **Action**: REPLACE
- **Replacement**: 
  - 2
  - 4
- **Metrics**: MAE (yaw), MAE (pitch), MAE (roll), Model Size (MB)

</div>