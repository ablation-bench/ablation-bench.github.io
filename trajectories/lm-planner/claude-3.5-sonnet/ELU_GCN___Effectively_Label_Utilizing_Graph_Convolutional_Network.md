<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/ELU_GCN___Effectively_Label_Utilizing_Graph_Convolutional_Network

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes ELU-GCN with two main components:
1. ELU graph learning stage that enables GCNs to effectively utilize label information
2. Graph contrastive learning stage that explores consistency and mutually exclusive information between the learned ELU graph and original graph

The paper already includes some ablation studies as shown in Table 2, where they:
- Test the model with only ELU graph (+ELU graph)
- Test the model with both ELU graph and contrastive loss (+Lcon)

However, there are some important missing ablations that could provide deeper insights:

1. The ELU graph construction involves a key parameter k that determines the order/depth of label propagation when calculating Q(i) iteratively. The paper uses a fixed k but doesn't study its impact. Testing different k values would reveal how the propagation depth affects performance.

2. The paper uses a pre-trained MLP to get node representations H = MLP(X) before constructing the ELU graph. However, they don't ablate different architectures for this MLP or compare against using raw features directly. This would help understand how important the pre-training step is.

I'll suggest these two ablations in order of importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Label Propagation Depth
- **Ablated Part**: The order k of label propagation used when calculating Q(i) iteratively in ELU graph construction
- **Action**: REPLACE
- **Replacement**: 
  - k=1
  - k=2
  - k=3
  - k=5
- **Metrics**: Accuracy, Training Time

### Pre-training Architecture
- **Ablated Part**: The MLP architecture used for pre-training node representations before ELU graph construction
- **Action**: REPLACE
- **Replacement**: 
  - No pre-training (raw features)
  - 1-layer MLP
  - 3-layer MLP
- **Metrics**: Accuracy, Training Time

</div>