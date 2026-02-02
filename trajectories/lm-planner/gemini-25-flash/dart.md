<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/dart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user requested up to 5 ablation studies for the paper "Differentiable Prompt Makes Pre-trained Language Models Better Few-shot Learners (DART)".

My strategy is to identify the key novel components of the DART method based on the abstract and the description of the approach, and then propose ablation studies that isolate the contribution of these components.

The core novelties highlighted in the abstract and method sections are:
1.  **Differentiable Template Optimization**: Using trainable pseudo tokens for the prompt template.
2.  **Differentiable Label Optimization**: Mapping class labels to trainable pseudo tokens.
3.  **Auxiliary Fluency Constraint Objective ($\mathcal{L}_F$)**: An additional MLM loss to regularize the prompt embeddings.
4.  **Joint Optimization**: Optimizing templates and labels together.

I will propose ablation studies targeting these components and potentially key hyperparameters.

1.  **Ablating Differentiable Label Optimization**: The paper specifically mentions optimizing label tokens in continuous space as a new branch of research. Comparing DART's approach to using discrete label tokens (like previous methods) is crucial to show the benefit of this novelty.
2.  **Ablating Differentiable Template Optimization**: Similarly, optimizing the template in continuous space is a core part of DART. Comparing it to using a fixed or manually designed template will demonstrate its value.
3.  **Ablating the Fluency Constraint**: The auxiliary loss is introduced to improve training stability and prompt quality. Removing this term will show its impact on performance.
4.  **Varying Hyperparameters**: The number of pseudo tokens used for the template and the weight of the fluency constraint ($\lambda$) are important hyperparameters. Investigating their sensitivity can provide insights into the method's robustness and optimal configuration.

Based on this, I will propose the following 5 ablation studies, ranked by their perceived importance in demonstrating the value of DART's core contributions:

1.  **Discrete Label Baseline**: Replace the differentiable label embeddings with discrete tokens selected from the vocabulary. This directly tests the benefit of differentiable label optimization.
2.  **Fixed Template Baseline**: Replace the differentiable template embeddings with a simple, fixed, hand-crafted template. This tests the benefit of differentiable template optimization.
3.  **No Fluency Constraint**: Remove the auxiliary fluency constraint objective ($\mathcal{L}_F$) from the total loss. This tests the contribution of the regularization term.
4.  **Template Token Count Sensitivity**: Vary the number of trainable pseudo tokens used for the template. This tests the impact of the length of the continuous template.
5.  **Fluency Constraint Weight Sensitivity**: Vary the hyperparameter $\lambda$ that weights the fluency constraint objective. This tests the importance of the strength of the auxiliary regularization.

The paper evaluates performance on classification tasks and mentions "better few-shot performance" and "absolute performance improvement". Standard metrics for these tasks include Accuracy and F1-score. I will include both in the metrics list for each ablation.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Discrete Label Baseline
- **Ablated Part**: Differentiable label embeddings
- **Action**: REPLACE
- **Replacement**: 
  - Discrete label tokens (selected from vocabulary, e.g., via search)
- **Metrics**: Accuracy, F1-score

### Fixed Template Baseline
- **Ablated Part**: Differentiable template embeddings
- **Action**: REPLACE
- **Replacement**: 
  - Fixed, hand-crafted template (e.g., '[X] [MASK] .')
- **Metrics**: Accuracy, F1-score

### No Fluency Constraint
- **Ablated Part**: Auxiliary fluency constraint objective (L_F)
- **Action**: REMOVE
- **Metrics**: Accuracy, F1-score

### Template Token Count Sensitivity
- **Ablated Part**: Number of trainable pseudo tokens in the template
- **Action**: REPLACE
- **Replacement**: 
  - List of token counts
- **Metrics**: Accuracy, F1-score

### Fluency Constraint Weight Sensitivity
- **Ablated Part**: Weight (lambda) of the fluency constraint objective
- **Action**: REPLACE
- **Replacement**: 
  - List of lambda values
- **Metrics**: Accuracy, F1-score

</div>