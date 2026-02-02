<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Prototypical_evoluation_for_few_shot_learning_in_vision_language_model_adaptation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Prototypical Evolutionary Adaptation (PEA)" proposes a novel method for few-shot learning in Vision-Language Models (VLMs) by dynamically calibrating class prototypes. The core ideas are:
1.  Initializing prototypes using the average of support sample features (Nearest Mean Classifier approach).
2.  Introducing learnable shift vectors ($\Delta_c$) to evolve these initial prototypes ($\overline{c}_y$) via $\overline{c}'_y = \overline{c}_y + \alpha \cdot \Delta_c$.
3.  Classifying samples based on the similarity between the query image embedding ($u$) and the sum of the evolved visual prototype ($\overline{c}'_y$) and the text embedding ($t_y$) for each class (Equation 6: $\langle \overline{c}'_y + t_y, u \rangle$).

The paper mentions conducting ablation studies on the hyperparameter $\alpha$ and using the ResNet-50 backbone, but the results of these specific ablations are not presented in the provided text. The main experimental results compare PEA against various baseline methods (Zero-Shot, LP variants, Prompt Tuning, Adapter methods), which demonstrates overall performance but does not isolate the contribution of PEA's specific components.

To better understand the effectiveness of PEA's novel contributions, two key ablation studies are missing:
1.  **Ablating the learned shift vector ($\Delta_c$):** This would evaluate the impact of the "Evolutionary" part of PEA. By removing the learned shift, the evolved prototype $\overline{c}'_y$ would simply be the initial prototype $\overline{c}_y$. The classification would still incorporate the text embedding as in the full PEA method. This ablation isolates the benefit of learning the dynamic shift to refine the initial prototype.
2.  **Ablating the addition of the text embedding ($t_y$) in the final classification:** The full PEA method classifies based on the similarity to the *sum* of the evolved visual prototype and the text embedding. This is a distinct approach compared to methods that use only visual prototypes or learn a linear classifier initialized by text embeddings. Removing the text embedding from this final similarity calculation would test the contribution of explicitly combining the visual and text modalities in this manner. The classification would then be based solely on the similarity to the evolved visual prototype $\overline{c}'_y$.

These two ablations are crucial for attributing PEA's performance gains to its specific architectural and methodological choices beyond a standard prototype-based method or simply initializing with text features. They are highly important for understanding which aspects of PEA are most effective. The relevant metrics used in the paper are average accuracy across datasets and out-of-distribution (OOD) average accuracy.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: No Learned Shift
- **Ablated Part**: Learnable shift vector (Delta_c) in prototype evolution
- **Action**: REMOVE
- **Metrics**: Average accuracy, OOD Average accuracy

### Ablation: No Text Embedding in Classification
- **Ablated Part**: Addition of text embedding (t_y) in the final classification similarity calculation
- **Action**: REMOVE
- **Metrics**: Average accuracy, OOD Average accuracy

</div>