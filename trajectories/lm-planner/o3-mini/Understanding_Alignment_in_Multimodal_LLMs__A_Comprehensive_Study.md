<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Understanding_Alignment_in_Multimodal_LLMs__A_Comprehensive_Study

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One major component of BDHS is how it establishes the final loss by averaging the DPO losses from (1) the externally provided non‐preferred responses and (2) the BDHS generated ones (see Equation 5). In the paper the mixing weight γ is fixed (γ = 0.5), but its precise contribution is not studied. Varying γ may reveal an optimal balance between relying on external supervision and the hallucination‐inducing generation. Another key design choice is the hybrid “Mixed-DPO” strategy that combines offline preference data and online generated preference pairs with a fixed mixing probability p (p = 0.5 is used). Since the benefit of integrating online signals over offline data likely depends on the degree of mixing, an ablation study that varies p from fully offline (p = 1.0) to fully online (p = 0.0) would help us better understand this trade-off. Measuring standard metrics (POPE, MMHAL, MMHALv, LLaVAW, VQAT, GQA, MMVet, Recallcoco) in both experiments should provide insight into the optimal settings and robustness of the alignment approach.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### BDHS Loss Mixing Parameter Ablation
- **Ablated Part**: The integration balance in BDHS between externally supervised non-preferred responses and BDHS-generated non-preferred responses as used in the averaged DPO loss (Equation 5)
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.25
  - 0.5
  - 0.75
  - 1.0
- **Metrics**: POPE, MMHAL, MMHALv, LLaVAW, VQAT, GQA, MMVet, Recallcoco

### Mixed-DPO Offline-Online Mixing Ablation
- **Ablated Part**: The probability p that controls the sampling mix between offline preference data and online generated preference pairs in the Mixed-DPO method
- **Action**: REPLACE
- **Replacement**: 
  - 0.0
  - 0.25
  - 0.5
  - 0.75
  - 1.0
- **Metrics**: POPE, MMHAL, MMHALv, LLaVAW, VQAT, GQA, MMVet, Recallcoco

</div>