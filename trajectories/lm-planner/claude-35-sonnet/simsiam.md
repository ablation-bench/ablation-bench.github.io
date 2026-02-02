<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/simsiam

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, SimSiam's key components are:

1. The stop-gradient operation, which is claimed to be essential for preventing collapse
2. The prediction MLP (h) with specific architecture (2 layers, bottleneck structure)
3. The projection MLP (f) with 3 layers and batch normalization
4. The symmetric loss function combining both directions
5. The specific augmentation strategy (though not detailed in the main text)

The most critical aspects to ablate would be:

1. The stop-gradient operation since it's claimed to be essential for preventing collapse
2. The prediction MLP architecture since it's a key architectural choice
3. The loss symmetry since it affects how the two views interact
4. The projection MLP design since it affects the learned representations
5. The augmentation strategy since it defines the invariances being learned

The metrics used in the paper are:
- Linear evaluation accuracy on ImageNet
- kNN classifier accuracy as a training progress monitor
- Standard deviation of l2-normalized outputs (to detect collapse)
- Training loss curves
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Stop-gradient Ablation
- **Ablated Part**: stop-gradient operation
- **Action**: REMOVE
- **Metrics**: linear_eval_accuracy, knn_accuracy, output_std, training_loss

### Prediction MLP Architecture
- **Ablated Part**: prediction MLP structure
- **Action**: REPLACE
- **Replacement**: 
  - single layer MLP
  - 3-layer MLP
  - same dimension as input
- **Metrics**: linear_eval_accuracy, knn_accuracy

### Loss Symmetry
- **Ablated Part**: symmetric loss function
- **Action**: REPLACE
- **Replacement**: 
  - only p1->z2 direction
  - only p2->z1 direction
- **Metrics**: linear_eval_accuracy, knn_accuracy, training_loss

### Projection MLP
- **Ablated Part**: projection MLP in encoder
- **Action**: REPLACE
- **Replacement**: 
  - 2-layer MLP
  - 4-layer MLP
  - no projection MLP
- **Metrics**: linear_eval_accuracy, knn_accuracy

### Batch Normalization
- **Ablated Part**: batch normalization in prediction MLP
- **Action**: REMOVE
- **Metrics**: linear_eval_accuracy, knn_accuracy, training_loss

</div>