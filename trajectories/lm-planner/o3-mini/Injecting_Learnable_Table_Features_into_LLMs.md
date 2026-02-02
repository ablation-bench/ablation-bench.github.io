<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Injecting_Learnable_Table_Features_into_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already demonstrates significant improvements by injecting table structure information through a hypergraph encoder and shows benefits over pure text modalities. However, two important aspects remain unassessed. First, the method uses an MLP-based alignment layer to transform the learnable hypergraph-based table features into the LLM’s semantic space. It is not clear how critical this specific alignment module is for achieving high performance. A missing ablation study would remove this alignment layer to directly inject raw hypergraph features into the LLM, helping to isolate and assess the contribution of the alignment transformation on downstream QA metrics and robustness (including permutation invariance). Second, the hypergraph encoder employs set transformer–based multiset functions to aggregate node and hyperedge information. Considering the complexity of this module, a study investigating alternative aggregation methods (such as simple mean pooling, max pooling, or sum pooling) is warranted. This experiment would reveal the sensitivity of the overall framework performance to the choice of aggregation function, as measured by accuracy metrics on StructQA, HiTab, WikiTQ, WikiSQL, and BLEU on FetaQA.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Alignment Module Ablation
- **Ablated Part**: MLP-based alignment layer that transforms hypergraph table features into the LLM’s semantic space
- **Action**: REMOVE
- **Metrics**: StructQA Accuracy, HiTab Accuracy, WikiTQ Accuracy, WikiSQL Execution Accuracy, FetaQA BLEU, Permutation Robustness

### Aggregation Function Ablation
- **Ablated Part**: Set Transformer-based multiset function in the hypergraph encoder
- **Action**: REPLACE
- **Replacement**: 
  - mean pooling
  - max pooling
  - sum pooling
- **Metrics**: StructQA Accuracy, HiTab Accuracy, WikiTQ Accuracy, WikiSQL Execution Accuracy, FetaQA BLEU

</div>