<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Annotation_Efficient_Language_Model_Alignment_via_Diverse_and_Representative_Response_Texts

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes AEPO (Annotation-Efficient Preference Optimization), a method for efficiently selecting a subset of responses to annotate for preference optimization. The key components are:

1. A subsampling strategy that maximizes both diversity and representativeness of selected responses through an objective function combining:
   - frep: Representativeness objective measuring closeness to all candidate responses
   - fdiv: Diversity objective measuring distinctness between selected responses
   - λ: Hyperparameter controlling the trade-off between diversity and representativeness

2. The paper includes ablations on:
- Different λ values (0.0, 0.5, 1.0, 2.0)
- Different loss functions (DPO, hinge loss, KTO loss)
- Different model sizes and architectures
- Different datasets
- Different LoRA hyperparameters

However, I notice two important missing ablations:

1. The choice of embedding model for computing response similarity is a critical component but not ablated. The paper uses all-mpnet-base-v2 without exploring alternatives.

2. The paper uses cosine distance as the dissimilarity function d(y1,y2) without exploring other distance metrics that could affect the diversity and representativeness objectives.

These components directly impact how responses are selected and warrant investigation through ablation studies.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Embedding Model Ablation
- **Ablated Part**: Sentence embedding model used for computing response similarity
- **Action**: REPLACE
- **Replacement**: 
  - all-mpnet-base-v2
  - BERT-base
  - RoBERTa-base
  - SimCSE
- **Metrics**: OASST score, Eurus score, Win rate vs SFT, Diversity metrics (distinct-n), Representativeness score

### Distance Metric Ablation
- **Ablated Part**: Distance function for computing response dissimilarity
- **Action**: REPLACE
- **Replacement**: 
  - cosine distance
  - euclidean distance
  - manhattan distance
  - jensen-shannon divergence
- **Metrics**: OASST score, Eurus score, Win rate vs SFT, Diversity metrics (distinct-n), Representativeness score

</div>