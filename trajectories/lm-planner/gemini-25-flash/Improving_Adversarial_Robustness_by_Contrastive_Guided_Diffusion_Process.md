<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Improving_Adversarial_Robustness_by_Contrastive_Guided_Diffusion_Process

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes Contrastive-Guided Diffusion Process (Contrastive-DP) to improve adversarial robustness by generating more distinguishable synthetic data. The core idea is to add the gradient of a contrastive loss to the diffusion model's sampling process (Algorithm 1). The paper presents several ablation studies in Section 5.2:
1.  **Sensitivity of λ:** Investigates the impact of the strength of the contrastive guidance during sampling.
2.  **Effectiveness of different contrastive losses:** Compares InfoNCE and Hard Negative Mining (HNM) losses, and the effect of using an additional embedding network, all applied as guidance during sampling.
3.  **Data selection:** Evaluates different post-generation selection criteria and compares selection on Contrastive-DP generated data versus vanilla DDIM generated data.

While these ablations provide insights into the hyperparameters and specific formulation of the contrastive loss used for guidance, they do not explore alternative ways of integrating the contrastive signal or the temporal aspect of applying the guidance during the multi-step diffusion process.

Based on the method's design and the existing ablations, two important missing ablation studies are:

1.  **Contrastive Integration Method (Training vs. Sampling Guidance):** The current method applies contrastive loss gradient as guidance *during the sampling process* of a potentially pre-trained diffusion model. A natural alternative would be to incorporate the contrastive objective directly into the *training process* of the diffusion model itself. This would train the diffusion model to inherently generate more distinguishable samples, rather than guiding a pre-trained model during generation. Comparing these two approaches (training-time integration vs. sampling-time guidance) is crucial to understand the specific contribution and efficiency of the proposed guidance mechanism.
2.  **Temporal Guidance Application:** The current Contrastive-DP applies the contrastive gradient guidance at *every* time step `t` during the reverse diffusion process (Algorithm 1). Diffusion models transition from pure noise to clear images over many steps. The effectiveness or necessity of the contrastive signal might vary depending on the noise level (i.e., the time step). Ablating the application of guidance to specific phases (e.g., early noisy steps, intermediate steps, late denoising steps) or applying it less frequently could reveal insights into *when* the distinguishability signal is most impactful and potentially lead to more efficient generation.

These two ablations are important because they investigate fundamental aspects of how the contrastive signal is used (training vs. sampling) and how it is applied over time during the generative process, which are not covered by the existing experiments and are key to understanding the method's performance. The relevant metrics used in the paper are clean accuracy and robust accuracy.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Contrastive Integration Method
- **Ablated Part**: Method of integrating contrastive loss (training vs. sampling guidance)
- **Action**: REPLACE
- **Replacement**: 
  - Integrate contrastive loss during diffusion model training
- **Metrics**: clean acc, rob acc

### Temporal Guidance Application
- **Ablated Part**: Time steps during diffusion sampling where contrastive guidance is applied
- **Action**: REPLACE
- **Replacement**: 
  - Apply guidance only during early steps
  - Apply guidance only during late steps
  - Apply guidance every N steps
- **Metrics**: clean acc, rob acc

</div>