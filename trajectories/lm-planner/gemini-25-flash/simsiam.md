<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/simsiam

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The SimSiam paper proposes a simple Siamese network architecture for unsupervised representation learning that avoids collapsing solutions without relying on negative pairs, large batches, or momentum encoders. The core components highlighted in the paper are the Siamese structure with shared weights, the projection and prediction MLP heads, the negative cosine similarity loss, and critically, the stop-gradient operation.

Based on the paper's emphasis and the novelty of the SimSiam approach, the most important ablation studies should focus on understanding which components are essential for preventing collapse and achieving good performance.

1.  **Stop-Gradient:** The paper explicitly identifies the stop-gradient operation as critical for preventing collapsing solutions and provides empirical evidence (Figure 2). Ablating this component is the most direct way to verify this claim and understand its necessity.
2.  **Prediction MLP:** SimSiam uses a prediction MLP ($h$) on one branch. This is a departure from simpler Siamese setups and is also present in related methods like BYOL. Ablating this MLP helps determine if this non-linear transformation and bottleneck structure are necessary for the method's success or for preventing collapse.
3.  **Projection MLP:** The encoder $f$ includes a projection MLP head after the backbone. This is a common practice in recent self-supervised methods. Ablating this head helps understand its role in transforming the backbone features into a space suitable for the prediction and similarity comparison.
4.  **Symmetrized Loss:** The loss function is symmetrized by swapping the inputs to the prediction head and stop-gradient. While common, it's important to verify if this symmetrization is necessary or if an asymmetric loss would suffice or perform differently.

These four ablations cover the most significant architectural and functional choices made in SimSiam, particularly those related to the interaction between the two branches and the prevention of collapse. The metrics chosen (linear evaluation accuracy, kNN accuracy, training loss, representation std) are directly taken from the paper's own evaluation methodology, allowing for direct comparison and analysis of the impact of each ablation on learning progress and final representation quality.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Stop-Gradient
- **Ablated Part**: Stop-gradient operation in the loss function
- **Action**: REMOVE
- **Metrics**: ImageNet linear evaluation accuracy, kNN accuracy, Training loss, Representation std

### Ablation: Prediction MLP
- **Ablated Part**: Prediction MLP head (h)
- **Action**: REMOVE
- **Metrics**: ImageNet linear evaluation accuracy, kNN accuracy, Training loss, Representation std

### Ablation: Projection MLP
- **Ablated Part**: Projection MLP head (part of f)
- **Action**: REMOVE
- **Metrics**: ImageNet linear evaluation accuracy, kNN accuracy, Training loss, Representation std

### Ablation: Symmetrized Loss
- **Ablated Part**: Symmetrization of the loss function
- **Action**: REPLACE
- **Replacement**: 
  - Asymmetric loss (D(p1, stopgrad(z2)))
- **Metrics**: ImageNet linear evaluation accuracy, kNN accuracy, Training loss, Representation std

</div>