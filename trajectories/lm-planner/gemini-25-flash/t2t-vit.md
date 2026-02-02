<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/t2t-vit

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 ablation studies for the paper "Tokens-to-Token ViT: Training Vision Transformers from Scratch on ImageNet". I need to identify the key contributions of the paper and propose experiments that isolate their impact on performance. The output should be in JSONL format with specific fields and ranked by importance.

The main contributions highlighted in the abstract and introduction are:
1.  The Tokens-to-Token (T2T) transformation module for progressive tokenization and local structure modeling.
2.  An efficient backbone with a deep-narrow structure, motivated by CNN design.
3.  Achieving strong performance when trained *from scratch* on ImageNet, unlike the original ViT which requires large pre-training datasets.

Based on these, I will propose ablation studies focusing on the T2T module and the backbone architecture.

1.  **Ablating the T2T module:** The T2T module is presented as a core innovation to address ViT's inability to model local structure. The most important ablation is to replace this progressive tokenization with the simple, non-overlapping patch splitting used in the original ViT. This directly tests the value of the T2T approach.
2.  **Ablating the efficient backbone:** The paper claims the deep-narrow backbone is more efficient and improves feature richness compared to the standard ViT backbone. An ablation should replace the T2T-ViT backbone with a standard ViT-like backbone (e.g., wider and shallower, while keeping parameters/MACs roughly comparable if possible, or using a standard ViT configuration like Base/16) to see the performance difference.
3.  **Varying T2T module design:** The T2T module involves iterative steps. The paper uses 2 iterations ($n=2$). Ablating the number of iterations (e.g., using 1 or 3) would show how the depth of the progressive tokenization affects the outcome.
4.  **T2T Transformer Type:** The paper mentions using Performer or Transformer layers within the T2T module, noting Performer for memory efficiency. Comparing the performance when using standard Transformer vs. Performer in the T2T module would be a relevant ablation, as the paper provides a specific model (T2T-ViT$_t$-14) for this comparison.

The primary metrics used in the paper are Top-1 and Top-5 accuracy on ImageNet.

Ranking the ablations by importance:
1.  Replacing the entire T2T module with standard patch embedding is the most fundamental test of the T2T concept itself.
2.  Testing the impact of the deep-narrow backbone architecture is the second major component to evaluate.
3.  Exploring variations within the T2T module, such as the number of iterations, is important for understanding its design space.
4.  Comparing the specific transformer type (Performer vs. Transformer) within T2T is a more specific implementation detail ablation.

I will generate the JSONL output for these four ablations.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### T2T Module Effectiveness
- **Ablated Part**: Tokens-to-Token (T2T) progressive tokenization module
- **Action**: REPLACE
- **Replacement**: 
  - Standard ViT patch embedding (non-overlapping, single layer)
- **Metrics**: Top-1 Accuracy, Top-5 Accuracy

### Backbone Architecture Impact
- **Ablated Part**: T2T-ViT deep-narrow backbone structure
- **Action**: REPLACE
- **Replacement**: 
  - Standard ViT-like backbone (e.g., wider/shallower with similar parameters/MACs)
- **Metrics**: Top-1 Accuracy, Top-5 Accuracy

### T2T Iterations
- **Ablated Part**: Number of iterations in the T2T module
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
- **Metrics**: Top-1 Accuracy, Top-5 Accuracy

### T2T Transformer Type
- **Ablated Part**: Type of transformer layer in the T2T module
- **Action**: REPLACE
- **Replacement**: 
  - Transformer
  - Performer
- **Metrics**: Top-1 Accuracy, Top-5 Accuracy

</div>