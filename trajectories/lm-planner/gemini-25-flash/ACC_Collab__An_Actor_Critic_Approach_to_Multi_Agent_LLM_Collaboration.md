<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/ACC_Collab__An_Actor_Critic_Approach_to_Multi_Agent_LLM_Collaboration

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "ACC-Collab: An Actor-Critic Approach to Multi-Agent LLM Collaboration" proposes a novel framework for training a two-agent team (Actor and Critic) to collaborate on tasks. The core components include the two distinct agent roles, an iterative discussion process, an actor-critic based learning framework using iterative best-response optimization, a partial trajectory reward estimation, and a novel "Guided-Collaboration" method for generating high-quality training data used with DPO.

The paper presents several experimental results to demonstrate the effectiveness of ACC-Collab. These include comparisons against various multi-agent and single-agent baselines (SoM, Persona, DebateTune, SFT, DebateGPT), analysis of performance improvement over multiple deliberation rounds, per-round accuracy analysis, and an examination of the individual performance of trained agents when paired with untrained counterparts. They also provide a qualitative analysis of the trained critic's responses and measure process accuracy using GPT-4o. The paper also compares ACC-Collab (1 training round) with ACC-Collab+ (2 training rounds), which is an ablation on the number of training iterations.

While the paper provides a good comparison to baselines and analyzes the trained agents individually, there are a couple of key ablation studies missing that would further clarify the contribution of specific components of the ACC-Collab training framework:

1.  **Ablation of Training One Agent:** The paper trains both the Actor and the Critic. While Section 5.3 shows the performance of a *trained* agent paired with an *untrained* agent at inference time, it doesn't show the effect of *only training one* of the agents within the full ACC-Collab training pipeline (which involves alternating updates and data generation using both agents). Training only the Actor (while the Critic remains untrained throughout the training process, but still participates in data generation) or training only the Critic (while the Actor remains untrained) would isolate the contribution of training each specific agent within the collaborative learning setup. This is distinct from the inference-time pairing shown in Section 5.3.
2.  **Ablation of Guided Collaboration Data Generation:** The paper highlights "Guided-Collaboration" as a novel data generation scheme for creating high-quality preference data. An ablation study comparing training using this guided data versus training using data generated from simpler or "natural" deliberation trajectories (e.g., selecting trajectories based on estimated final accuracy without explicit guidance towards/away from the correct answer, as mentioned in Section 4.3) would be crucial to demonstrate the effectiveness and necessity of the proposed guided data generation method.

These two missing ablations are important because they directly test the contribution of the core training components: which agents need to be trained and how the training data should be generated.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Train Only One Agent
- **Ablated Part**: Training of either the Actor or the Critic agent within the ACC-Collab alternating training loop.
- **Action**: REMOVE
- **Metrics**: Final Answer Accuracy, Percent Improvement, Per-Round Accuracy, Process Accuracy

### Natural Data Generation
- **Ablated Part**: Guided Collaboration Trajectory data generation method.
- **Action**: REPLACE
- **Replacement**: 
  - Data generated from natural deliberation trajectories selected by estimated final accuracy
- **Metrics**: Final Answer Accuracy, Percent Improvement, Per-Round Accuracy

</div>