<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/smoothnet

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 important ablation studies for the SmoothNet paper, formatted as JSONL. I need to identify the key components of the SmoothNet method and propose experiments to evaluate their contribution. The paper highlights its temporal-only nature, the use of FCNs, the motion-aware design (incorporating velocity and acceleration), and the specific loss function. The key evaluation metrics mentioned are MPJPE (Mean Per Joint Position Error) and Accel (Mean Per Joint Acceleration Error).

Based on the paper's description, the most critical aspects to investigate through ablation are:

1.  **The choice of FCNs as the temporal backbone:** The paper argues FCNs are better suited than TCNs or Transformers for this specific temporal smoothing task. Ablating this involves replacing the FCN with these alternatives.
2.  **The motion-aware design:** The paper introduces velocity and acceleration streams as an enhancement over a basic position-only model. Ablating this involves removing these streams to see their impact.
3.  **The acceleration loss component:** The loss function combines position and acceleration terms. Ablating the acceleration loss helps understand its specific contribution to smoothness and potential trade-offs with position accuracy.
4.  **The temporal receptive field (window size):** The sliding window size $T$ determines the temporal context the network sees. Varying this hyperparameter is a standard and important ablation for temporal models.

These four ablations cover the core architectural choice, the main proposed enhancement, the training objective, and a crucial hyperparameter. They are ranked by their perceived importance in validating the paper's claims about the SmoothNet design. I will include MPJPE and Accel as metrics for all ablations, as they are the primary evaluation metrics used in the paper.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Temporal Architecture Comparison
- **Ablated Part**: FCN temporal backbone
- **Action**: REPLACE
- **Replacement**: 
  - TCN
  - Transformer
- **Metrics**: MPJPE, Accel

### Motion-Aware Streams Contribution
- **Ablated Part**: Velocity and acceleration input streams
- **Action**: REMOVE
- **Metrics**: MPJPE, Accel

### Acceleration Loss Contribution
- **Ablated Part**: L1 loss on acceleration (L_acc)
- **Action**: REMOVE
- **Metrics**: MPJPE, Accel

### Temporal Window Size
- **Ablated Part**: Sliding window size (T)
- **Action**: REPLACE
- **Replacement**: 
  - Smaller T
  - Larger T
- **Metrics**: MPJPE, Accel

</div>