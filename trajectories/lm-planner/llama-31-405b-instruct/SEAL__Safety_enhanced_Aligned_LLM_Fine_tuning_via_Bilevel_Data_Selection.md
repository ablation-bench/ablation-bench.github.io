<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/SEAL__Safety_enhanced_Aligned_LLM_Fine_tuning_via_Bilevel_Data_Selection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "SEAL: Safety-enhanced Aligned LLM Fine-tuning via Bilevel Data Selection" proposes a novel framework to enhance safety in large language model (LLM) fine-tuning. The authors introduce a bilevel optimization problem to learn a data selector that up-ranks safe and high-quality fine-tuning data and down-ranks unsafe or low-quality ones. The paper presents experimental results on various models, including LLAMA-3-8B-INSTRUCT, MERLINITE-7B, and PYTHIA-2.8B, and demonstrates the effectiveness of the proposed framework in improving the safety and quality of the fine-tuned models.

To further investigate the robustness of the proposed framework, we suggest two missing ablation studies:

1. **Ablation Study 1: Impact of Data Selector Architecture**
The paper uses a softmax function as the data selector. It would be interesting to explore the impact of different data selector architectures on the performance of the SEAL framework. For example, one could compare the performance of the softmax function with other activation functions, such as sigmoid or ReLU.

2. **Ablation Study 2: Effect of Upper-Level Safety Dataset Size**
The paper uses a fixed size for the upper-level safety dataset. It would be useful to investigate how the size of the upper-level safety dataset affects the performance of the SEAL framework. For example, one could compare the performance of the framework with different sizes of the upper-level safety dataset, such as 10%, 20%, or 50% of the total fine-tuning dataset.

These ablation studies can provide further insights into the robustness and generalizability of the proposed framework and help identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: data selector architecture
- **Action**: REPLACE
- **Replacement**: 
  - softmax
  - sigmoid
  - ReLU
- **Metrics**: win rate, safety alignment

### Ablation Study 2
- **Ablated Part**: upper-level safety dataset size
- **Action**: REPLACE
- **Replacement**: 
  - 10%
  - 20%
  - 50%
- **Metrics**: win rate, safety alignment

</div>