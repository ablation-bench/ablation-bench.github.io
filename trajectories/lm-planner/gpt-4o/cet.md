<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/cet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Preserving Commonsense Knowledge from Pre-trained Language Models via Causal Inference" introduces a novel method called Causal Effect Tuning (CET) to address the issue of catastrophic forgetting during fine-tuning of pre-trained language models (PLMs). The method is based on causal inference and aims to preserve the pre-trained knowledge while allowing the model to learn new knowledge from the target data. The key components of the method include a causal graph that identifies the missing causal effects from the pre-trained data as the root cause of catastrophic forgetting, and a unified objective that combines the vanilla fine-tuning objective with a causal objective to preserve old knowledge.

To design ablation studies, we need to focus on the major components of the method and understand their contributions to the overall performance. The main components to consider for ablation are the causal graph, the unified objective, the heuristic estimation for commonsense QA, and the hyper-parameters involved in the method.

1. Ablation of the Causal Graph: The causal graph is central to the method as it frames the problem of catastrophic forgetting and guides the design of the unified objective. Ablating the causal graph would involve removing the causal paths that preserve pre-trained knowledge and observing the impact on performance.

2. Ablation of the Unified Objective: The unified objective is a combination of the vanilla fine-tuning objective and the causal objective. Ablating this component would involve testing the performance of the model with only the vanilla fine-tuning objective or only the causal objective.

3. Ablation of the Heuristic Estimation: The heuristic estimation is used to approximate the causal effect in commonsense QA. Ablating this component would involve replacing the heuristic estimation with alternative methods for estimating the causal effect, such as using different similarity metrics or removing the heuristic estimation altogether.

4. Ablation of Hyper-parameters: The method involves several hyper-parameters, such as the number of nearest neighbors (K) and the similarity threshold (θ). Ablating these hyper-parameters would involve testing the performance of the model with different values for these parameters or removing them to observe their impact.

5. Ablation of the Plug-in Module: The method can be implemented as a plug-in module to enhance existing QA models. Ablating this component would involve testing the performance of the model without the plug-in module to understand its contribution to the overall performance.

These ablation studies will help attribute the method's performance to its major components and provide insights into the effectiveness of each component in preserving commonsense knowledge during fine-tuning.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Causal Graph
- **Ablated Part**: Causal graph that frames the problem of catastrophic forgetting
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score

### Ablation of Unified Objective
- **Ablated Part**: Unified objective combining vanilla fine-tuning and causal objective
- **Action**: REPLACE
- **Replacement**: 
  - vanilla fine-tuning objective only
  - causal objective only
- **Metrics**: accuracy, F1-score

### Ablation of Heuristic Estimation
- **Ablated Part**: Heuristic estimation for commonsense QA
- **Action**: REPLACE
- **Replacement**: 
  - alternative similarity metrics
  - remove heuristic estimation
- **Metrics**: accuracy, F1-score

### Ablation of Hyper-parameters
- **Ablated Part**: Hyper-parameters such as number of nearest neighbors (K) and similarity threshold (θ)
- **Action**: REPLACE
- **Replacement**: 
  - different values for K
  - different values for θ
- **Metrics**: accuracy, F1-score

### Ablation of Plug-in Module
- **Ablated Part**: Plug-in module to enhance existing QA models
- **Action**: REMOVE
- **Metrics**: accuracy, F1-score

</div>