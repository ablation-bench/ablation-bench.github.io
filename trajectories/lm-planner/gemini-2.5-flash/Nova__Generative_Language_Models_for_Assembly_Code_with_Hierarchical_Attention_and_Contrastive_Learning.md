<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Nova__Generative_Language_Models_for_Assembly_Code_with_Hierarchical_Attention_and_Contrastive_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Nova: Generative Language Models for Assembly Code with Hierarchical Attention and Contrastive Learning" proposes Nova, a generative LLM for assembly code incorporating two main novelties: Hierarchical Self-Attention (HA) and Contrastive Learning (CL). The CL objective is further composed of Functionality Contrastive Learning (FCL) and Optimization Contrastive Learning (OCL).

The paper includes several ablation studies to evaluate the contribution of these components. Specifically, Tables 5 and 11 (for Binary Code Decompilation - BCD) and Tables 12-15 (for Binary Code Similarity Detection - BCSD) compare the full Nova model with variants where:
1.  Both CL and HA are removed (Nova<sup>−</sup>CL−HA, which is the baseline LM + training on assembly corpus).
2.  HA is removed, but CL (both FCL and OCL) is kept (Nova<sup>−</sup>HA).
3.  HA and FCL are removed, keeping only OCL (Nova<sup>−</sup>F CL−HA, only in Table 11).
4.  HA and OCL are removed, keeping only FCL (Nova<sup>−</sup>OCL−HA, only in Table 11).

These existing ablations effectively demonstrate:
-   The combined benefit of CL and HA over the baseline (Nova vs Nova<sup>−</sup>CL−HA).
-   The benefit of HA when both FCL and OCL are present (Nova vs Nova<sup>−</sup>HA).
-   The individual benefits of FCL and OCL when HA is *absent* (Nova<sup>−</sup>HA vs Nova<sup>−</sup>F CL−HA and Nova<sup>−</sup>HA vs Nova<sup>−</sup>OCL−HA, and Nova<sup>−</sup>F CL−HA vs Nova<sup>−</sup>CL−HA, Nova<sup>−</sup>OCL−HA vs Nova<sup>−</sup>CL−HA).

However, the existing studies do not fully explore the individual contributions of FCL and OCL when the Hierarchical Attention mechanism *is* present. It is important to understand if each contrastive learning objective still provides a significant benefit in the context of the full Nova architecture, which includes HA. HA might already capture some of the semantic information that FCL and OCL aim to encode, potentially reducing their individual impact when combined.

Therefore, two important missing ablation studies are:
1.  Evaluating the impact of removing the Functionality Contrastive Learning objective while keeping the Optimization Contrastive Learning and Hierarchical Attention.
2.  Evaluating the impact of removing the Optimization Contrastive Learning objective while keeping the Functionality Contrastive Learning and Hierarchical Attention.

These ablations would isolate the contribution of each contrastive learning component within the complete Nova framework (LM + HA + CL), providing a more granular understanding of how each piece contributes to the final performance gains. The metrics used in the paper for evaluation (Pass@1, Pass@10 for BCD, and Recall@1 for BCSD) should be reported for these experiments.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Nova-noFCL-wHA
- **Ablated Part**: Functionality Contrastive Learning objective
- **Action**: REMOVE
- **Metrics**: Pass@1, Pass@10, Recall@1

### Nova-noOCL-wHA
- **Ablated Part**: Optimization Contrastive Learning objective
- **Action**: REMOVE
- **Metrics**: Pass@1, Pass@10, Recall@1

</div>