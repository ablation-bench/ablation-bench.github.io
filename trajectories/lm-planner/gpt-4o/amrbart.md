<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/amrbart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Graph Pre-training for AMR Parsing and Generation" introduces a novel approach to enhance the structure awareness of pre-trained language models (PLMs) by incorporating graph self-supervised training over AMR graphs. The method involves two graph auto-encoding strategies for graph-to-graph pre-training and four tasks to integrate text and graph information during pre-training. The unified framework is designed to bridge the gap between pre-training and fine-tuning tasks.

To suggest ablation studies, we need to focus on the key components of the method that contribute to its performance. The main components to consider for ablation are:

1. Graph Auto-Encoding Strategies: The paper introduces two strategies for graph pre-training: node/edge level denoising and sub-graph level denoising. Ablating these strategies can help understand their individual contributions.

2. Unified Pre-training Framework: The framework combines text and graph sequences for pre-training, which is crucial for learning the interaction between textual and AMR information. Ablating this framework can reveal its impact on the model's performance.

3. Dynamic Masking Rate: The dynamic masking rate is used to adjust the masking probability during pre-training. Ablating this component can show its effect on the learning process.

4. Joint Text and Graph Pre-training Tasks: The paper introduces four auxiliary tasks to encourage information exchange between graphs and text. Ablating these tasks can help determine their importance in the overall framework.

5. Use of Silver Data: The paper mentions the use of silver data for pre-training. Ablating the use of silver data can help assess its contribution to the model's performance.

Based on these considerations, I suggest the following ablation studies.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Node/Edge Level Denoising Strategy
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR

### Ablation 2
- **Ablated Part**: Sub-Graph Level Denoising Strategy
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR

### Ablation 3
- **Ablated Part**: Unified Pre-training Framework
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR

### Ablation 4
- **Ablated Part**: Dynamic Masking Rate
- **Action**: REPLACE
- **Replacement**: 
  - Static Masking Rate
- **Metrics**: Smatch, BLEU, METEOR

### Ablation 5
- **Ablated Part**: Use of Silver Data
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR

</div>