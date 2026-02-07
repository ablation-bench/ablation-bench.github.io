<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Finetuning_CLIP_to_Reason_about_Pairwise_Differences

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

From analyzing the paper, I notice that the authors have already conducted several ablation studies, including:

1. Testing different loss functions (contrastive vs MSE) for the finetuning objective
2. Evaluating the impact of filtering LLM generations vs using unfiltered data
3. Testing different pretraining datasets (COCO vs CUB) for generating comparisons
4. Evaluating different model scales (ViT-L vs ViT-H)

However, there are two critical missing ablation studies that would help better understand the method's key components:

1. The choice of LLM for generating comparisons - The authors only use LLaMA2-13B-chat for generating the comparisons. Testing different LLMs (e.g., GPT-3, PaLM) would help understand how sensitive the method is to the choice of LLM and quality of generated comparisons.

2. The impact of finetuning both encoders vs just text encoder - The authors only finetune the text encoder while keeping the image encoder fixed. Testing joint finetuning of both encoders would help understand if this design choice is optimal.

These ablations would provide important insights into the robustness and design choices of the method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### LLM Choice Ablation
- **Ablated Part**: LLM used for generating comparisons
- **Action**: REPLACE
- **Replacement**: 
  - GPT-3
  - PaLM
  - LLaMA-7B
- **Metrics**: difference-based classification accuracy, zeroshot classification accuracy, CLIPScore

### Encoder Finetuning Ablation
- **Ablated Part**: Which encoders are finetuned
- **Action**: REPLACE
- **Replacement**: 
  - text encoder only
  - image encoder only
  - both encoders
- **Metrics**: difference-based classification accuracy, zeroshot classification accuracy, CLIPScore

</div>