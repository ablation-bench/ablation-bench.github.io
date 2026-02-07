<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Improving_the_Transferability_of_Adversarial_Attacks_through_Experienced_Precise_Nesterov_Momentum

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes Experienced Precise Nesterov momentum (EPN) to improve the transferability of adversarial attacks. EPN combines two main components: Experienced Momentum (EM) and Precise Nesterov momentum (PN).

1.  **Experienced Momentum (EM):** This involves pre-training the initial momentum value instead of starting from zero. The pre-training is done on a set of models derived by Random Channels Swapping (RCS) applied to the input image. The paper claims RCS helps prevent overfitting of EM and improves transferability.
2.  **Precise Nesterov momentum (PN):** This modifies the standard Nesterov momentum update by incorporating the gradient of the current data point into the pre-update calculation and the momentum accumulation formula (Eq 3).

The paper includes ablation studies in Section 4.4:
*   Impact of the decay factor µ for EPNI-FGSM.
*   Impact of the number of pretraining epochs for EM (epochs) for EPNI-FGSM.
*   Impacts of EM and PN by comparing NI-FGSM (baseline), ENI-FGSM (NI + EM), PNI-FGSM (NI + PN), and EPNI-FGSM (NI + EM + PN). This shows that both EM and PN contribute positively and their combination is better.

Based on the method description and the existing ablations, I identify two important missing ablation studies:

1.  **The role of Random Channels Swapping (RCS) in EM training:** The paper states that RCS is used during EM training to prevent overfitting and improve transferability, but there is no direct experiment showing the effect of training EM *without* RCS. An ablation removing RCS from the EM training process would directly evaluate its contribution to EM's effectiveness and the overall EPN performance.
2.  **The specific contribution of the current gradient term in the PN momentum update:** The PN momentum update formula (Eq 3) includes the normalized gradient of the current data point (`nabla J(f(x_t)) / ||nabla J(f(x_t))||_1`) in addition to the standard Nesterov terms (scaled previous momentum and gradient at the pre-update point). An ablation study removing this specific term from Eq 3 would clarify its impact on the performance of PN and EPN, helping to understand the precise mechanism by which PN improves upon standard Nesterov momentum.

These two ablations target key novel components of the proposed method (how EM is trained and the specific form of the PN update) that are not fully dissected in the existing ablation studies. They are ranked by focusing first on the EM training process (RCS) and then on the PN update formula detail. The primary metric used throughout the paper is Attack Success Rate, particularly the average attack success rate against different target models.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation on RCS for EM Training
- **Ablated Part**: Random Channels Swapping (RCS) applied during Experienced Momentum (EM) training
- **Action**: REMOVE
- **Metrics**: Average Attack Success Rate

### Ablation on Current Gradient in PN Update
- **Ablated Part**: Inclusion of the current gradient term in the Precise Nesterov (PN) momentum update formula (Eq 3)
- **Action**: REMOVE
- **Metrics**: Average Attack Success Rate

</div>