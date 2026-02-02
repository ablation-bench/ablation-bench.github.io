<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Beyond_Joint_Demonstrations__Personalized_Expert_Guidance_for_Efficient_Multi_Agent_Reinforcement_Learning

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper’s key innovation is using personalized expert demonstrations to guide exploration through intrinsic reward shaping in a decentralized MARL setting. One central component is the personalized reward shaping module (via occupancy matching in EG‐MARL and the discriminator in GEG‐MARL) which is critical for bootstrapping the learning process. However, the paper does not report an ablation study that isolates the contribution of this module. Removing or “disabling” the reward-shaping component (e.g. by setting the weight η to 0) would highlight its impact on performance (e.g. in terms of average episodic reward, convergence speed, and overall task completion rate). 

A second important yet missing ablation is related to the decentralized critic update mechanism. In Algorithm 1, the agents exchange critic parameters with neighboring agents to average their value estimates. This design choice is intended to promote stable decentralized learning and coordination. However, the paper does not study the effectiveness of this neighbor communication. Removing the peer averaging step would help quantify its contribution by comparing the convergence properties and cooperative behavior (e.g. collision rate and success rate) against the full model.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Reward Shaping Module Removal
- **Ablated Part**: personalized demonstration-based reward shaping mechanism (intrinsic reward computed via occupancy measure matching or discriminator output)
- **Action**: REMOVE
- **Metrics**: average episodic reward, success rate, convergence rate

### Ablation: Critic Parameter Exchange
- **Ablated Part**: neighbor communication mechanism for critic (value function) parameter averaging
- **Action**: REMOVE
- **Metrics**: average episodic reward, policy convergence, cooperation success rate

</div>