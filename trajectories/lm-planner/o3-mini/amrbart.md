<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/amrbart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

In our proposed ablation studies, we aim to isolate the contributions of the major components of the method. First, we assess the overall benefit of the unified pre-training framework that bridges the gap between text and graph inputs by removing it and reverting to standard, separate pre-training. Next, as silver data are highlighted as useful for pre-training, we propose to remove their contribution to quantify their impact. We then target the two graph denoising strategies: the node/edge level denoising that focuses on local structural information, and the sub-graph level denoising that reinforces graph-level recovery. Finally, we investigate the effectiveness of the dynamic masking rate by replacing it with fixed (static) masking values. For all experiments, we plan to report AMR parsing performance via Smatch and AMR-to-text generation quality via BLEU.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Unified Pre-training Framework
- **Ablated Part**: The unified pre-training framework that integrates text and graph sequences via joint denoising tasks (e.g., text augmented graph denoising and vice versa)
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU

### Ablation 2: Silver Data Contribution
- **Ablated Part**: The incorporation of silver (automatically generated) data in the pre-training phase
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU

### Ablation 3: Node/Edge Level Denoising
- **Ablated Part**: The node/edge level denoising strategy applied on AMR graphs to mask local nodes and edges
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU

### Ablation 4: Sub-Graph Level Denoising
- **Ablated Part**: The sub-graph level denoising strategy that removes and replaces sub-graphs to enforce graph-level recovery
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU

### Ablation 5: Dynamic Masking Rate
- **Ablated Part**: The dynamic masking rate schedule used during joint pre-training tasks
- **Action**: REPLACE
- **Replacement**: 
  - 0.1
  - 0.2
  - 0.3
- **Metrics**: Smatch, BLEU

</div>