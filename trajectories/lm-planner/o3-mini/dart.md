<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/dart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose four ablation experiments to understand the contributions of key components in DART. First, we remove the auxiliary fluency constraint objective that is used to bind the continuously optimized pseudo prompt tokens, in order to quantify its role in ensuring coherent contextual representations. Second, we replace the differentiable (continuous) label optimization with a conventional discrete label selection (using fixed, handpicked label tokens) to see if the continuous label representations provide a significant advantage in handling complex label semantics. Third, we disable the differentiable template optimization by freezing the pseudo tokens (i.e. using fixed embeddings instead of updating them with backpropagation) to assess the benefit of learning the continuous prompt template. Fourth, instead of the joint optimization of both templates and labels, we try a sequential (or decoupled) optimization (for example, optimizing templates first and then labels, or vice versa) to study whether joint training is critical for stable few-shot performance. We will measure the effects across standard few-shot classification metrics such as accuracy, F1 score, and (when applicable) cross-entropy loss or stability measures.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Fluency Constraint Removal
- **Ablated Part**: Auxiliary fluency constraint objective that enforces co-dependence among prompt template tokens
- **Action**: REMOVE
- **Metrics**: Accuracy, F1, CrossEntropy Loss

### Ablation 2: Discrete Label Tokens
- **Ablated Part**: Differentiable label optimization for continuous label tokens
- **Action**: REPLACE
- **Replacement**: 
  - Pre-defined discrete label tokens
- **Metrics**: Accuracy, F1, CrossEntropy Loss

### Ablation 3: Fixed Prompt Template
- **Ablated Part**: Differentiable prompt template optimization (updating pseudo-token embeddings)
- **Action**: REMOVE
- **Metrics**: Accuracy, F1, Loss

### Ablation 4: Sequential Optimization
- **Ablated Part**: Joint optimization of template and label tokens
- **Action**: REPLACE
- **Replacement**: 
  - Optimize template first then labels
  - Optimize labels first then template
- **Metrics**: Accuracy, F1, Stability

</div>