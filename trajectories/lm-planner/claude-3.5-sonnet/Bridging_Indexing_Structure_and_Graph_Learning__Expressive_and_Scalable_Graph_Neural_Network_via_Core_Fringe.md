<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Bridging_Indexing_Structure_and_Graph_Learning__Expressive_and_Scalable_Graph_Neural_Network_via_Core_Fringe

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I notice that while there are some ablation studies mentioned, there are two critical components of the CFGNN method that warrant deeper investigation through ablation studies:

1. The Core-Fringe Structure Construction:
The paper uses Hub Labeling (HL) technique to construct the core-fringe structure, which is fundamental to the method's performance. However, there's no ablation study comparing this choice against other potential methods for identifying core nodes and constructing the structure. This is particularly important since the core-fringe structure is central to achieving both expressivity and scalability.

2. The Two-Stage Message Passing:
The paper introduces a novel two-stage message passing approach (Fringe→Core followed by Core→Fringe), but doesn't investigate how crucial this bidirectional flow is compared to alternative message passing schemes. Understanding the impact of this design choice would provide valuable insights into the method's effectiveness.

Looking at the metrics used in the paper, they vary by dataset but include MAE, Accuracy, AUROC, Average Precision, and F1 score. These should be maintained in the ablation studies for consistency.

I'll suggest these two missing ablation studies in order of importance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Core-Fringe Construction Ablation
- **Ablated Part**: Hub Labeling method for core-fringe structure construction
- **Action**: REPLACE
- **Replacement**: 
  - Degree-based core selection
  - PageRank-based core selection
  - Random core selection
- **Metrics**: MAE, Accuracy, AUROC, F1 score

### Message Flow Direction Ablation
- **Ablated Part**: Two-stage message passing (Fringe→Core followed by Core→Fringe)
- **Action**: REPLACE
- **Replacement**: 
  - Only Fringe→Core
  - Only Core→Fringe
  - Parallel bidirectional
- **Metrics**: MAE, Accuracy, AUROC, F1 score

</div>