<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/I_Want_to_Break_Free__Persuasion_and_Anti_Social_Behavior_of_LLMs_in_Multi_Agent_Settings_with_Social_Hierarchy

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper investigates persuasion and anti-social behavior in LLM agents within a simulated prison environment characterized by social hierarchy. The experimental setup involves a guard agent and a prisoner agent interacting through a custom toolkit (`zAImbardo`) using structured prompts. The study explores the impact of different LLMs, prisoner goals (Yard Time vs. Escape), agent personalities (Abusive/Respectful/Blank Guard, Rebellious/Peaceful/Blank Prisoner), research oversight disclosure, and risks disclosure on persuasion success and anti-social behavior (toxicity, harassment, violence).

The paper already performs several implicit "ablation" studies by comparing:
1.  Different LLMs.
2.  Different prisoner goals.
3.  Different combinations of agent personalities.
4.  The presence or absence of research oversight disclosure.
5.  The presence or absence of risks disclosure.

Key findings highlight the influence of LLM choice, prisoner goal (on persuasion), and especially guard personality (on both persuasion and anti-social behavior). They also note that anti-social behavior emerges even with blank personalities and that some models fail to maintain roles. The temporal analysis and Granger causality tests suggest anti-social behavior is not primarily driven by turn-by-turn interaction dynamics but rather by inherent agent characteristics/prompts.

Based on the methodology and findings, two important missing ablation studies could provide further insight:

1.  **Ablation of Core Prompt Sections:** The paper uses a modular prompt structure including "Communication Rules" and "Environment Description" shared between agents. These sections are fundamental to defining the interaction space and rules. Ablating (removing) one or more of these core shared sections would help understand the extent to which the observed behaviors (especially role adherence, conversation flow, and baseline anti-sociality) are driven by these explicit instructions versus the LLMs' inherent capabilities and training data biases related to the roles/scenario. Given that some models failed due to role switching, testing the impact of removing explicit communication rules seems particularly relevant.
2.  **Ablation of Decoding Strategy:** The paper uses a specific stochastic decoding strategy (Temperature 0.7, Top-k 40, Top-p 0.9). The decoding strategy significantly influences the variability and nature of the generated text. Comparing the results with a deterministic strategy (like greedy decoding) or a different stochastic setting (e.g., higher temperature for more variability) would reveal how the generation process itself impacts the emergence of persuasion attempts, anti-social language, and overall conversation dynamics. This is a standard ablation for generative model behavior studies.

These two ablations are chosen because they target fundamental aspects of the experimental setup: the explicit instructions given to the agents (prompt structure) and the mechanism by which the agents generate responses (decoding strategy). Understanding their influence is crucial for interpreting the observed social dynamics and attributing behaviors to either the prompt design or the LLMs' internal workings.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation of Communication Rules Prompt Section
- **Ablated Part**: The 'Communication Rules' section in the shared prompt template
- **Action**: REMOVE
- **Metrics**: Persuasion Success, Persuasion Turn, Toxicity (%), Toxicity (Avg), Harassment (%), Harassment (Avg), Violence (%), Violence (Avg), Conversation Failure Rate

### Ablation of Decoding Strategy
- **Ablated Part**: The stochastic decoding hyperparameters (Temperature, Top-k, Top-p)
- **Action**: REPLACE
- **Replacement**: 
  - Greedy Decoding (Temp=0, Top-k=1, Top-p=0)
  - Higher Temperature (Temp=1.0, Top-k=40, Top-p=0.9)
- **Metrics**: Persuasion Success, Persuasion Turn, Toxicity (%), Toxicity (Avg), Harassment (%), Harassment (Avg), Violence (%), Violence (Avg), Conversation Failure Rate

</div>