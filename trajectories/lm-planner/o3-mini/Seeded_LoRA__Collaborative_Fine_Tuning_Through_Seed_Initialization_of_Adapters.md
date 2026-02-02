<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Seeded_LoRA__Collaborative_Fine_Tuning_Through_Seed_Initialization_of_Adapters

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The Seeded LoRA method relies on two major components: the seed adapter used for initializing all following experts and the simple averaging strategy to merge the adapters’ outputs. However, the paper does not include ablation studies that examine how sensitive the method is to these key design choices. First, while the paper mentions that the seed expert is trained on a small random subset (around 10% of the data, with a note that as little as 5% can be sufficient), it does not explore how varying this fraction influences performance and task interference. Varying the seed data fraction could provide insight into the stability of the common optimization subspace and the trade-off between seed quality and diversity. Second, Seeded LoRA uses simple uniform averaging (each expert equally weighted) to aggregate the adapter outputs. Although the authors explain that this approach is equivalent to uniform routing (grouped convolution) and that more complex routing methods sometimes fail, the paper does not examine whether alternative merging strategies—such as dynamically learned or validation-based weights—could mitigate the potential noise introduced by less effective experts when many adapters are merged. Both aspects are critical to assessing the robustness and optimal design of Seeded LoRA.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Seed Data Fraction Ablation
- **Ablated Part**: The fraction of training data used for the seed adapter
- **Action**: REPLACE
- **Replacement**: 
  - 5%
  - 10%
  - 20%
- **Metrics**: Zero-shot accuracy, Mean task accuracy, Task interference measure

### Expert Merging Strategy Ablation
- **Ablated Part**: The method for merging adapter outputs (aggregation strategy)
- **Action**: REPLACE
- **Replacement**: 
  - simple averaging
  - learned weighted averaging
  - validation-based weighted averaging
- **Metrics**: Zero-shot accuracy, Mean task accuracy, Robustness to ineffective experts

</div>