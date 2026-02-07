<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/SPTNet__An_Efficient_Alternative_Framework_for_Generalized_Category_Discovery_with_Spatial_Prompt_Tuning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user requested up to two missing ablation studies for the paper "SPTNet: An Efficient Alternative Framework for Generalized Category Discovery with Spatial Prompt Tuning". I need to identify key components of the SPTNet method and suggest ablation experiments that were not performed in the paper but would be valuable for understanding the method's performance.

SPTNet's main contributions are:
1.  A two-stage iterative learning framework alternating between optimizing model parameters (F&H) and data parameters (prompts).
2.  Spatial Prompt Tuning (SPT), which includes distinct patch-wise prompts and a global prompt, applied at the input pixel space.

The paper already includes several ablation studies:
-   Comparison of different prompt types (VPT, Global, SPT, Shared Spatial) and the alternative training strategy (Table 4).
-   Comparison of different training strategies (end-to-end, data first, model first, alternative) (Table 5).
-   Effects of hyperparameters (alternating frequency k, spatial prompt size m, global prompt size m+) (Figure 3, Appendix D).
-   Performance of variants (SPTNet-P, SPTNet-S) (Appendix C).

Based on the existing ablations, I identified two important missing studies:

1.  **Contribution of Global Prompt within the Alternating Framework:** Table 4 shows the effect of adding a Global prompt to SimGCD *without* the alternating strategy (row 3 vs 1). It also shows the effect of adding Global prompts to SPTNet-S (Shared Spatial + Alter) to get SPTNet (Distinct Spatial + Global + Alter) (row 7 vs 8). However, it does not show the effect of using *only* the Global prompt *with* the alternating strategy. This ablation (SimGCD + Alternating Strategy + Global Prompt) would isolate the contribution of the Global prompt within the proposed alternating framework, allowing for a clearer comparison against using only spatial prompts (SPTNet-P) or the combination (SPTNet). This is crucial for understanding the individual roles of the spatial and global prompts when trained with the proposed alternating method.

2.  **Impact of Spatial Prompt Location:** The paper proposes Spatial Prompt Tuning (SPT) which attaches prompts to the *border* of each image patch (Figure 2). The motivation is partly based on the idea that object parts are important for GCD. While the attention maps (Figure 5, Appendix K) suggest SPT helps focus attention on objects, the specific design choice of placing prompts on the *border* of patches is not ablated. An experiment exploring placing prompts in the *inner* region of patches, rather than the border, would directly test whether the specific border placement is important or if any spatial perturbation within the patch is sufficient, and whether focusing prompts away from borders might better target "object parts" often located centrally within patches. This tests a specific design choice within the novel SPT method.

These two ablations are important because they further dissect the contributions of the core components (alternating strategy, global prompt, spatial prompt design) of the SPTNet method, which are not fully isolated in the current ablation studies. I will rank the first one (isolating Global prompt contribution within the framework) as slightly more important as it concerns the interaction of the main framework components. The metrics used in the paper are consistently "All", "Old", and "New" accuracy, so I will use these.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### SPTNet (Alter + Global)
- **Ablated Part**: Spatial prompts (distinct patch-wise prompts)
- **Action**: REMOVE
- **Metrics**: All Accuracy, Old Accuracy, New Accuracy

### SPT (Inner Patch Prompts)
- **Ablated Part**: Location of spatial prompts within the patch
- **Action**: REPLACE
- **Replacement**: 
  - Prompts applied to the inner region of each patch
- **Metrics**: All Accuracy, Old Accuracy, New Accuracy

</div>