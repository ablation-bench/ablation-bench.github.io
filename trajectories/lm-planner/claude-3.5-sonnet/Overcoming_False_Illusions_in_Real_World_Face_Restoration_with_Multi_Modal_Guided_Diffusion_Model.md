<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/Overcoming_False_Illusions_in_Real_World_Face_Restoration_with_Multi_Modal_Guided_Diffusion_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents MGFR, a multi-modal guided face restoration method that uses text prompts, reference images, and identity information. The authors already conducted several ablation studies including:

1. Impact of training data size (Table 6)
2. Effect of information exchange links between components (Table 3)
3. Impact of negative prompts and hyperparameters (Section 4.4)
4. Ablation on identity embedding (Figure 15)
5. Single vs Dual Control Adapter comparison (Figure 32)

However, there are two critical ablation studies missing that would help better understand the method's key components:

1. The dual-control adapter's two-stage training strategy is a major contribution, but there's no ablation showing its necessity compared to joint training of both stages. This would help validate the authors' claim that separate training is needed to handle complex text information.

2. The paper uses multiple types of prompts (attribute, negative quality, negative attribute) but doesn't ablate the relative importance of each type. Understanding which prompt types contribute most to performance would be valuable for practitioners.

These ablations would provide important insights into the method's key design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Two-Stage vs Joint Training
- **Ablated Part**: two-stage training strategy of dual-control adapter
- **Action**: REPLACE
- **Replacement**: 
  - joint training of both stages
- **Metrics**: LPIPS, ManIQA, ClipIQA, MUSIQ

### Prompt Type Importance
- **Ablated Part**: different types of prompts
- **Action**: REMOVE
- **Metrics**: LPIPS, ManIQA, ClipIQA, MUSIQ

</div>