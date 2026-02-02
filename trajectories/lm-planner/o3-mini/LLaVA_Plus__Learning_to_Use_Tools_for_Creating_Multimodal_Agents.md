<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/LLaVA_Plus__Learning_to_Use_Tools_for_Creating_Multimodal_Agents

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper shows several ablations that focus on the impact of training with explicit tool‐use examples (e.g., “no thoughts” ablation, testing “LLaVA (Tools in Test)” vs. “LLaVA-Plus”) and even an incremental tool-specific fine‐tuning experiment. However, two important areas remain unexplored:
1. The continuous incorporation of raw visual input during the entire dialogue. One of the main claims of LLaVA-Plus is that the image query is not only used at the beginning but is actively provided throughout the session—improving planning and tool selection. A missing ablation is to remove or restrict this continuous visual context after the initial query and see how much the maintained image information contributes to performance. Assessing this would reveal the importance of “continuous” visual grounding in multimodal interactions.
2. The contribution of a diverse skill repository. LLaVA-Plus is trained with an extensive set of skills (both core visual understanding and extended skills such as external knowledge retrieval, image generation/editing, and interactive segmentation). There is room for an ablation study that removes the extended (non–core) skills from the repository and trains the model using only core visual understanding skills. This study would quantify how much each type of skills (or the extent of skill diversity) impacts overall performance on tasks that require tool use, including the specialized evaluations (e.g., grounding, OCR, captioning).
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Continuous Visual Context Ablation
- **Ablated Part**: Raw image input provided continuously during multi-turn tool use dialogues
- **Action**: REMOVE
- **Metrics**: LLaVA-Bench Conversation Score, LLaVA-Bench Detail Score, LLaVA-Bench Reasoning Score, SEED-Bench Accuracy

### Skill Repository Diversity Ablation
- **Ablated Part**: Extended skills (e.g., external knowledge retrieval, image generation/editing, interactive segmentation) in the skill repository
- **Action**: REMOVE
- **Metrics**: Tool Use Accuracy (Grounding, Tagging, Caption, OCR), LLaVA-Bench (Tools) Performance, VisIT-Bench ELO Ratings

</div>