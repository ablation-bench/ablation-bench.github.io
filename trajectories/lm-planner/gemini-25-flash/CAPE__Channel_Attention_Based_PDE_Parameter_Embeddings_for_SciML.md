<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/CAPE__Channel_Attention_Based_PDE_Parameter_Embeddings_for_SciML

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "CAPE: Channel-Attention-Based PDE Parameter Embeddings for SciML" proposes two main contributions: the CAPE module for parameter embedding and a curriculum learning strategy. The experiments section includes comparisons against several baselines (Base, PINO, Conditional, prev. 2-steps) and an ablation study on the curriculum learning strategy (Table 3). It also mentions an ablation study on the CAPE structure in the appendix (Table 9), although the details are not provided in the main text.

Based on the method description, the CAPE module takes the current state and PDE parameters to predict intermediate future states, which are then fed to a base network. The training involves a combined loss function including the standard nRMSE for the final prediction and an auxiliary nRMSE loss (`L_cape`) that regularizes the CAPE module's intermediate output against the true future states. The number of intermediate steps predicted by CAPE (`ell`) is also a design parameter, stated as `ell=1` for most experiments.

Considering the existing ablations (curriculum strategy, and presumably internal CAPE structure), two important aspects of the CAPE module and its training are not explicitly ablated in the main text:

1.  **The impact of the auxiliary CAPE loss (`L_cape`):** This loss term explicitly forces the CAPE module's output to resemble the true future state. It's crucial to understand if this explicit regularization is necessary for the overall performance or if the base network can learn to utilize the CAPE output effectively even without this direct supervision on the intermediate prediction. Ablating this loss (setting its weight to zero) or varying its weight would clarify its contribution.
2.  **The number of intermediate steps (`ell`) predicted by CAPE:** The method is formulated to potentially predict a sequence of `ell` intermediate steps (Eq. 11), but the experiments primarily use `ell=1`. Investigating whether providing a longer sequence of intermediate future states (`ell > 1`) to the base network improves performance or generalization would be valuable.

These two ablations are important because they test core design choices related to *what* the CAPE module is trained to output and *how much* information it provides to the base network, beyond just its internal structure. They are not covered by the curriculum learning ablation, and while the appendix might cover CAPE structure, it's less likely to cover the auxiliary loss weight or the number of steps `ell` as distinct ablations from the core structural components.

I will prioritize the auxiliary loss ablation slightly higher as it directly tests the necessity of the specific training objective applied to the CAPE module's output.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Auxiliary CAPE Loss Impact
- **Ablated Part**: Auxiliary loss function (L_cape) for the CAPE module output
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 1.0
- **Metrics**: nRMSE

### Number of CAPE Intermediate Steps
- **Ablated Part**: Number of future intermediate time steps (ell) predicted by the CAPE module
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 3
- **Metrics**: nRMSE

</div>