<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Using_semantic_distance_for_diverse_and_sample_efficient_genetic_programming

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The first missing ablation we suggest focuses on the choice of the semantic distance function in equation (2) – a crucial component since it determines how “semantically similar” or “distinct” the mutated programs are. In the paper, the authors use an L1 distance with a specific scaling function. However, it is unclear how sensitive the overall performance is to this choice. An ablation study replacing the L1 distance with other metrics (such as L2 distance or cosine similarity) and testing different scaling functions would provide insight into the robustness of the method with respect to the distance metric design.

The second missing ablation study examines the effect of sampling the mutation hyperparameters µ and β versus using fixed values. The current method re-samples µ ∼ U(0, 0.4) and β ∼ exp(U(–6, –1)) at each mutation, likely to adapt to different regions of the fitness landscape. An ablation that fixes µ and β to constant values (with a few candidate pairs) would help determine to what degree this stochasticity contributes to sample efficiency and overall performance in tasks such as function regression and optimizer discovery.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Distance Metric Ablation
- **Ablated Part**: The semantic distance function used in the mutation objective, including the L1 norm and its associated scaling function.
- **Action**: REPLACE
- **Replacement**: 
  - L2 distance
  - Cosine similarity
  - Alternative scaling functions
- **Metrics**: function regression fitness, sample efficiency, graph node count

### Fixed Hyperparameters Ablation
- **Ablated Part**: The stochastic sampling of mutation hyperparameters µ and β in the mutation objective.
- **Action**: REPLACE
- **Replacement**: 
  - Fixed µ=0.2, β=exp(-3.5)
  - Fixed µ=0.1, β=0.01
  - Fixed µ=0.4, β=0.3
- **Metrics**: optimizer fitness, sample efficiency, final evaluation performance

</div>