<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Seeded_LoRA__Collaborative_Fine_Tuning_Through_Seed_Initialization_of_Adapters

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Seeded LoRA: Collaborative Fine-Tuning Through Seed Initialization of Adapters" presents a novel approach to collaborative fine-tuning (CoFT) of large language models. The authors propose a method called Seeded LoRA, which initializes a model before fine-tuning using a generic seed expert low-rank adapter. This approach enables the integration of any combination of independently fine-tuned models through simple averaging of expert adapter outputs.

The paper evaluates Seeded LoRA on 16 different zero-shot tasks and demonstrates that it significantly outperforms LoRA and MoE LoRA (MoLoRA) approaches, improving by an average of 7 percentage points. The authors also analyze the pitfalls of routing mechanisms in CoFT and highlight the benefits of Seeded LoRA in mitigating task interference during fine-tuning.

To further investigate the effectiveness of Seeded LoRA, we suggest two missing ablation studies:

1. **Ablation of the seed expert**: The paper emphasizes the importance of the seed expert in initializing the model before fine-tuning. However, it would be interesting to see how the performance of Seeded LoRA changes without the seed expert. This ablation study would help to understand the contribution of the seed expert to the overall performance of the model.
2. **Comparison with other routing mechanisms**: The paper discusses the pitfalls of routing mechanisms in CoFT and highlights the benefits of Seeded LoRA. However, it would be useful to compare the performance of Seeded LoRA with other routing mechanisms, such as uniform routing or learned routing, to further understand the advantages and limitations of each approach.

These ablation studies would provide additional insights into the effectiveness of Seeded LoRA and help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Seed Expert
- **Ablated Part**: seed expert
- **Action**: REMOVE
- **Metrics**: zero-shot accuracy

### Comparison with Other Routing Mechanisms
- **Ablated Part**: routing mechanism
- **Action**: REPLACE
- **Replacement**: 
  - uniform routing
  - learned routing
- **Metrics**: zero-shot accuracy

</div>