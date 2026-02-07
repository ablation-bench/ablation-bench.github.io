<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Self_Guided_Exploration_for_Automatic_and_Diverse_AI_Supervision

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Self Guided Exploration for Automatic and Diverse AI Supervision" proposes Exploratory AI (EAI), a method for autonomously generating training data using an actor-critic framework inspired by unsupervised reinforcement learning. The core components are an actor model that generates content, a critic model that evaluates novelty and correctness and provides critiques, a replay buffer storing accepted data, and exploration principles guiding the process.

The paper includes several ablation studies:
1.  **Effect of sampled inputs:** Investigates how the number of samples from the replay buffer used to condition the actor impacts performance (Table 2).
2.  **Effect of exploration principles:** Evaluates the contribution of different guiding principles (rephrase, new topic, restructure, new scenario) by removing them individually or in combination (Table 3).
3.  **Effect of critic:** Compares EAI with a version where the critic is removed (EAI w/o critic), demonstrating the overall importance of the critic component (Table 4).
4.  **Scaling with generated data:** Shows how performance changes as the amount of EAI-generated data increases, comparing EAI to RFT (Figure 4).
5.  **Scaling with human annotation size:** Examines EAI's performance when initialized with varying amounts of human data in the replay buffer (Figure 5).

While these ablations cover important aspects, there are a couple of key areas that could benefit from further investigation to fully understand the mechanism and robustness of EAI.

Firstly, the paper mentions that the actor and critic engage in up to two interaction rounds, where the critic provides critiques that guide the actor's subsequent generation attempts (Algorithm 1). The "Effect of critic" ablation shows that the critic *as a whole* is important (evaluation + critique loop). However, it doesn't isolate the impact of the *iterative refinement process* driven by the critique itself. An ablation varying the maximum number of interaction rounds (e.g., 1 round vs. 2 rounds vs. more) would directly quantify the value added by allowing the actor to refine its output based on the critic's feedback. This is a crucial part of the proposed feedback loop.

Secondly, the paper uses different models for the critic (GPT4 when supervising LLaMA2, Vicuna when supervising Vicuna). While Table 1 shows overall performance with these different setups, it's not a clean ablation of the *critic model's capability* while keeping the actor model constant. A dedicated ablation study using the *same* actor model (e.g., Vicuna 13B) but varying the critic model (e.g., Vicuna 13B vs. GPT4) would reveal how much the performance gain depends on the critic being a highly capable, potentially proprietary, model versus a self-supervised open-source model. This is important for understanding the generalizability and accessibility of the EAI approach.

Based on their importance in understanding the core mechanisms and dependencies of EAI, these two ablations are suggested.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Effect of Interaction Rounds
- **Ablated Part**: Number of interaction rounds between actor and critic per generation attempt
- **Action**: REPLACE
- **Replacement**: 
  - 1
  - 2
  - 3
- **Metrics**: GSM8K pass@1, MATH pass@1

### Effect of Critic Model
- **Ablated Part**: Specific language model used for the Critic
- **Action**: REPLACE
- **Replacement**: 
  - Vicuna 13B
  - GPT4
- **Metrics**: GSM8K pass@1, MATH pass@1

</div>