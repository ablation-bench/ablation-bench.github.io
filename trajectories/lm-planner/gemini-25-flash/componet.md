<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/componet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 ablation studies for the paper "Self-Composing Policies for Scalable Continual Reinforcement Learning". I need to identify the key components of the CompoNet architecture and propose modifications (REMOVE, REPLACE, ADD) to understand their contribution to the method's performance, knowledge transfer, forgetting avoidance, and scalability.

Based on the abstract and Section 4 (Model Architecture), the core components are:
1.  The modular, growable architecture (adding a new module per task).
2.  The self-composing mechanism within each module, which takes the current state and the outputs of *all* previous policy modules as input.
3.  The specific structure of the self-composing module:
    *   Output Attention Head: Attends to previous policy outputs to propose a tentative output `v`.
    *   Input Attention Head: Attends to previous policy outputs and `v` to provide context.
    *   Internal Policy: A feed-forward network that processes the state and input attention output, and *adds* its output to `v` to produce the final module output.
4.  The state encoding strategy (per-module vs. shared).

I will prioritize ablations that target the novel self-composition mechanism and its specific implementation details, as these are the main contributions.

1.  **Ablate the Internal Policy:** The Internal Policy is described as crucial for adjusting/overwriting the attention output, enabling learning from scratch when previous policies are irrelevant. Removing it would test if the module can function purely by combining previous policies via attention. This directly tests a key functional part of the module.
2.  **Replace Attention Mechanisms:** The paper highlights the use of attention for selective composition. Replacing the attention heads with a simpler mechanism (like concatenation followed by a feed-forward network) would test if the *attention* specifically is necessary for effective composition, or if any function over the inputs suffices.
3.  **Change Combination Method:** The Internal Policy's output is *added* to the tentative vector `v`. This resembles a residual connection. Changing this to a different combination (e.g., replacing `v` entirely, or gating) would test the importance of this specific additive structure.
4.  **State Encoding Strategy:** For visual tasks, the paper mentions per-module encoders as the default but also suggests a shared encoder. Ablating this choice is important for understanding the practical scalability and performance implications, especially as the number of tasks grows.

These four ablations cover the core self-composition logic, the specific mechanism (attention), the output combination, and a practical architectural choice. They are distinct and target key aspects of the proposed method. The relevant metrics mentioned in the paper are Performance (Average Return/Success Rate), Memory Cost, and Inference Time.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Internal Policy
- **Ablated Part**: Internal Policy block within each self-composing module
- **Action**: REMOVE
- **Metrics**: Performance (Average Return/Success Rate), Memory Cost, Inference Time

### Feed-forward Composition
- **Ablated Part**: Attention mechanisms (Output and Input Attention Heads) within each module
- **Action**: REPLACE
- **Replacement**: 
  - Feed-forward network processing concatenated inputs (state encoding, previous policy outputs, tentative vector v)
- **Metrics**: Performance (Average Return/Success Rate), Memory Cost, Inference Time

### Internal Policy Replaces v
- **Ablated Part**: Combination method of Internal Policy output and Output Attention tentative vector v
- **Action**: REPLACE
- **Replacement**: 
  - Internal Policy output replaces the tentative vector v instead of being added to it
- **Metrics**: Performance (Average Return/Success Rate), Memory Cost, Inference Time

### Shared State Encoder
- **Ablated Part**: Per-module state encoders (for visual tasks)
- **Action**: REPLACE
- **Replacement**: 
  - Single shared state encoder across all modules
- **Metrics**: Performance (Average Return/Success Rate), Memory Cost, Inference Time

</div>