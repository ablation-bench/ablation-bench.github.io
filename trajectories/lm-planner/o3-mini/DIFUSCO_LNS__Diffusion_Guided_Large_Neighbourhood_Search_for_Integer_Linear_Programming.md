<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/DIFUSCO_LNS__Diffusion_Guided_Large_Neighbourhood_Search_for_Integer_Linear_Programming

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that target core design choices of DIFUSCO-LNS. First, while the paper ablates the number of inference diffusion steps and inference schedulers, it does not analyze the contribution of integrating the diffusion hidden state into the policy network. In DIFUSCO-LNS the denoising process produces binary diffusion hidden states that are incorporated into the variable node features via a positional encoding scheme. Removing this integration would help isolate the benefits of the multimodal modeling capacity provided by the diffusion process in guiding destroy policy generation. Second, the method relies on expert demonstrations collected via Local Branching with a quality filtering parameter (αₕq) set to 0.5. The quality of these demonstrations is critical to successful imitation learning. Varying this threshold (for instance, testing values below and above 0.5) could elucidate how sensitive the overall performance is to the quality and quantity of the collected high-quality destroy policies. Both ablations are evaluated using established metrics (primal gap, primal integral, and primal bound) that are reported in the paper.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Remove Diffusion Hidden State Integration
- **Ablated Part**: Integration of the diffusion hidden state (with positional encoding) into the policy network's variable features
- **Action**: REMOVE
- **Metrics**: primal gap, primal integral, primal bound

### Ablation: Vary Expert Demonstration Quality Threshold
- **Ablated Part**: Quality filtering parameter (αₕq) used for selecting high-quality LB demonstrations
- **Action**: REPLACE
- **Replacement**: 
  - 0.3
  - 0.5
  - 0.7
- **Metrics**: primal gap, primal integral, primal bound

</div>