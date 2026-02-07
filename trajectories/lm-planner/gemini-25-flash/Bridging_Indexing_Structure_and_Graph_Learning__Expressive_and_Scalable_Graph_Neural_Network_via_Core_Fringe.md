<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Bridging_Indexing_Structure_and_Graph_Learning__Expressive_and_Scalable_Graph_Neural_Network_via_Core_Fringe

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces CFGNN, a novel Graph Neural Network that leverages a Core-Fringe structure inspired by Hub Labeling (HL) to achieve both expressivity and scalability. The method involves constructing this structure using HL and then performing a two-stage message passing process (Fringe to Core, then Core to Fringe). The paper presents empirical results showing CFGNN's performance and scalability compared to baselines and mentions ablation studies in the appendix (A.10-A.11) to confirm the benefits of the core-fringe structure.

Based on the abstract and method description, the core components are:
1.  The Core-Fringe structure itself.
2.  The specific method used to construct this structure (Hub Labeling).
3.  The two-stage message passing mechanism.

While the paper mentions ablations confirming the benefits of the core-fringe structure, it's crucial to understand *why* the specific HL-based construction is beneficial compared to other potential ways of defining a core-fringe structure. The paper highlights HL's properties like 2-hop cover, but it's not clear from the abstract or main sections if alternative partitioning methods were explored as ablations.

Therefore, a key missing ablation is comparing the HL-based core-fringe construction against alternative, simpler methods for defining cores and fringes (e.g., based on node degree or clustering). This would directly test if the advantage comes specifically from the properties induced by HL or merely from the general concept of partitioning the graph into cores and fringes. This is ranked as the most important missing ablation.

Secondly, the properties of the HL-based structure, such as the total label size or average fringe size, are results of the HL construction process (which often uses greedy heuristics aiming to minimize size). Varying these properties by using different HL parameters or heuristics could reveal the trade-off between the structure's size/density and the model's performance and computational cost. This ablation would provide insight into how the specific characteristics of the HL-generated structure impact the CFGNN's expressivity and scalability, which are the main claims of the paper. This is ranked as the second most important missing ablation.

These two ablations directly investigate the impact of the core design choice (using HL) and the resulting structure's properties, which are fundamental to the CFGNN method. The metrics used in the paper's evaluation tables (MAE, Accuracy, AUROC, Avg. Precision, F1 score, AP) should be used to evaluate the performance impact, and for the second ablation, metrics related to structure size and computational cost should also be reported.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Alternative Core/Fringe Definition
- **Ablated Part**: Method for constructing the Core-Fringe structure
- **Action**: REPLACE
- **Replacement**: 
  - Core/Fringe based on node degree (high-degree nodes as cores)
  - Core/Fringe based on graph clustering (e.g., using k-means on node features)
- **Metrics**: MAE, Accuracy, AUROC, Avg. Precision, F1 score, AP

### Core/Fringe Size Impact
- **Ablated Part**: Properties of the Core-Fringe structure (e.g., average fringe size, number of cores) as determined by the Hub Labeling construction
- **Action**: REPLACE
- **Replacement**: 
  - HL construction targeting smaller structure size
  - HL construction targeting larger structure size
- **Metrics**: MAE, Accuracy, AUROC, Avg. Precision, F1 score, AP, Total Label Size, Average Fringe Size, Memory Usage, Runtime

</div>