<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/DivScene__Benchmarking_LVLMs_for_Object_Navigation_with_Diverse_Scenes_and_Objects

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "DivScene: Benchmarking LVLMs for Object Navigation with Diverse Scenes and Objects" introduces the DivScene and DivTraj datasets and the NATVLM agent, which fine-tunes an LVLM (Idefics 2) using imitation learning on BFS shortest paths and incorporates Chain-of-Thought (CoT) explanations.

The paper includes several ablation studies:
1.  **Efficacy of CoT:** Comparing NATVLM with and without CoT explanation traces (Table 2). This shows CoT is crucial.
2.  **Position Comparison Method:** Analyzing different ways of handling positional information, including providing gold labels in the input (Table 2). This suggests the model's internal position calculation might be imperfect.
3.  **Number of Recent Images:** Investigating the impact of providing 2, 4, 6, or 8 recent visual observations (Figure 4, Table 15). They found 4 images to be a good balance.
4.  **Number of Recent Steps:** Examining the effect of providing 4, 8, 12, or 16 steps of recent agent status (position, rotation, action) (Table 3, Table 13). They found 8 steps to be optimal.
5.  **Few-shot Learning:** Evaluating performance with varying proportions of the training data (Table 4, Table 14).

Based on the method description and existing ablations, here are two important missing ablation studies:

1.  **LVLM Backbone Comparison (Fine-tuned):** The paper uses Idefics 2 (8B) as the base LVLM for NATVLM. While they compare NATVLM against *untuned* open-source and API-based LVLMs as baselines (Table 1), they do not show if their fine-tuning approach (IL on BFS paths with CoT) is effective across different LVLM architectures. Fine-tuning other strong open-source LVLMs used as baselines (like Llava 1.5 13B or Qwen-VL 7B) using the same NATVLM method would demonstrate the generalizability of their training approach and highlight whether the performance is specifically tied to Idefics 2 or is a broader benefit of fine-tuning LVLMs for this task. This is a major component of the method (the choice of the base model).

2.  **Spatial Input Ablation:** The instruction template (Table 9) provides detailed spatial information, including the target object type and its absolute position, the agent's absolute position and rotation, and crucially, the recommended grid destination and its rotation from the BFS planner. While they ablate how position difference is handled *within* the CoT or as a gold *input*, they don't ablate the *structure* or *completeness* of the spatial information provided in the main instruction. Removing or altering parts of this spatial input (e.g., removing the recommended grid position/rotation hint from the BFS planner) would help understand the agent's reliance on this specific guidance versus its ability to infer navigation goals from the target object type/position and visual observations alone. This is a key part of the agent's input representation.

These two ablations are important because they investigate the impact of the core model choice and the specific way spatial information is provided, both of which are fundamental to the NATVLM agent's design.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### LVLM Backbone Comparison (Fine-tuned)
- **Ablated Part**: Choice of LVLM backbone for fine-tuning
- **Action**: REPLACE
- **Replacement**: 
  - Llava 1.5 (13B)
  - Qwen-VL (7B)
- **Metrics**: SR, SPL, SEL

### Spatial Input Ablation (Recommended Grid Hint)
- **Ablated Part**: Recommended grid destination and rotation from BFS planner in the instruction
- **Action**: REMOVE
- **Metrics**: SR, SPL, SEL

</div>