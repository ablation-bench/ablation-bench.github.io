<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Knowledge_Accumulating_Contrastive_Prompt_for_Continual_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper proposes a novel prompt‐based continual learning method by accumulating knowledge in a single prompt using contrastive learning. While the ablations included study of prompt length and the trade-off parameter λprev, two key design choices remain unexplored. First, the method updates the previous prompt by hard replacement after each task. An ablation study exploring different update mechanisms (e.g., replacing it with an exponential moving average update using various smoothing factors) would help quantify if a gradual accumulation of past knowledge rather than a hard overwrite can better balance plasticity and stability. Second, the paper follows the DualPrompt setting for inserting prompts into a fixed set of layers, but it does not investigate how the location or number of layers where the prompt is inserted may affect performance. Testing prompt insertion in only early, middle, or later layers (or in all layers) could provide insights into whether the choice of insertion stage influences the feature alignment and forgetting properties. These two ablation studies are critical for understanding the sensitivity of the method to its accumulation update mechanism and network integration design.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Prompt Update Mechanism
- **Ablated Part**: The prompt accumulation update strategy (current hard replacement of the previous prompt)
- **Action**: REPLACE
- **Replacement**: 
  - hard replacement
  - EMA update with α=0.1
  - EMA update with α=0.5
  - EMA update with α=0.9
- **Metrics**: Average Accuracy, Forgetting

### Ablation: Prompt Insertion Scheme
- **Ablated Part**: The layers in the network where the prompt is inserted
- **Action**: REPLACE
- **Replacement**: 
  - insert prompt in early layers only
  - insert prompt in middle layers only
  - insert prompt in later layers only
  - insert prompt in all layers
- **Metrics**: Average Accuracy, Forgetting

</div>