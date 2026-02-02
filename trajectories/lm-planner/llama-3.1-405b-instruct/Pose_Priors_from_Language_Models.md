<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Pose_Priors_from_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Pose Priors from Language Models" presents a zero-shot pose optimization method that leverages large pretrained text-based models to improve pose estimation by converting natural language descriptors into tractable losses to constrain the 3D pose optimization. The method, called ProsePose, produces surprisingly compelling pose reconstructions of people in close contact, correctly capturing the semantics of the social and physical interactions.

The paper evaluates ProsePose on three 2-person interaction datasets and one dataset of complex yoga poses, showing that it produces more accurate reconstructions than previous approaches that do not use a large amount of task-specific data for training. The results indicate that LMMs, without any additional finetuning, offer a useful prior for pose reconstruction.

To further investigate the effectiveness of ProsePose, we suggest two missing ablation studies:

1. Ablating the language model: The paper uses GPT4-V as the LMM, but it would be interesting to see how the performance of ProsePose changes when using different language models, such as LLaVA or other variants of GPT.
2. Ablating the constraint generation: The paper uses a specific method to generate constraints from the LMM's output, but it would be interesting to see how the performance of ProsePose changes when using different constraint generation methods or parameters.

These ablation studies would provide further insights into the effectiveness of ProsePose and its components, and would help to identify potential areas for improvement.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: Language Model
- **Action**: REPLACE
- **Replacement**: 
  - LLaVA
  - GPT-3
- **Metrics**: PA-MPJPE, PCC

### Ablation B
- **Ablated Part**: Constraint Generation
- **Action**: REPLACE
- **Replacement**: 
  - Different constraint generation method
  - Different parameters for constraint generation
- **Metrics**: PA-MPJPE, PCC

</div>