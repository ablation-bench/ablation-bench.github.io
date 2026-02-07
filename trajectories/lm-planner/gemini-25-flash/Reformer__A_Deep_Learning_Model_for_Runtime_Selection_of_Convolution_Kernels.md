<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Reformer__A_Deep_Learning_Model_for_Runtime_Selection_of_Convolution_Kernels

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Reformer: A Deep Learning Model for Runtime Selection of Convolution Kernels" proposes a novel model, Reformer, built upon the Γ-block, for selecting optimal GPU kernels on the CPU. The key contributions include the Γ-block architecture (a lighter alternative to the Transformer block for CPU inference), the Reformer model itself (stacking Γ-blocks), and a novel method for assigning training probabilities based on kernel runtimes (ratio-preserving probability).

The paper includes several comparisons:
1.  **Γ-block vs. Transformer block:** Evaluated on text classification tasks (IMDB, Reuters) to show comparable accuracy with faster training and inference times on CPU (Table 1). This justifies the Γ-block design.
2.  **Reformer vs. MIOpen heuristics:** Evaluated on convolution kernel selection, demonstrating significant speedup (Figure 5, Figure 6). This shows the practical effectiveness of the Reformer model.
3.  **Reformer vs. ResNet18:** Compared on kernel selection accuracy, showing Reformer achieves comparable accuracy despite being much smaller.

While these comparisons are valuable, the paper lacks ablation studies that isolate the impact of specific novel components *within* the Reformer model for the primary kernel selection task. Based on the paper's contributions and design choices, two important missing ablation studies are:

1.  **Training Target Probability Formulation:** The paper highlights its novel ratio-preserving probability assignment method for training as a key contribution, arguing it's more robust than one-hot or softmax probabilities (Table 2). However, it does not experimentally compare the performance of the Reformer model when trained with these different probability formulations on the kernel selection task. An ablation study testing training with one-hot and softmax targets would directly demonstrate the benefit of the proposed ratio-preserving method.
2.  **Number of Γ-blocks:** The Reformer model is constructed by stacking three Γ-blocks (L=3). The paper doesn't explore how the number of stacked blocks affects performance (accuracy, speedup, inference time). Ablating the number of blocks (e.g., testing 1, 2, or 4 blocks) would help understand the model's capacity and the impact of depth on the kernel selection task.

These two ablations are crucial for attributing the Reformer's success in kernel selection to its specific training methodology and architectural depth, respectively. They directly test the impact of novel or key design choices on the main task.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Training Target Probability Ablation
- **Ablated Part**: Method for assigning optimality probabilities to kernels for training (ratio-preserving probability)
- **Action**: REPLACE
- **Replacement**: 
  - One-hot probability
  - Softmax probability
- **Metrics**: Test Accuracy, Average Speedup vs. Heuristics, CPU Inference Time

### Number of Gamma Blocks Ablation
- **Ablated Part**: Number of stacked Γ-blocks in the Reformer model
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 4
- **Metrics**: Test Accuracy, Average Speedup vs. Heuristics, CPU Inference Time

</div>