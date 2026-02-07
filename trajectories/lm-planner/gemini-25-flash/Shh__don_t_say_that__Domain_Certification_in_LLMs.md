<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Shh__don_t_say_that__Domain_Certification_in_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Shh, don't say that! Domain Certification in LLMs" introduces VALID, a method for domain certification in LLMs using rejection sampling based on the likelihood ratio between a general LLM (L) and a domain-specific guide model (G). The core idea is to reject outputs `y` from L if their likelihood under L, relative to their likelihood under G, exceeds a threshold `k` normalized by sequence length `Ny`. This is formalized as `log L(y|x) / G(y) <= k * Ny`. The method provides certificates (ϵy-AC and ϵ-DC) bounding the probability of generating out-of-domain content.

The paper includes several experiments and analyses, including evaluating likelihood ratios on ground truth data (Section 3.2), generating responses with VALID (Section 3.3), certified benchmarking (Section 3.4), studying the effect of response length (Appendix E.6), constriction ratios by likelihood (Appendix E.7), repeated sampling (T>1) (Appendix F), comparing M to G' (Appendix G.1), and studying the influence of G's size (Appendix G.2).

While these experiments provide valuable insights, two important ablation studies are missing that would further clarify the contribution of key components of the VALID method:

1.  **Ablating the Domain-Specific Guide Model (G):** The method's novelty lies in using a *domain-specific* guide model G to define the rejection criterion. The paper shows that larger G models perform better (Appendix G.2) and that the combined model M outperforms a simple domain-specific model G' (Appendix G.1). However, it does not directly ablate the role of G in the likelihood ratio. What happens if G is removed entirely (e.g., replaced by a uniform distribution) or replaced by a non-domain-specific model (like the base L model)? This ablation would demonstrate whether the domain-specific nature of G is crucial for achieving tight certificates on out-of-domain samples and for the observed separation between in-domain and out-of-domain likelihood ratios.

2.  **Ablating Length Normalization:** The paper highlights the importance of length normalization (`kN_y`) in the rejection criterion, showing that log likelihood ratios scale with sequence length (Figure 2, 5b). However, a direct ablation study showing the performance degradation (in terms of certification tightness and ID/OOD separation) when this normalization is removed is missing. This experiment would quantitatively demonstrate the necessity of length normalization for the method's effectiveness across sequences of varying lengths.

These two ablations are crucial for understanding which components are essential for VALID's performance and certification guarantees. Ablating G tests the core idea of using a domain-specific guide, while ablating length normalization tests a key technical detail for handling variable-length text.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablate Guide Model G
- **Ablated Part**: The domain-specific guide model (G) used in the likelihood ratio for rejection sampling.
- **Action**: REPLACE
- **Replacement**: 
  - Uniform distribution (constant likelihood)
  - General-purpose LLM (e.g., base L model)
- **Metrics**: eCDF of epsilon-y-ACs, epsilon-DC vs False Rejection Rate curve, Constriction Ratio (median on OOD samples)

### Ablate Length Normalization
- **Ablated Part**: The length normalization factor (Ny) applied to the rejection threshold k in the likelihood ratio criterion.
- **Action**: REMOVE
- **Metrics**: eCDF of epsilon-y-ACs (stratified by sequence length), epsilon-DC vs False Rejection Rate curve (stratified by sequence length)

</div>