<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Hide___Seek__Transformer_Symmetries_Obscure_Sharpness___Riemmanian_Geometry_Finds_It

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a new method for measuring sharpness in transformer models by accounting for symmetries in the attention mechanism using Riemannian geometry. The key components are:

1. A new geodesic sharpness measure that accounts for GL(h) symmetry in transformers
2. A Riemannian quotient manifold approach to handle symmetries
3. Approximation of geodesics using Taylor expansions
4. Application to both diagonal networks and transformers

The paper already includes several ablation studies:
- Ablation of the norm component vs second-order weight corrections (Section G)
- Testing different metrics (Section F.2)
- Testing different relaxation parameters (Section H.2)

However, there are two important missing ablations that could strengthen the paper:

1. The choice of symmetry group: The paper focuses on GL(h) symmetry but doesn't ablate the impact of considering different/additional symmetries in transformers.

2. The geodesic approximation order: The paper uses a second-order Taylor expansion for approximating geodesics but doesn't study the impact of using different orders of approximation.

These ablations would help understand the importance of these key design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Symmetry Group Ablation
- **Ablated Part**: GL(h) symmetry group used for the attention mechanism
- **Action**: REPLACE
- **Replacement**: 
  - GL(1) symmetry
  - GL(h/2) symmetry
  - GL(h) + translation symmetry
- **Metrics**: Kendall tau correlation with generalization, test accuracy

### Geodesic Approximation Order
- **Ablated Part**: Second-order Taylor expansion for geodesic approximation
- **Action**: REPLACE
- **Replacement**: 
  - first-order approximation
  - third-order approximation
- **Metrics**: Kendall tau correlation with generalization, computational cost

</div>