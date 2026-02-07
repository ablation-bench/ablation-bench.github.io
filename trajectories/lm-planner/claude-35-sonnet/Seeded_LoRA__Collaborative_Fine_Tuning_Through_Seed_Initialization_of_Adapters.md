<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Seeded_LoRA__Collaborative_Fine_Tuning_Through_Seed_Initialization_of_Adapters

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

From analyzing the paper, I notice several key ablation studies were already conducted:
1. Comparison of Seeded LoRA with and without the seed expert in the final model (Section F)
2. Comparison of training on individual datasets vs clusters (Sections D, E, G, H)
3. Analysis of different numbers of experts (5, 10, 15, 30 experts mentioned in Section 6)

However, there are two critical missing ablation studies that could provide important insights:

1. The size of the seed data subset - The paper uses 10% of data for the seed expert and mentions "as little as 5% can be sufficient", but doesn't ablate this key hyperparameter. Understanding how the seed data size affects performance would be crucial for practical applications.

2. The initialization strategy of the seed expert - While the paper emphasizes the importance of initialization in the same optimization subspace, it doesn't explore different initialization strategies for the seed expert itself. This could reveal whether the benefits come from the initialization or just from having a common starting point.

These ablations would help validate key claims about the method's robustness and provide practical guidance for implementation.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Seed Data Size Ablation
- **Ablated Part**: percentage of data used for training the seed expert
- **Action**: REPLACE
- **Replacement**: 
  - 1%
  - 5%
  - 10%
  - 20%
  - 30%
- **Metrics**: Average accuracy across 16 tasks, Task-specific accuracies

### Seed Expert Initialization Strategy
- **Ablated Part**: initialization method for the seed expert
- **Action**: REPLACE
- **Replacement**: 
  - random initialization
  - pretrained model weights
  - task-specific initialization
  - meta-learned initialization
- **Metrics**: Average accuracy across 16 tasks, Task-specific accuracies, Linear mode connectivity measure

</div>