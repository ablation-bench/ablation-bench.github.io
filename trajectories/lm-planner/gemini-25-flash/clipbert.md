<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/clipbert

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 important ablation studies for the paper "Less is More: CLIPBERT for Video-and-Language Learning via Sparse Sampling". I need to identify key components of the ClipBERT method and propose experiments to understand their contribution, using the metrics mentioned in the paper (R@K for retrieval, Accuracy for VQA). The output must be in a specific JSONL format, ranked by importance.

Based on the paper's abstract and method section, the core ideas are sparse sampling for training, end-to-end learning, using a 2D CNN vision backbone, and leveraging image-text pre-training. The method involves encoding sparsely sampled clips and text, fusing them with a Transformer, and aggregating clip-level predictions.

The paper already includes some ablations, notably varying the number of training clips ($N_{train}$) and discussing pre-training strategies. I will focus on other crucial aspects not explicitly detailed as ablations in the provided text snippets, or aspects that warrant further investigation.

Key components to consider for ablation:
1.  **Sparse Sampling Strategy:** While $N_{train}$ is ablated, the inference strategy ($N_{test}$ and aggregation $\mathcal{G}$) is also critical.
2.  **End-to-end Training:** The paper claims this is important, but a direct comparison within their framework (fixed vs. finetuned encoders) is a strong ablation.
3.  **Vision Encoding:** This involves the choice of backbone, temporal fusion ($\mathcal{M}$), number of frames per clip ($T$), and 2D position embedding.
4.  **Cross-modal Fusion:** The Transformer architecture.
5.  **Pre-training:** The paper discusses it, but specific comparisons (e.g., ImageNet vs. Image-Text pre-training for vision) are valuable.

Considering the importance and likelihood of not being fully covered in the provided text:

1.  **Prediction Aggregation Function ($\mathcal{G}$):** How predictions from multiple clips are combined at inference is a direct part of the sparse-training-dense-inference strategy. Different aggregation methods could have a significant impact.
2.  **Number of Inference Clips ($N_{test}$):** While training is sparse, inference uses multiple clips. The number of clips used at inference affects both performance (coverage of the video) and computational cost.
3.  **Temporal Fusion Method ($\mathcal{M}$):** The method used to combine frame features within a single clip is a key step in generating the clip representation.
4.  **Vision Backbone Architecture:** The choice of the 2D CNN backbone (ResNet-50) is a fundamental architectural decision. Comparing it to other standard backbones would show its specific contribution.
5.  **2D Position Embedding:** The use of 2D position embeddings for visual features is a specific design choice for the Transformer input. Removing it would test its necessity.

These five ablations cover different levels of the model, from the final prediction aggregation to the initial visual feature processing and architectural choices. They are ranked based on their direct relevance to the core sparse sampling/aggregation strategy and the visual encoding pipeline.

The metrics used in the paper are R@1, R@5, R@10 for text-to-video retrieval and Accuracy for video question answering. I will include these.

I will now format the output as JSONL.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Prediction Aggregation
- **Ablated Part**: Function for aggregating clip predictions at inference
- **Action**: REPLACE
- **Replacement**: 
  - Mean Pooling
  - Max Pooling
  - Sum Pooling
- **Metrics**: R@1, R@5, R@10, Accuracy

### Inference Clip Count
- **Ablated Part**: Number of uniformly sampled clips during inference (N_test)
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 8
  - 32
  - 64
- **Metrics**: R@1, R@5, R@10, Accuracy

### Temporal Fusion Method
- **Ablated Part**: Method for aggregating frame features into clip features
- **Action**: REPLACE
- **Replacement**: 
  - Mean Pooling
  - Max Pooling
  - Attention Pooling
- **Metrics**: R@1, R@5, R@10, Accuracy

### Vision Backbone Architecture
- **Ablated Part**: Vision encoder architecture
- **Action**: REPLACE
- **Replacement**: 
  - ResNet-50
  - ResNet-101
  - EfficientNet-B0
- **Metrics**: R@1, R@5, R@10, Accuracy

### Visual Position Embedding
- **Ablated Part**: 2D position embedding for visual features
- **Action**: REMOVE
- **Metrics**: R@1, R@5, R@10, Accuracy

</div>