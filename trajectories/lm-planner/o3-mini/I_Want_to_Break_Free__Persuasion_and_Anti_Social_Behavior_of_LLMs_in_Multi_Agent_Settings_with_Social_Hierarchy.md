<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/I_Want_to_Break_Free__Persuasion_and_Anti_Social_Behavior_of_LLMs_in_Multi_Agent_Settings_with_Social_Hierarchy

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

We propose two missing ablation studies that would further clarify how design choices affect both persuasion and anti‐social behavior in the simulated multi-agent interactions.

The first ablation study targets the fixed conversational turn order. In the current method the conversation is tightly structured (with the guard always speaking 10 messages and the prisoner 9), reinforcing a power dynamic that may be driving both persuasion outcomes and the emergence of toxic language by the guard. By replacing this fixed structure with alternative turn-taking protocols (such as equal number of turns, reversing the order, or a randomized turn order), one can assess how much the specific ordering contributes to the observed effects. Here, the evaluation would focus on metrics like persuasion success rate, the turn when persuasion is achieved, as well as anti‐social behavior outcomes (toxicity, harassment, violence) and error rates related to role adherence.

The second ablation study addresses the explicit role instructions embedded in the prompt. Currently, both agents receive structured starting prompts and personality cues that clearly assign them roles (guard or prisoner) and behavioral expectations. Although the experiments already vary personality via different options (blank, abusive, respectful, rebellious, peaceful), all experiments include an explicit role declaration. Removing these explicit cues entirely would help understand if the emergent behaviors (including role switching errors and anti-social output) are primarily driven by the underlying LLM biases or are a product of explicit instructions. The outcome metrics would again include persuasion success, the frequency of role switching errors, and multiple anti-social behavior measures.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Turn Order Ablation
- **Ablated Part**: Fixed conversation turn-taking structure (guard sending 10 messages and prisoner sending 9) that enforces a power dynamic.
- **Action**: REPLACE
- **Replacement**: 
  - Equal turns for both agents
  - Reversed turn order (prisoner starts and/or ends)
  - Randomized turn order
- **Metrics**: persuasion success rate, turn of persuasion achievement, percentage of toxic messages, harassment score, violence score, role adherence error rate

### Role Prompt Removal Ablation
- **Ablated Part**: Explicit role and personality instructions in the starting prompt and private sections that assign agents as guard or prisoner.
- **Action**: REMOVE
- **Metrics**: persuasion success rate, incidence of role switching errors, percentage of toxic messages, harassment score, violence score

</div>