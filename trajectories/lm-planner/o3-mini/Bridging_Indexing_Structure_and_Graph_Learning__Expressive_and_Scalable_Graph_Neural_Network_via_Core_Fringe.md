<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Bridging_Indexing_Structure_and_Graph_Learning__Expressive_and_Scalable_Graph_Neural_Network_via_Core_Fringe

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One crucial missing ablation is to investigate the sensitivity of CFGNN’s performance to the core selection mechanism. In the current method, core nodes are selected using hub labeling, but there is no comparison against other selection strategies (such as using node degrees, PageRank scores, or even random choices). Such an ablation would reveal whether the expressivity and scalability benefits are specifically tied to the hub labeling technique or if similar benefits can be achieved using alternative approaches. This experiment is important because the selection of cores directly influences the construction of the core-fringe structure and therefore the overall message propagation and model performance.

Another important ablation that is missing is an evaluation of the contribution of the two-stage propagation process (the collection of messages from fringes to cores followed by the distribution from cores back to fringes). While the paper validates the effectiveness of the dual-stage design as a whole, it does not assess the impact of each individual stage. Removing or simplifying the distribution stage (or alternatively, testing a single-stage variant) could show how much each stage contributes to the expressivity and scalability, and whether both stages are strictly necessary.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Core Selection Strategy Ablation
- **Ablated Part**: the hub labeling-based core selection mechanism used to construct the core-fringe structure
- **Action**: REPLACE
- **Replacement**: 
  - degree-based selection
  - pagerank-based selection
  - random selection
- **Metrics**: MAE, Accuracy, AUROC, F1 score

### Propagation Stage Ablation
- **Ablated Part**: the two-stage message passing mechanism (collect and distribute stages)
- **Action**: REMOVE
- **Metrics**: MAE, Accuracy, AUROC, F1 score

</div>