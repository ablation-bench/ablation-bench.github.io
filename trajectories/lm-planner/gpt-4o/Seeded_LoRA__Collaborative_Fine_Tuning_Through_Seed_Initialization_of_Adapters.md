<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Seeded_LoRA__Collaborative_Fine_Tuning_Through_Seed_Initialization_of_Adapters

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Seeded LoRA: Collaborative Fine-Tuning Through Seed Initialization of Adapters" introduces a novel approach to Collaborative Fine-Tuning (CoFT) that eliminates the need for post-merge fine-tuning by using a seed expert for initialization. The paper presents several experiments comparing Seeded LoRA with other methods like LoRA and MoLoRA, demonstrating its superior performance across various tasks. The existing ablation studies in the paper focus on the effectiveness of Seeded LoRA in mitigating task interference and the impact of routing failures.

To suggest missing ablation studies, we need to identify key components of the Seeded LoRA method that have not been thoroughly investigated. One such component is the choice of the seed expert's data subset. The paper mentions that the seed expert is trained on a random subset of the data, but it does not explore the impact of different data selection strategies on the performance of Seeded LoRA. Another potential area for ablation is the averaging mechanism used to combine the outputs of the experts. The paper claims that simple averaging is effective, but it does not compare this with other potential aggregation methods.

Therefore, the two missing ablation studies I suggest are: 
1. Investigating the impact of different data selection strategies for the seed expert.
2. Exploring alternative aggregation methods for combining expert outputs.

These ablations will help to better understand the robustness and flexibility of the Seeded LoRA approach.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Seed Expert Data Selection
- **Ablated Part**: Data subset selection for seed expert training
- **Action**: REPLACE
- **Replacement**: 
  - Random subset
  - Domain-specific subset
  - Balanced subset
- **Metrics**: Zero-shot accuracy, Task interference

### Ablation 2: Expert Output Aggregation
- **Ablated Part**: Aggregation method for expert outputs
- **Action**: REPLACE
- **Replacement**: 
  - Simple averaging
  - Weighted averaging
  - Max pooling
- **Metrics**: Zero-shot accuracy, Inference time

</div>