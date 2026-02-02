<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/Rethinking_Multiple_Instance_Learning_From_Feature_Space_to_Probability_Space

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Rethinking Multiple-Instance Learning From Feature Space to Probability Space" introduces a novel approach to Multiple-Instance Learning (MIL) by transitioning from feature space to probability space. The key components of the proposed Probability-Space MIL network (PSMIL) include a self-training alignment strategy and a probability-space attention pooling mechanism. The paper provides a comprehensive set of experiments, including ablation studies, to demonstrate the effectiveness of these components.

The existing ablation studies in the paper focus on the two main strategies: probability-space attention pooling (PSAtt) and probability-space alignment (PSAli). The ablation results show the impact of these strategies on the performance of the model, particularly in complex datasets like CIFAR-10 and CIFAR-100. The paper also explores the effect of different values of the alignment parameter λ.

However, there are some potential missing ablation studies that could further elucidate the contributions of specific components or design choices in the PSMIL framework. One such missing ablation could involve the class prototypes used in the probability-space attention mechanism. Another potential ablation could explore the impact of the momentum-based update strategy for the class prototypes.

These missing ablations are important because they could provide insights into the sensitivity of the model to specific design choices and help in understanding the robustness and generalizability of the proposed method.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Class Prototypes
- **Ablated Part**: class prototypes used in probability-space attention pooling
- **Action**: REMOVE
- **Metrics**: accuracy, AUC, F1

### Ablation of Momentum-based Update
- **Ablated Part**: momentum-based update strategy for class prototypes
- **Action**: REPLACE
- **Replacement**: 
  - no momentum
  - higher momentum (0.01)
  - lower momentum (0.0001)
- **Metrics**: accuracy, AUC, F1

</div>