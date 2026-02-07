<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Towards_Scalable_Exact_Machine_Unlearning_Using_Parameter_Efficient_Fine_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user requested up to two missing ablation studies for the paper "Towards Scalable Exact Machine Unlearning Using Parameter-Efficient Fine-Tuning". I analyzed the paper's methodology, focusing on the key components of the S3T framework: sharding and slicing, sequential slice-wise PEFT training, training multiple sequences, sequence selection algorithms, and the layer deactivation mechanism for unlearning.

I reviewed the existing experimental evaluations and ablations presented in Section 4 and Appendix C. The paper already evaluates the impact of shard count, slice count, budget size, sequence selection algorithms, layers per slice, and compares S3T against baselines (SISA, ProtoSISA, full retraining, sequential PEFT training).

Based on this analysis, I identified two important aspects of the S3T method that could benefit from further ablation studies to better understand their contribution and limitations:

1.  **The specific sequential and cumulative nature of the slice-wise PEFT training:** The paper describes a top-down, cumulative training process for PEFT layers (Section 3.2, Appendix C.2). While they mention practical reasons for choosing this (e.g., bottom-up convergence issues), an ablation comparing this specific strategy against alternatives (like different layer orders or non-cumulative slice usage per layer) would provide deeper insight into its impact on model performance, training stability, and the effectiveness of the layer deactivation for unlearning. This directly probes a core, novel part of the S3T training procedure.
2.  **The choice of PEFT method:** The paper states that S3T is general and can be extended to other PEFT techniques but primarily uses LoRA in its experiments. An ablation study comparing S3T implemented with different PEFT methods would validate this claim of generality and assess whether the observed benefits are specific to LoRA or apply more broadly. This is important for understanding the framework's applicability.

I decided to propose these two ablations as they address fundamental design choices within the S3T framework that are not fully explored through ablation in the current paper. I ranked the sequential training strategy ablation slightly higher as it investigates the specific *process* of creating parameter isolation, which is central to S3T's mechanism. The PEFT method ablation investigates the *tool* used for isolation and its generality.

For each ablation, I defined the ablated part, the action (REPLACE), potential replacements, and relevant metrics based on those used in the paper (Performance, Deletion Rate, Performance retention, Storage cost, Training time).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Sequential Training Strategy Ablation
- **Ablated Part**: The specific sequential layer training order (top-down) and cumulative slice usage during slice-wise PEFT layer training.
- **Action**: REPLACE
- **Replacement**: 
  - Layer Order: Bottom-up
  - Layer Order: Random order
  - Slice Usage: Train PEFT layers for slice i only on data from slice i (non-cumulative)
- **Metrics**: Performance (task-specific metrics as in paper), Performance retention after deletions, Training time

### PEFT Method Ablation
- **Ablated Part**: The specific Parameter-Efficient Fine-Tuning (PEFT) technique (LoRA) used for parameter isolation.
- **Action**: REPLACE
- **Replacement**: 
  - Prefix Tuning
  - Adapter layers
- **Metrics**: Performance (task-specific metrics as in paper), Deletion Rate, Performance retention after deletions, Storage cost, Training time

</div>