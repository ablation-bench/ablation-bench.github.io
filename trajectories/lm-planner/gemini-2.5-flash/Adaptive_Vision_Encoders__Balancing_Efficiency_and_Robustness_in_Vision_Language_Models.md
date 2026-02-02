<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Adaptive_Vision_Encoders__Balancing_Efficiency_and_Robustness_in_Vision_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes LoRSU, a novel parameter-efficient fine-tuning method for vision encoders in VLMs, designed to be efficient and preserve generic knowledge. LoRSU achieves this by selectively updating parameters in two key areas: the first linear layer (MLP) of each transformer block based on gradient norm sparsity, and the most informative attention heads based on their cumulative gradient norm. These selected attention heads are then updated using LoRA. The paper demonstrates LoRSU's effectiveness compared to other PEFT methods (F-FT, F-EWC, LN, LoRA, SPU) on image classification and VQA tasks, showing superior performance on target datasets with minimal forgetting on control datasets. They also compare updating the vision encoder (LoRSU-V) versus the LLM (LoRSU-L, LoRSU-L+), highlighting the efficiency and effectiveness of the vision-only update. The existing ablation studies in the paper include a comparison of LoRSU against other methods and an ablation on the LoRA rank (r) used within LoRSU.

While the paper effectively demonstrates LoRSU's overall performance, it lacks ablation studies that isolate the contribution of the specific components *within* the LoRSU method itself. LoRSU is presented as a combination of selective MLP updates and selective attention head updates with LoRA. It is crucial to understand the individual contribution of each of these selective update strategies to the method's success in balancing target performance and knowledge preservation.

Therefore, the first suggested missing ablation study is to evaluate the performance when only one of the selective update mechanisms is used, removing the other. This would involve two experiments: one where only the selective MLP update is applied (effectively similar to SPU but within the LoRSU framework's overall setup), and one where only the selective attention head update with LoRA is applied (no MLP sparsity). Comparing these variants to the full LoRSU method would clarify the necessity and contribution of combining both selective updates.

The second suggested missing ablation study focuses on the hyperparameters governing the selection process. The paper fixes the sparsity percentage for the MLP layer (10%) and the number of top attention heads (k=2) for LoRSU, while ablating the LoRA rank (r). Understanding the sensitivity of LoRSU's performance and robustness to the number of selected attention heads (k) is important. Ablating this parameter would reveal how the choice of k impacts the trade-off between target improvement and forgetting.

These two ablations are important because they directly investigate the core design principles of LoRSU – the combination of selective updates and the specific criteria for selecting which parameters/heads to update. They would provide deeper insight into *why* LoRSU works and how its components contribute to its reported state-of-the-art performance and robustness. The metrics used should align with those reported in the paper, specifically the Target Improvement and Average Control Change for both image classification and VQA accuracy.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### LoRSU MLP Only
- **Ablated Part**: Selective Attention Head updates (with LoRA) in LoRSU
- **Action**: REMOVE
- **Metrics**: Target Improvement (Classification), Average Control Change (Classification), Target Improvement (VQA), Average Control Change (VQA)

### LoRSU Attention Heads Only
- **Ablated Part**: Selective MLP updates in LoRSU
- **Action**: REMOVE
- **Metrics**: Target Improvement (Classification), Average Control Change (Classification), Target Improvement (VQA), Average Control Change (VQA)

### LoRSU Attention Head Count
- **Ablated Part**: Number of top attention heads selected for updating in LoRSU
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 4
  - 8
  - All
- **Metrics**: Target Improvement (Classification), Average Control Change (Classification), Target Improvement (VQA), Average Control Change (VQA)

</div>