<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/DPO_Diff__On_Discrete_Prompt_Optimization_of_Text_to_Image_Diffusion_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After analyzing the paper, I'll suggest missing ablation studies focusing on the major components of DPO-Diff. First, let me identify the key components and existing ablations:

Key components:
1. Shortcut Gradient computation
2. Compact domain spaces (Antonym Space for negative prompts, Synonym Space for positive prompts)
3. Evolution Search strategy

The paper already includes:
- Ablation comparing different search algorithms (Section 6.1)
- Ablation comparing negative vs positive prompt optimization (Section 6.2)

Missing Important Ablations:
1. The most critical missing ablation is on the Shortcut Gradient component. While the paper introduces this as a major contribution for efficient backpropagation through diffusion steps, there's no ablation studying how different K values affect the performance. The paper only mentions using K=1 because it "produces effective supervision signals" but doesn't validate this empirically.

2. Another important missing ablation is on the size of the compact domain spaces. The paper mentions using "at most 5 substitutes" for each word but doesn't justify this choice or explore how different vocabulary sizes affect the optimization process.

I'll focus on these two missing ablations as they target core components of the method that directly impact its effectiveness and efficiency.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Shortcut Gradient Steps Ablation
- **Ablated Part**: number of steps K in Shortcut Gradient computation
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 5
  - 10
  - 25
  - 50
- **Metrics**: clip_loss, memory usage, runtime

### Compact Space Size Ablation
- **Ablated Part**: number of word substitutes in compact domain spaces
- **Action**: REPLACE
- **Replacement**: 
  - 3
  - 5
  - 10
  - 15
- **Metrics**: clip_loss, search time

</div>