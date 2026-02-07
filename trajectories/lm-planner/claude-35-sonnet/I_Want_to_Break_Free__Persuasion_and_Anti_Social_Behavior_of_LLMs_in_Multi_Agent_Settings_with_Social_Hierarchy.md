<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/I_Want_to_Break_Free__Persuasion_and_Anti_Social_Behavior_of_LLMs_in_Multi_Agent_Settings_with_Social_Hierarchy

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper studies interactions between LLM agents in a prison setting, focusing on persuasion and anti-social behavior. The key components of their method are:

1. The prompt structure with shared and private sections
2. The personality types assigned to agents (abusive/respectful for guards, rebellious/peaceful for prisoners)
3. The goals assigned to prisoners (yard time vs escape)
4. The research oversight and risk disclosure sections

Looking at the existing ablations:
- They tested different LLM models
- They tested different personality combinations
- They tested different goals
- They tested with/without research oversight and risk disclosure

Key missing ablations:

1. The prompt structure itself is never ablated. The authors use a fixed structure with shared and private sections, but don't test if this specific structure is important vs alternatives.

2. The communication rules section is fixed but could significantly impact the interactions. The authors don't test variations in how agents are instructed to communicate.

I'll focus on these two as the most important missing ablations since they relate to core design choices that could meaningfully impact the results.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Prompt Structure Ablation
- **Ablated Part**: The division of prompts into shared and private sections
- **Action**: REPLACE
- **Replacement**: 
  - Single combined prompt without section divisions
  - Fully separate prompts with no shared information
- **Metrics**: Persuasion success rate, % of toxic messages, % of harassment messages, % of violent messages

### Communication Rules Ablation
- **Ablated Part**: The communication rules section specifying how agents should interact
- **Action**: REPLACE
- **Replacement**: 
  - No communication rules
  - Minimal rules (just turn-taking)
  - Expanded rules with more specific interaction guidelines
- **Metrics**: Persuasion success rate, % of toxic messages, % of harassment messages, % of violent messages

</div>