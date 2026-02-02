<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/amrbart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel approach for AMR parsing and generation by pre-training a BART model on AMR graphs in addition to text. The core idea is to improve the model's understanding of graph structures, which are central to AMR. The method introduces specific graph auto-encoding strategies (node/edge denoising, sub-graph denoising) and a unified framework for joint text and graph pre-training, involving several auxiliary tasks.

To design ablation studies, I focused on the key novel components introduced by the authors:
1.  **Graph Pre-training:** The most significant contribution is adding graph pre-training. Ablating all graph-related pre-training tasks (both standard graph denoising and joint text-graph tasks) will directly measure the overall impact of their proposed pre-training strategy compared to a standard text-only pre-trained model fine-tuned on the task.
2.  **Joint Text-Graph Pre-training:** The unified framework and the joint tasks are designed to bridge the gap between text and graph modalities and between pre-training and fine-tuning. Ablating these joint tasks while keeping standard text and graph pre-training separate would assess the value of this specific integration strategy.
3.  **Graph Denoising Strategies:** The paper proposes two distinct graph denoising methods: node/edge level and sub-graph level. Ablating one of these (specifically the sub-graph level, as it's a higher-level structural task) can reveal its individual contribution.
4.  **Dynamic Masking:** A dynamic masking rate is used for some joint tasks. Testing a static masking rate instead will evaluate if this specific training schedule is beneficial.
5.  **Silver Data:** The paper mentions and evaluates the use of silver data. While the paper's experiments already show results with and without silver data, explicitly defining this as an ablation confirms its importance and allows for direct comparison within the ablation framework.

Based on these points, I've selected the top 5 most important ablations, prioritizing those that test the core novelties (graph pre-training, joint training) and specific design choices (denoising strategy, masking rate, data source). The metrics used are those reported in the paper for evaluating AMR parsing (Smatch) and AMR-to-text generation (BLEU, METEOR, chrF++).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Graph Pre-training
- **Ablated Part**: All graph-specific pre-training tasks (standard graph denoising and joint text-graph tasks)
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR, chrF++

### No Joint Text-Graph Pre-training
- **Ablated Part**: All joint pre-training tasks combining text and graph inputs/outputs
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR, chrF++

### No Sub-graph Denoising
- **Ablated Part**: Sub-graph level denoising strategy during graph pre-training
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR, chrF++

### Static Masking Rate
- **Ablated Part**: Dynamic masking rate for joint text-graph pre-training tasks
- **Action**: REPLACE
- **Replacement**: 
  - 0.15
  - 0.35
- **Metrics**: Smatch, BLEU, METEOR, chrF++

### No Silver Data
- **Ablated Part**: Use of silver data during pre-training
- **Action**: REMOVE
- **Metrics**: Smatch, BLEU, METEOR, chrF++

</div>