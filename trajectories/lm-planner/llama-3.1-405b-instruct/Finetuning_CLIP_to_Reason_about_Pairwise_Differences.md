<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Finetuning_CLIP_to_Reason_about_Pairwise_Differences

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Finetuning CLIP to Reason about Pairwise Differences" proposes a method to improve the embedding space of CLIP by generating language descriptions of the difference between images and using this dataset to improve the joint embedding space of CLIP to reflect more interpretable differences between classes. The authors demonstrate that their finetuning enables the ability to perform general difference-based classification while generally improving or maintaining standard zeroshot prompting performance with their updated VLM. They also show that their finetuning generally improves the VLM's embedding space and its ability to perform arithmetic.

To further investigate the effectiveness of their method, I suggest two missing ablation studies:

1. Ablation study on the impact of the number of LLM-generated comparisons on the performance of PC-CLIP. This study would help understand how the number of comparisons affects the performance of PC-CLIP and whether there is a point of diminishing returns.
2. Ablation study on the impact of the type of LLM used to generate comparisons on the performance of PC-CLIP. This study would help understand whether the performance of PC-CLIP is sensitive to the type of LLM used and whether some LLMs are more effective than others in generating comparisons.

These ablation studies would provide valuable insights into the effectiveness of the proposed method and help identify areas for further improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study 1
- **Ablated Part**: number of LLM-generated comparisons
- **Action**: REMOVE
- **Metrics**: difference-based classification accuracy, zeroshot classification accuracy

### Ablation Study 2
- **Ablated Part**: type of LLM
- **Action**: REPLACE
- **Replacement**: 
  - LLaMA2-13B
  - GPT4
  - T5
- **Metrics**: difference-based classification accuracy, zeroshot classification accuracy

</div>