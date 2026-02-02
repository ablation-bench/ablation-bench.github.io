<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/hvpnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 ablation studies for the paper "Good Visual Guidance Makes A Better Extractor: Hierarchical Visual Prefix for Multimodal Entity and Relation Extraction". I need to identify the key components of the proposed HVPNeT method and suggest ablations, ranking them by importance.

Based on the abstract and method section, the core contributions are:
1.  Using visual features as a "pluggable visual prefix".
2.  Employing "hierarchical multi-scaled visual features" (pyramidal features).
3.  Using a "dynamic gated aggregation strategy" to combine these hierarchical features.
4.  Fusing the visual prefix at "each self-attention layer of BERT".
5.  Utilizing both global and object-level visual features.

The most important ablation is typically removing the core novel component or the entire multimodal aspect to establish a baseline. Then, ablating the specific mechanisms introduced (hierarchical features, dynamic gate, prefix fusion strategy) is crucial to understand their individual contributions.

Here is the plan for the top 5 ablations, ranked by importance:

1.  **Remove all visual features:** This establishes a text-only baseline, showing the overall gain from incorporating any visual information. This is the most fundamental ablation.
2.  **Ablate the Dynamic Gated Aggregation:** This mechanism adaptively weights the hierarchical features. Replacing it with a simpler, fixed aggregation (like simple averaging) will show if the dynamic gating is beneficial.
3.  **Ablate the Hierarchical Visual Features:** The paper highlights using pyramidal features. Ablating this by using only single-scale features (e.g., from the last layer of the visual backbone) will demonstrate the value of the hierarchical approach.
4.  **Ablate Object-level Visual Features:** The paper uses both global and object features. Removing the object features will show their specific contribution compared to just using global image information.
5.  **Ablate the Layer-wise Fusion Strategy:** The paper fuses the visual prefix at *each* BERT layer. Ablating this by fusing only at a single layer (e.g., the final layer) will show if the layer-wise fusion is necessary or if a simpler fusion strategy is sufficient.

The paper evaluates on MNER and MRE tasks. The standard metrics for these tasks are Precision, Recall, and F1-score. The abstract mentions "effectiveness" and "state-of-the-art performance", implying these standard metrics are used. I will use "F1-score (NER)" and "F1-score (RE)" as the primary metrics, as F1 is commonly used to summarize performance for these tasks.

I will now format these into the required JSONL structure.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Text-only Baseline
- **Ablated Part**: All visual features and fusion mechanisms
- **Action**: REMOVE
- **Metrics**: F1-score (NER), F1-score (RE)

### Fixed Aggregation
- **Ablated Part**: Dynamic Gated Aggregation
- **Action**: REPLACE
- **Replacement**: 
  - Simple average pooling of hierarchical features
- **Metrics**: F1-score (NER), F1-score (RE)

### Single-scale Visual Features
- **Ablated Part**: Hierarchical Pyramidal Visual Features
- **Action**: REPLACE
- **Replacement**: 
  - Use features from the final visual backbone layer
- **Metrics**: F1-score (NER), F1-score (RE)

### No Object Features
- **Ablated Part**: Object-level visual features
- **Action**: REMOVE
- **Metrics**: F1-score (NER), F1-score (RE)

### Last Layer Fusion
- **Ablated Part**: Fusion at each Transformer layer
- **Action**: REPLACE
- **Replacement**: 
  - Fuse visual prefix only at the final layer
- **Metrics**: F1-score (NER), F1-score (RE)

</div>