<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/3DMolFormer__A_Dual_channel_Framework_for_Structure_based_Drug_Discovery

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "3DMolFormer: A Dual-channel Framework for Structure-based Drug Discovery" proposes a novel transformer-based framework capable of handling both protein-ligand docking and pocket-aware 3D drug design. The core innovations include a parallel sequence format for discrete tokens and continuous numerical values representing 3D complexes, a dual-channel transformer architecture, large-scale pre-training with a composite loss, and task-specific fine-tuning strategies, including leveraging docking functionality within drug design.

The paper includes several ablation studies:
1.  **Pre-training (w/o PT):** Demonstrates the importance of large-scale pre-training for docking performance.
2.  **Data Augmentation (w/o DA):** Shows the benefit of data augmentation during docking fine-tuning.
3.  **Model Scaling:** Investigates different model sizes based on pre-training loss.
4.  **Alpha Coefficient in Composite Loss:** Shows the insensitivity of pre-training loss balance to the `alpha` parameter.
5.  **RL Fine-tuning (w/o RL):** Highlights the necessity of RL fine-tuning for drug design performance.

While these ablations cover important aspects like pre-training, data augmentation, model size, and the necessity of RL, they do not fully explore all critical components and design choices. Based on the paper's emphasis on the dual-channel nature, the specific composite loss function, and the method of leveraging task duality, I identify two important missing ablation studies:

1.  **Ablating the use of docking-tuned weights for 3D coordinate generation in drug design:** The paper explicitly states that during RL fine-tuning for drug design, the generation of 3D coordinates uses weights from the model fine-tuned for docking, while token generation uses the RL-tuned weights. This is presented as a way to leverage the duality. An ablation study comparing this approach to using the RL-tuned weights (or even the pre-trained weights) for 3D generation would directly assess the benefit of this specific mechanism for transferring knowledge from the docking task to the drug design task's 3D output quality.
2.  **Ablating the components of the pre-training composite loss:** The pre-training uses a composite loss combining cross-entropy (CE) for the token sequence and mean squared error (MSE) for the numerical sequence. While the paper ablates the balancing coefficient `alpha`, it doesn't show the effect of training with *only* one type of loss where applicable. Ablating the CE loss component (training only with MSE where coordinates exist) and the MSE loss component (training only with CE for tokens) would reveal the individual contributions of learning discrete structure patterns versus continuous 3D coordinate patterns during the crucial pre-training phase for the dual-channel model. This is fundamental to understanding how the model learns from the parallel sequence format.

These two ablations are important because they target core, novel aspects of the 3DMolFormer framework: the specific way duality is leveraged in fine-tuning and the learning objective for the unique dual-channel representation during pre-training. They would provide deeper insight into *why* the proposed method works well.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Docking Weights for Design 3D
- **Ablated Part**: Using docking-fine-tuned weights for generating 3D coordinates during RL drug design fine-tuning
- **Action**: REPLACE
- **Replacement**: 
  - Use RL-fine-tuned weights for 3D generation
  - Use pre-trained weights for 3D generation
- **Metrics**: Vina Score, Vina Dock, QED, SA, Success Rate, Mean Delta Score, Mean Clash Score, Median Strain Energy

### Ablate Pre-training Loss Components
- **Ablated Part**: Composite loss function (CE + MSE) during pre-training
- **Action**: REPLACE
- **Replacement**: 
  - Train with only CE loss (ignoring MSE)
  - Train with only MSE loss (ignoring CE)
- **Metrics**: Pre-training Loss (CE), Pre-training Loss (MSE), %<1.0A, %<2.0A, %<3.0A, %<5.0A, Avg. RMSD, Vina Dock, Success Rate

</div>