<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/storm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose five ablation studies that individually investigate the key components of STORM’s pre‐writing pipeline. First, by removing the perspective-guided question asking, we can assess how vital diversifying viewpoints is to generating comprehensive and well-organized outlines. Second, by eliminating the simulated multi-turn conversation, we can study the importance of iterative follow-up questions in enriching topic exploration. Third, by disabling the retrieval-grounding step in generating factual answers, we evaluate the contribution of trusted external sources in reducing hallucination and improving factuality. Fourth, by bypassing the outline refinement stage (i.e. not integrating conversation-derived insights with the LLM’s initial draft outline), we isolate the role of conversation feedback in curating a robust outline. Finally, by varying the number of conversation rounds (M), we aim to understand how the depth of interaction impacts the overall outline quality as measured by heading soft recall, heading entity recall, and expert assessments (e.g., organization and breadth). These studies together can illuminate which parts of the proposed pipeline contribute most significantly to the final performance.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: No Perspective Guidance
- **Ablated Part**: The component that discovers and employs multiple diverse perspectives to guide question asking
- **Action**: REMOVE
- **Metrics**: heading_soft_recall, heading_entity_recall, editor_organization_score, editor_coverage_score

### Ablation 2: No Simulated Multi-turn Conversation
- **Ablated Part**: The iterative multi-turn conversation simulation that updates question asking with conversation history
- **Action**: REMOVE
- **Metrics**: heading_soft_recall, heading_entity_recall, editor_organization_score, editor_coverage_score

### Ablation 3: No Retrieval-Grounded Answers
- **Ablated Part**: The retrieval augmentation step that grounds answers on trusted external sources during conversation
- **Action**: REMOVE
- **Metrics**: heading_soft_recall, heading_entity_recall, editor_organization_score, editor_coverage_score

### Ablation 4: No Outline Refinement Using Conversation Feedback
- **Ablated Part**: The outline curation stage that refines the initial draft outline using the simulated conversations
- **Action**: REMOVE
- **Metrics**: heading_soft_recall, heading_entity_recall, editor_organization_score, editor_coverage_score

### Ablation 5: Vary Number of Conversation Rounds
- **Ablated Part**: The fixed limit on conversation rounds (M) in the multi-turn conversation simulation
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 3
  - 5
- **Metrics**: heading_soft_recall, heading_entity_recall, editor_organization_score, editor_coverage_score

</div>