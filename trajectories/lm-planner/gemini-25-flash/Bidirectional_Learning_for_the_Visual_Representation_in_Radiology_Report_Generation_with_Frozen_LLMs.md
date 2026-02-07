<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Bidirectional_Learning_for_the_Visual_Representation_in_Radiology_Report_Generation_with_Frozen_LLMs

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel bidirectional learning framework for radiology report generation using frozen LLMs. The core idea is to enhance the visual representation by making it both interpretable by the LLM for text generation (vision-to-text, V2T) and generatable by the LLM when given the ground truth report (text-to-vision, T2V). Additionally, an image reconstruction task (Img Rec) is used to ensure the visual representation captures image features. The framework consists of a vision encoder, visual mapper, a frozen LLM, a *newly trained* text encoder, textual mapper, and a vision decoder. The training objective is a combination of three loss terms: VTC loss (for V2T), TVC loss (for T2V), and REC loss (for Img Rec), weighted by hyperparameters λ1 and λ2.

The paper includes an ablation study (Table 3) that evaluates the contribution of the T2V and Img Rec components by comparing models trained with V2T only, V2T+CLIP (as a baseline comparison), V2T+T2V, and the full V2T+T2V+Img Rec model. This ablation successfully demonstrates the positive impact of the T2V and Img Rec components on both NLG and clinical efficacy metrics. Table 4 further shows that the T2V module improves performance when integrated into a different backbone (R2GenGPT).

While the existing ablations validate the main proposed learning objectives (T2V and Img Rec losses), there are other significant design choices and components whose impact is not fully explored:

1.  **The Text Encoder for the T2V Branch:** The paper explicitly states the need to "jointly learn a new text encoder" for the T2V branch instead of using the LLM's built-in word embedding layer (lines 211-215), providing several justifications. However, there is no ablation study to verify if using the LLM's built-in embedding layer (perhaps with the textual mapper) would yield significantly worse results. This ablation would directly test the necessity and benefit of training a separate text encoder for the text-to-vision task.
2.  **The Weights of the Regularization Losses (λ1, λ2):** The total loss is a weighted sum of the VTC, TVC, and REC losses, with weights λ1 and λ2 for TVC and REC, respectively. The paper mentions that λ1 and λ2 are set to 1 without fine-tuning (line 311). Ablating these hyperparameters would reveal the sensitivity of the model's performance to the balance between the main VTC loss and the two regularization terms (TVC and REC). Testing different values for these weights is a standard practice to understand their influence and potentially find optimal settings.

Based on their importance in validating key architectural and training design choices, these two ablations are the most significant missing studies. The first directly questions a justified design choice, while the second explores the sensitivity to crucial training hyperparameters.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### T2V Text Encoder Mechanism
- **Ablated Part**: The newly trained text encoder in the Text-to-Vision (T2V) branch.
- **Action**: REPLACE
- **Replacement**: 
  - Use the frozen LLM's built-in word embedding layer (potentially with the textual mapper)
- **Metrics**: BLEU-4, ROUGE, METEOR, RadGraph F1, Bert Score, RadCliQ

### Regularization Loss Weight Sensitivity
- **Ablated Part**: Hyperparameters lambda1 (weight for TVC loss) and lambda2 (weight for REC loss).
- **Action**: REPLACE
- **Replacement**: 
  - {'lambda1': 0.1, 'lambda2': 1.0}
  - {'lambda1': 0.5, 'lambda2': 1.0}
  - {'lambda1': 2.0, 'lambda2': 1.0}
  - {'lambda1': 1.0, 'lambda2': 0.1}
  - {'lambda1': 1.0, 'lambda2': 0.5}
  - {'lambda1': 1.0, 'lambda2': 2.0}
  - {'lambda1': 0.5, 'lambda2': 0.5}
  - {'lambda1': 2.0, 'lambda2': 2.0}
- **Metrics**: BLEU-4, ROUGE, METEOR, RadGraph F1, Bert Score, RadCliQ

</div>