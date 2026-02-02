<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Pose_Priors_from_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Pose Priors from Language Models" proposes a novel zero-shot method, ProsePose, for 3D human pose estimation that leverages the semantic knowledge of physical contact embedded in Large Multimodal Models (LMMs). The core idea is to prompt an LMM with an image to generate a list of contact constraints between body parts, convert these constraints into a loss function, and use this loss to refine an initial pose estimate via optimization.

The paper includes several ablation studies:
1.  **Effect of LMM Samples (N):** Figure 5 shows that averaging the loss over multiple samples from the LMM improves performance, demonstrating a method to mitigate LMM hallucination.
2.  **Impact of Loss Terms:** Table 3 ablates each loss term in the joint optimization, showing that the LMM loss ($\mathcal{L}_{\text{LMM}}$) and the 2D keypoint loss ($\mathcal{L}_{\text{2D}}$) are the most crucial for performance.
3.  **Choice of LMM:** Section 7.4 and Table 6 compare the performance when using GPT4-V versus LLaVA+GPT4, indicating that GPT4-V yields better results.

While these ablations are informative, they do not fully explore the critical aspects of how the LMM prior is elicited and defined. Specifically, two important missing ablations relate to the LMM prompting strategy and the granularity of the body regions used for defining constraints.

First, the paper mentions using a "chain-of-thought" technique in the prompt (L239-241) by asking the LMM to describe the pose or reasoning before listing constraints. This is a common strategy to improve LLM performance, and ablating this component would quantify its specific contribution to the pose estimation task in this framework. It would show whether the LMM's ability to generate useful contact constraints is significantly dependent on this explicit reasoning step.

Second, the paper defines a specific set of "coarse regions" (L194-201, §6.2) for the LMM to reference in the constraints, noting that LMMs struggle with fine-grained or chirality distinctions. However, the evaluation metric PCC is calculated using a set of 75 "fine-grained regions" (L355-359, §7.1). An ablation studying the impact of using these fine-grained regions directly in the LMM prompt and constraint definition, instead of the coarse ones, would be highly valuable. This would reveal whether the LMM can effectively reason about contact at a finer granularity and whether the method's performance is sensitive to the level of detail in the contact definition provided to the LMM.

These two missing ablations are crucial for understanding the robustness and effectiveness of the LMM-based prior generation process, which is the core novelty of ProsePose. They investigate how the input (prompt structure, region definition) affects the quality of the LMM's output and, consequently, the final pose estimation performance.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Chain-of-Thought Prompting
- **Ablated Part**: The instruction in the LMM prompt asking for reasoning or description before listing contact constraints.
- **Action**: REMOVE
- **Metrics**: Joint PA-MPJPE, Avg. PCC, PA-MPJPE

### Ablation of Body Region Granularity
- **Ablated Part**: The set of coarse body regions used in the LMM prompt and constraint definition.
- **Action**: REPLACE
- **Replacement**: 
  - The set of 75 fine-grained regions used for PCC calculation.
- **Metrics**: Joint PA-MPJPE, Avg. PCC, PA-MPJPE

</div>