<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Finetuning_CLIP_to_Reason_about_Pairwise_Differences

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces PC-CLIP by aligning the difference between image embeddings (computed via subtraction) and LLM-generated textual descriptions to improve reasoning over pairwise differences. However, there are some important design decisions that are not thoroughly studied by ablation experiments. One such decision is the choice of finetuning strategy: the authors update only the text encoder, leaving the image encoder fixed. It is important to study whether finetuning both encoders jointly would further improve the geometric structure of the embedding space (especially for difference-based classification) and how that might affect downstream tasks such as zeroshot classification and text-to-image generation quality (e.g., measured by CLIPScore). Another critical design component is the specific operation used to combine the two image embeddings into a difference vector (currently computed as the element-wise subtraction). An ablation that experiments with replacing subtraction—for example, using concatenation or element-wise multiplication—would help in understanding how much the specific arithmetic operation contributes to the improved alignment and performance. These two missing ablation studies would shed light on the importance of updating both encoders versus only the text encoder and on the role of the subtraction operation in aligning pairwise differences.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Joint Encoder Finetuning Ablation
- **Ablated Part**: The finetuning strategy where only the text encoder is updated (with the image encoder fixed) in PC-CLIP
- **Action**: REPLACE
- **Replacement**: 
  - text encoder only
  - text encoder + image encoder joint finetuning
- **Metrics**: difference-based classification accuracy, zeroshot classification accuracy, CLIPScore

### Image Pair Combination Operation Ablation
- **Ablated Part**: The operation used to combine the image embeddings (currently element-wise subtraction) to form the pairwise difference
- **Action**: REPLACE
- **Replacement**: 
  - subtraction (baseline)
  - concatenation
  - element-wise multiplication
- **Metrics**: difference-based classification accuracy, zeroshot classification accuracy, embedding arithmetic evaluation

</div>