<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Duolando__Follower_GPT_with_Off_Policy_Reinforcement_Learning_for_Dance_Accompaniment

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Duolando: Follower GPT with Off-Policy Reinforcement Learning for Dance Accompaniment" presents a novel task of dance accompaniment, where a follower's dance motion is generated in response to a leader's dance motion and music. The authors propose a GPT-based model, Duolando, which uses off-policy reinforcement learning to improve its performance. The model is trained on a large-scale duet dance dataset, DD100, which is also introduced in the paper.

The paper presents several ablation studies to evaluate the effectiveness of different components of the model. However, there are some missing ablation studies that could provide further insights into the model's performance.

One potential ablation study is to investigate the impact of the music input on the model's performance. The paper mentions that the music input is used to condition the follower's motion, but it would be interesting to see how the model performs without music input or with different types of music input.

Another potential ablation study is to evaluate the effectiveness of the off-policy reinforcement learning component. The paper mentions that the off-policy reinforcement learning helps to improve the model's performance, but it would be interesting to see how the model performs without this component or with different reinforcement learning algorithms.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: Music Input
- **Action**: REMOVE
- **Metrics**: FIDk, FIDg, Divk, Divg, FIDcd, Divcd, CF, BED, BAS

### Ablation B
- **Ablated Part**: Off-Policy Reinforcement Learning
- **Action**: REPLACE
- **Replacement**: 
  - On-Policy Reinforcement Learning
  - No Reinforcement Learning
- **Metrics**: FIDk, FIDg, Divk, Divg, FIDcd, Divcd, CF, BED, BAS

</div>