<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/dart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper introduces a novel approach called DifferentiAble pRompT (DART) that enhances the few-shot learning capabilities of pre-trained language models by optimizing prompt templates and target labels in a differentiable manner. The key components of DART include differentiable template optimization, differentiable label optimization, and a fluency constraint objective. These components are crucial for the performance improvements reported in the paper. Therefore, the ablation studies should focus on these components to understand their individual contributions to the overall performance.

1. Differentiable Template Optimization: This component allows the model to optimize prompt templates in a continuous space, which is expected to provide more expressive templates than discrete tokens. An ablation study could involve removing this component to see how much it contributes to the performance.

2. Differentiable Label Optimization: This component maps class labels to a continuous vocabulary space, which is crucial for handling complex label semantics. An ablation study could involve replacing this with a traditional discrete label mapping to evaluate its impact.

3. Fluency Constraint Objective: This auxiliary objective ensures the association among template tokens and maintains the language understanding ability of the model. An ablation study could involve removing this objective to assess its importance.

4. Joint Optimization of Templates and Labels: The paper mentions that joint optimization of templates and labels helps mitigate instability in few-shot fine-tuning. An ablation study could involve optimizing them separately to evaluate the benefits of joint optimization.

5. Use of Unused Tokens: The approach uses unused tokens in the vocabulary for optimization. An ablation study could involve using different sets of tokens to see if the choice of tokens affects performance.

The metrics to report for these ablation studies should include the few-shot performance on the NLP tasks evaluated in the paper, such as accuracy or F1 score, as these are the primary metrics used to demonstrate the effectiveness of DART.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1
- **Ablated Part**: Differentiable Template Optimization
- **Action**: REMOVE
- **Metrics**: accuracy, F1

### Ablation 2
- **Ablated Part**: Differentiable Label Optimization
- **Action**: REPLACE
- **Replacement**: 
  - discrete label mapping
- **Metrics**: accuracy, F1

### Ablation 3
- **Ablated Part**: Fluency Constraint Objective
- **Action**: REMOVE
- **Metrics**: accuracy, F1

### Ablation 4
- **Ablated Part**: Joint Optimization of Templates and Labels
- **Action**: REPLACE
- **Replacement**: 
  - separate optimization
- **Metrics**: accuracy, F1

### Ablation 5
- **Ablated Part**: Use of Unused Tokens
- **Action**: REPLACE
- **Replacement**: 
  - different token sets
- **Metrics**: accuracy, F1

</div>