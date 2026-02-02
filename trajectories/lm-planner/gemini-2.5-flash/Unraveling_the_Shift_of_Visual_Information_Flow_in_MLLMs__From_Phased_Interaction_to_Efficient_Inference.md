<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Unraveling_the_Shift_of_Visual_Information_Flow_in_MLLMs__From_Phased_Interaction_to_Efficient_Inference

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Unraveling the Shift of Visual Information Flow in MLLMs: From Phased Interaction to Efficient Inference" proposes Hierarchical Modality-Aware Pruning (HiMAP), an inference acceleration method for MLLMs. The method is based on the paper's core finding that visual information flow shifts across layers: image-to-instruction interaction is dominant in shallow layers, while image-to-image interaction is dominant in deeper layers. HiMAP leverages this by applying a two-stage pruning process: pruning image tokens in shallow layers based on their attention to instruction tokens (ϕsh), and pruning remaining image tokens in deeper layers based on their attention to other image tokens (ϕdp).

The paper presents several experiments:
1.  Analysis of modality contributions to predictions, showing image tokens have low overall impact.
2.  Analysis of intra-visual vs. visual-textual information flow across layers, validating the shift hypothesis.
3.  Information flow perturbation experiments to further validate the hypothesis about shallow injection and deeper aggregation.
4.  Evaluation of the full HiMAP method against baseline and FastV, demonstrating significant FLOPs reduction with minimal performance loss across various tasks and models.

While the paper effectively validates its underlying hypothesis and shows the overall effectiveness of HiMAP, it lacks detailed ablation studies on the specific design choices of HiMAP itself. The main components of HiMAP are its hierarchical (two-stage) pruning structure and its modality-aware pruning criteria. Ablating these components would provide crucial insights into *why* HiMAP performs well and confirm that its design, derived from the information flow analysis, is indeed optimal.

Based on this analysis, two important missing ablation studies are identified:

1.  **HiMAP Stage Contribution:** This ablation would investigate the contribution of each stage (shallow pruning and deep pruning) of the hierarchical structure. By removing one stage at a time and comparing the performance and efficiency against the full two-stage HiMAP, the study could demonstrate whether both stages are necessary and how much each contributes to the overall result.
2.  **Pruning Criterion Ablation:** This ablation would test the importance of using modality-aware criteria (ϕsh for shallow, ϕdp for deep). By replacing these specific criteria with alternatives (e.g., swapping them or using a generic criterion), the study could validate whether the criteria derived from the information flow analysis are superior to other choices for effective pruning.

These two ablations are crucial for attributing HiMAP's success to its specific design principles and validating the practical utility of the paper's findings about visual information flow. They are ranked equally important as they test the two core aspects of the HiMAP method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### HiMAP Stage Contribution
- **Ablated Part**: The two-stage hierarchical pruning structure (shallow and deep stages).
- **Action**: REMOVE
- **Metrics**: TFLOPs, Ratio, Sci-VQA (Accuracy), A-OKVQA (Accuracy), POPE (Accuracy), Nocaps (CIDEr), Flickr30k (CIDEr), LLaVA-Bench (GPT-4o), MM-Vet (GPT-4o)

### Pruning Criterion Ablation
- **Ablated Part**: The specific modality-aware pruning criteria (phi_sh and phi_dp).
- **Action**: REPLACE
- **Replacement**: 
  - Swap shallow/deep criteria (phi_dp at K1, phi_sh at K2)
  - Use uniform criterion (sum of attention to all tokens at K1 and K2)
- **Metrics**: TFLOPs, Ratio, Sci-VQA (Accuracy), A-OKVQA (Accuracy), POPE (Accuracy), Nocaps (CIDEr), Flickr30k (CIDEr), LLaVA-Bench (GPT-4o), MM-Vet (GPT-4o)

</div>