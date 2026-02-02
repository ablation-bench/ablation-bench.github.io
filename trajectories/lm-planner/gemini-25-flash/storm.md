<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-25-flash/storm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user wants a list of up to 5 ablation studies for the STORM system described in the paper "Assisting in Writing Wikipedia-like Articles From Scratch with Large Language Models". The goal is to identify key components of the method and propose experiments to understand their contribution to the overall performance.

I have analyzed the paper, focusing on Section 3 (Method) and Section 2 (Task), to understand the core components of STORM and the evaluation metrics used.

The main components of STORM are:
1.  Discovering diverse perspectives.
2.  Simulating multi-turn, grounded conversations for each perspective.
3.  Creating an outline by refining a draft using conversation data.
4.  Writing the article using the outline and collected references.

The evaluation metrics mentioned are:
*   Outline quality: Heading soft recall, Heading entity recall.
*   Article quality (human evaluation): Organized, Broad in coverage.

Based on these components and metrics, I have identified several potential ablation studies:

1.  **Ablating the multi-perspective approach:** This is a central idea of STORM. Removing the diverse perspectives and only using a basic one would show the value of this component.
2.  **Ablating the iterative conversation:** The multi-turn conversation is highlighted as important for asking in-depth questions. Replacing it with a single-turn approach would test the benefit of iteration.
3.  **Ablating the outline refinement:** STORM uses a two-step process for outline generation. Testing an alternative, like generating the outline directly from the conversation data, would evaluate the refinement step.
4.  **Varying the number of perspectives:** A parameter study on the number of perspectives (N) would show how sensitive the performance is to this choice.
5.  **Varying the conversation length:** A parameter study on the maximum number of conversation rounds (M) would show the impact of conversation depth.
6.  **Ablating source filtering:** Removing the filtering of untrustworthy sources would test its importance, especially regarding potential bias transfer mentioned in the paper.

I will select the top 5 most important ablations, prioritizing those that test the core novelties and key parameters of the system. The multi-perspective approach and the iterative conversation are the most prominent features. The outline refinement is specific to the pre-writing stage evaluation. Varying the key parameters (number of perspectives and conversation length) are also important to understand the system's design choices. Ablating source filtering is interesting, but perhaps slightly less central to the core *process* of question asking and outline generation compared to the others, although it's crucial for groundedness.

Therefore, the top 5 ablations are:
1.  Removing diverse perspectives.
2.  Replacing multi-turn conversation with single-turn.
3.  Replacing the two-step outline generation with a direct approach.
4.  Varying the number of perspectives.
5.  Varying the conversation length.

I will now format these into the required JSONL structure, ensuring the correct fields and metrics are used. For ablations affecting the information gathering process (1, 2, 4, 5), I will include both outline and human evaluation metrics. For the ablation primarily affecting the outline structure (3), I will focus on the outline metrics.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### No Diverse Perspectives
- **Ablated Part**: Discovery and utilization of diverse perspectives (using only the basic fact writer perspective)
- **Action**: REMOVE
- **Metrics**: Heading soft recall, Heading entity recall, Organized (human eval), Broad in coverage (human eval)

### Single-Turn Question Asking
- **Ablated Part**: Multi-turn simulated conversations for iterative question asking
- **Action**: REPLACE
- **Replacement**: 
  - Single-turn question asking per perspective
- **Metrics**: Heading soft recall, Heading entity recall, Organized (human eval), Broad in coverage (human eval)

### Outline Generation Strategy
- **Ablated Part**: Two-step outline generation (draft from topic + refinement from conversations)
- **Action**: REPLACE
- **Replacement**: 
  - Generate outline directly from simulated conversations
- **Metrics**: Heading soft recall, Heading entity recall

### Number of Perspectives
- **Ablated Part**: Number of diverse perspectives (N)
- **Action**: REPLACE
- **Replacement**: 
  - N=0 (only basic)
  - N=2
  - N=5
  - N=10
- **Metrics**: Heading soft recall, Heading entity recall, Organized (human eval), Broad in coverage (human eval)

### Conversation Length
- **Ablated Part**: Maximum number of conversation rounds (M)
- **Action**: REPLACE
- **Replacement**: 
  - M=1
  - M=3
  - M=5
- **Metrics**: Heading soft recall, Heading entity recall, Organized (human eval), Broad in coverage (human eval)

</div>