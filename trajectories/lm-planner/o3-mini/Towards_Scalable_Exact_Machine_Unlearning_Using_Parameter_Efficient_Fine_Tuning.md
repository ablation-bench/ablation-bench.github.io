<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Towards_Scalable_Exact_Machine_Unlearning_Using_Parameter_Efficient_Fine_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies targeting two of the main components that give S³T its novelty. First, while the paper adopts a sequential top‐to‐bottom slice‐wise training strategy (which enforces parameter isolation) and demonstrates its advantages compared to full training and other baselines, it does not explicitly investigate what happens if the slice ordering is changed. An ablation that replaces the current sequential order with alternative orders (for example, reversing the order to train in a bottom‐to‐top fashion or using a random/non‐sequential order) would help determine how critical the top-to-bottom sequential schedule is for the model’s performance and deletion efficiency. The metrics of interest would include standard performance metrics on benchmarks (accuracy on GLUE, CIFAR, etc.), deletion rate and deletion time. 

Second, S³T is built around a parameter‐efficient fine-tuning method using LoRA, where the low-rank adaptation (the rank “r”) is a key hyperparameter that controls the extent of parameter isolation as well as the storage and computational overhead. While the paper reports results using a fixed LoRA rank, an ablation that replaces the chosen rank with alternative values (for example, testing ranks 4, 8, 16, and 32) could provide insights into the trade-offs between overall task performance, deletion performance (deletion rate and deletion time), and the associated training/storage cost. This ablation would further illuminate the sensitivity of the method to the design choice of low-rank dimensionality.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Impact of Slice Training Order
- **Ablated Part**: The sequential top-to-bottom slice-wise training strategy for parameter isolation in S³T.
- **Action**: REPLACE
- **Replacement**: 
  - Bottom-to-top ordering
  - Random (non-sequential) ordering
- **Metrics**: Task performance (e.g., accuracy on GLUE benchmarks, CIFAR-10/100 metrics), Deletion rate, Deletion time

### Ablation 2: Effect of LoRA Rank Variation
- **Ablated Part**: The fixed low-rank (r) used in the LoRA-based parameter-efficient fine-tuning within S³T.
- **Action**: REPLACE
- **Replacement**: 
  - Rank = 4
  - Rank = 8
  - Rank = 16 (baseline)
  - Rank = 32
- **Metrics**: Task performance (e.g., accuracy on GLUE benchmarks, vision tasks), Deletion rate, Deletion time, Storage cost, Training time

</div>