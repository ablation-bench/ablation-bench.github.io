<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Answer_Me_if_You_Can__Debiasing_Video_Question_Answering_via_Answering_Unanswerable_Questions

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Answer Me if You Can: Debiasing Video Question Answering via Answering Unanswerable Questions" proposes a novel framework for debiasing video question answering (VideoQA) models by leveraging unanswerable questions to capture the bias in the dataset. The framework, called VoidQ, uses a causal intervention to remove the effect of confounders, which are variables that affect both the input and the answer. The authors demonstrate the effectiveness of their approach through experiments on multiple VideoQA benchmark datasets.

To further investigate the robustness of the proposed framework, we suggest two missing ablation studies:

1. **Effect of different types of unanswerable questions**: The current framework uses unanswerable questions that are constructed by pairing a text and a video from two different samples. It would be interesting to explore the effect of using different types of unanswerable questions, such as questions that are unrelated to the video content or questions that are semantically incorrect.
2. **Impact of the number of confounder queries on performance**: The authors use a fixed number of confounder queries (M = 128) in their experiments. It would be useful to investigate how the number of confounder queries affects the performance of the model. Specifically, how does the model perform with a smaller or larger number of confounder queries?

These ablation studies can provide further insights into the robustness and generalizability of the proposed framework.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: type of unanswerable questions
- **Action**: REPLACE
- **Replacement**: 
  - unrelated questions
  - semantically incorrect questions
- **Metrics**: accuracy, confidence score

### Ablation B
- **Ablated Part**: number of confounder queries
- **Action**: REPLACE
- **Replacement**: 
  - 64
  - 256
  - 512
- **Metrics**: accuracy, confidence score

</div>