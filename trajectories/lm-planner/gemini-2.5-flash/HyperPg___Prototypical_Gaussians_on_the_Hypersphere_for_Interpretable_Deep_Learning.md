<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/HyperPg___Prototypical_Gaussians_on_the_Hypersphere_for_Interpretable_Deep_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "HyperPg - Prototypical Gaussians on the Hypersphere for Interpretable Deep Learning" introduces two main novelties: 1) HyperPg, a new prototype representation modeling a Gaussian distribution over cosine similarities on a hypersphere, and 2) HyperPgNet, an architecture that leverages HyperPg to learn prototypes aligned with human concepts using pixel-level annotations and a "Right for the Right Concept" (RRC) loss.

The paper includes an ablation study on the number of prototypes per concept (Section 6.3) and explores different probability distributions for HyperPg in the appendix (Appendix A). It also implicitly evaluates the effect of the LRRC loss by comparing HyperPgNet with and without it (Table 1, Fig 6).

However, two crucial aspects are not fully ablated to isolate their contributions:

1.  **The HyperPg Prototype Representation itself:** The core technical contribution is the HyperPg formulation (probabilistic cosine similarity with learnable mean and standard deviation) compared to standard point-based prototypes. While Table 1 compares "ProtoPNet + HyperPG" to standard ProtoPNet, this comparison is confounded by the base architecture (ProtoPNet) and its original L2 similarity. A direct comparison within the HyperPgNet framework (keeping the concept alignment losses, RRC, etc.) but replacing the HyperPg module with a standard point-based cosine similarity module would isolate the benefit of the probabilistic hyperspherical representation.
2.  **The Concept Alignment Training Strategy:** HyperPgNet's other major contribution is the training approach that aligns prototypes with human-defined concepts using annotations and the LRRC loss, in contrast to traditional class-based prototype learning (like ProtoPNet). While Table 1 compares HyperPgNet to ProtoPNet, this comparison is confounded by both the prototype type and the training strategy. An ablation within HyperPgNet that removes the explicit concept alignment mechanisms (LRRC loss and concept-specific clustering/separation losses) and reverts to a more standard class-based training objective would demonstrate the impact of the concept alignment strategy itself, independent of the HyperPg representation.

These two missing ablations are critical for understanding which components contribute most to HyperPgNet's reported performance and interpretability gains. I will prioritize these two.

For the metrics, I will use those reported in the paper: Test Top-1 Accuracy, Training Epochs to Convergence (as indicated by figures like Fig 5), and the quality of Prototype Activation Maps (as shown in figures like Fig 6, 7, 8).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### HyperPg Representation Ablation
- **Ablated Part**: HyperPg prototype representation (Gaussian distribution of cosine similarities with learnable mean and standard deviation)
- **Action**: REPLACE
- **Replacement**: 
  - Standard point-based cosine similarity prototype layer (using s_cos(z|α) directly)
- **Metrics**: Test Top-1 Accuracy, Training Epochs to Convergence, Qualitative Prototype Activation Maps

### Concept Alignment Ablation
- **Ablated Part**: Concept alignment training strategy (LRRC loss and concept-based clustering/separation losses)
- **Action**: REMOVE
- **Metrics**: Test Top-1 Accuracy, Training Epochs to Convergence, Qualitative Prototype Activation Maps

</div>