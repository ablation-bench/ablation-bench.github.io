<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Local_Prompt__Extensible_Local_Prompts_for_Few_Shot_Out_of_Distribution_Detection

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Local-Prompt: Extensible Local Prompts for Few-Shot Out-of-Distribution Detection" proposes a novel few-shot OOD detection method based on vision-language models, focusing on enhancing local information using trainable local prompts while keeping global prompts frozen. The method has two main components: global prompt guided negative augmentation and local prompt enhanced regional regularization. The global prompts (hand-crafted and frozen during training) are used to guide the selection of hard negative samples via random cropping and similarity calculation. The local prompts are trainable and optimized using contrastive and diversity regularization losses based on local image features. The method also introduces regional-related OOD and ID scores.

The paper includes several ablation studies in Section 5.2 and Appendix C, investigating:
1.  The effectiveness of the loss components ($\mathcal{L}_{\text{pos}}$, $\mathcal{L}_{\text{neg}}$, $\mathcal{L}_{\text{reg}}$).
2.  The influence of different negative augmentation strategies (random crop vs. others).
3.  The number of local negative prompts ($N_{\text{neg}}$).
4.  Different OOD score strategies (MCM, GL-MCM, Regional-MCM).
5.  The influence of loss coefficients ($\lambda_{\text{neg}}$, $\lambda_{\text{reg}}$).
6.  The regional number $k$ used in the scores.
7.  Training time.
8.  The number of negative augmentations selected.

While these ablations cover various aspects, two important design choices are not fully explored:
1.  **The decision to freeze global prompts during training:** The paper emphasizes training *local* prompts and freezing global ones. It shows that combining the trained local prompts with *pre-trained* global prompts (from LoCoOp) at inference time improves performance. However, it does not investigate training the global prompts *alongside* the local prompts within their own framework. An ablation comparing the proposed training strategy (frozen global prompts + trainable local prompts) with one where global prompts are also trainable would directly assess the impact of this core design choice during training.
2.  **The mechanism for selecting hard negative samples:** The negative augmentation is guided by frozen global prompts, selecting crops with the least similarity to the class prompt. An ablation is performed on the *type* of augmentation (random crop) and the *number* of negative samples, but not on the *guidance mechanism* itself. Comparing the global prompt guided selection with a simpler alternative, such as purely random selection of negative crops, would demonstrate the value of the global prompt guidance in identifying useful hard negative samples.

These two missing ablations are crucial for understanding the contribution of freezing global prompts during training and the effectiveness of the global prompt guided negative augmentation strategy, respectively. They directly probe key components of the proposed Local-Prompt method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Trainable Global Prompts during Training
- **Ablated Part**: Training strategy for global prompts
- **Action**: REPLACE
- **Replacement**: 
  - Trainable global prompts (e.g., initialized randomly or from LoCoOp)
- **Metrics**: FPR95, AUROC, ID accuracy

### Negative Augmentation Guidance Mechanism
- **Ablated Part**: Global prompt guidance in negative augmentation selection
- **Action**: REPLACE
- **Replacement**: 
  - Random selection of negative crops
- **Metrics**: FPR95, AUROC, ID accuracy

</div>