<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Seeded_LoRA__Collaborative_Fine_Tuning_Through_Seed_Initialization_of_Adapters

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Seeded LoRA: Collaborative Fine-Tuning Through Seed Initialization of Adapters" introduces Seeded LoRA, a method for collaborative fine-tuning that avoids post-merge fine-tuning by initializing task-specific LoRA adapters from a common "seed expert" adapter. This seed expert is trained on a small random subset of the data, aiming to align the optimization subspaces of subsequent task-specific adapters, enabling simple averaging for merging.

The paper presents several experiments comparing Seeded LoRA to baselines (LoRA, MoLoRA) and analyzing aspects of routing. Crucially, Appendix E provides an ablation study comparing Seeded LoRA *with* seed expert initialization to Seeded LoRA *without* it, demonstrating the benefit of the seed initialization itself. Appendix F explores including the seed expert in the final average. Section 6 and 7 discuss the merging mechanism (simple averaging) in comparison to learned routing.

While the paper establishes the importance of the seed initialization, it does not systematically explore the hyperparameters related to the seed expert training or the number of experts used. Two important missing ablation studies are identified:

1.  **Seed Data Percentage:** The paper states that the seed expert is trained on a "small random subset" (10%, with mention that 5% can be sufficient) and that the exact data is less important than achieving a common subspace. However, the sensitivity of Seeded LoRA's performance to the *percentage* of data used for training the seed expert is not shown. An ablation varying this percentage would validate the claim that a small amount is sufficient and determine the optimal range or minimum requirement. This is crucial for understanding the practical application and robustness of the method.

2.  **Number of Experts:** Seeded LoRA merges multiple task-specific experts via simple averaging. The main results (Table 1) use a specific number of experts (implied to be 8 based on Figure 1 and Section 4.1). The Limitations section mentions that averaging has "inherent limits as ineffective experts add more and more noise" when "too many experts are merged". An ablation varying the number of experts would demonstrate how the performance scales with the number of merged adapters and empirically investigate the point at which averaging might become less effective, as suggested by the limitations. This is important for understanding the scalability and practical limits of the simple averaging approach.

These two ablations are important because they investigate key hyperparameters of the Seeded LoRA method that directly impact its core components: the seed initialization process and the expert merging mechanism. The metrics used in the paper, particularly average zero-shot accuracy and per-task accuracy, are suitable for evaluating these ablations.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Seed Data Percentage Ablation
- **Ablated Part**: Percentage of training data used for the seed expert
- **Action**: REPLACE
- **Replacement**: 
  - 0.01
  - 0.05
  - 0.1
  - 0.2
- **Metrics**: Average Zero-shot Accuracy, Zero-shot Accuracy per Task

### Number of Experts Ablation
- **Ablated Part**: Number of dataset-specific experts
- **Action**: REPLACE
- **Replacement**: 
  - 4
  - 8
  - 16
  - 32
- **Metrics**: Average Zero-shot Accuracy, Zero-shot Accuracy per Task

</div>