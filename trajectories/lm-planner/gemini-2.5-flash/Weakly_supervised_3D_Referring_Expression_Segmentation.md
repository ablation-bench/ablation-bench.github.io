<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Weakly_supervised_3D_Referring_Expression_Segmentation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Weakly-supervised 3D Referring Expression Segmentation" introduces the Multi-Expert Network (MEN) framework, consisting of the Multi-Expert Mining (MEM) module and the Multi-Expert Aggregation (MEA) module, for weakly supervised 3D Referring Expression Segmentation. The MEM module utilizes three experts (full-context, attribute, and category) to extract semantic cues, and the MEA module aggregates their outputs using a specific conflation strategy.

The paper includes several ablation studies:
1.  Ablations on MEM: Testing combinations of the three experts (Table 2).
2.  Ablations on MEA: Comparing the proposed conflation strategy with Max and Average aggregation (Table 3).
3.  Ablations on image sources for experts (Table 4).
4.  Ablations on the choice of VL encoder (Long-CLIP vs. others) in the full-context expert (Table 5).
5.  Ablations on the text input (Tshort) for the attribute expert (Table 6, Table 12).
6.  Ablations on hyperparameters like Top-K frames (Table 9) and number of rendering views (Table 10).
7.  Ablations on the 3D instance segmentation backbone (Table 11).
8.  Ablations on the zero-target detection head (in the appendix for 3D-GRES) (Tables 13, 14).

While the existing ablations cover many aspects, two potentially important areas are not fully explored:

1.  **The specific mechanism of the Category Expert's text matching:** The category expert uses a learned MLP classifier on the textual full-context feature to predict category scores (Tcls), which are then matched with the instance segmentation model's predicted class scores (Pcls). An ablation comparing this learned approach to a simpler, potentially zero-shot method (e.g., using CLIP's inherent text-to-category similarity) would clarify the contribution of training this specific classifier.
2.  **The nature of the MEA aggregation:** The paper highlights the theoretical justification for the chosen conflation method (product of probabilities normalized). However, it only compares it to simple Max and Average. An ablation comparing this fixed mathematical aggregation to a learned aggregation function (e.g., a small neural network taking the expert distributions as input) would demonstrate whether the specific fixed formula is empirically superior or if a data-driven approach could yield better results.

Based on this analysis, I propose the following two missing ablation studies, focusing on the core 3D-RES task as presented in the main paper. I will use the comprehensive set of metrics reported in the main results and the MEM ablation (Table 1 and Table 2).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on Category Expert Text Matching
- **Ablated Part**: Learned MLP text classifier in the Category Expert
- **Action**: REPLACE
- **Replacement**: 
  - CLIP zero-shot similarity between text and category names
- **Metrics**: mIoU, R@1, IoU@0.25, R@1, IoU@0.5, R@3, IoU@0.25, R@3, IoU@0.5

### Ablation on MEA Aggregation Strategy
- **Ablated Part**: Fixed mathematical conflation formula in the MEA module
- **Action**: REPLACE
- **Replacement**: 
  - Learned aggregation module (e.g., MLP)
- **Metrics**: mIoU, R@1, IoU@0.25, R@1, IoU@0.5, R@3, IoU@0.25, R@3, IoU@0.5

</div>