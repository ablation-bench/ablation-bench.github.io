<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/storm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, STORM has several key components that contribute to its performance in generating Wikipedia-like articles:

1. Multi-perspective Question Asking: This is a core innovation where STORM discovers different perspectives to guide question generation, rather than using direct prompting.

2. Simulated Conversations: STORM uses a multi-turn conversation approach between a writer and expert, grounded on trusted sources.

3. Two-stage Outline Creation: The system first generates a draft outline using LLM's internal knowledge, then refines it using collected conversations.

4. Source Filtering: STORM uses a rule-based filter to exclude untrustworthy sources.

The most important ablations should test these key components to understand their contribution to the system's performance. I'll focus on the most critical ones:

1. Testing the value of multi-perspective questioning vs. single perspective
2. Evaluating the importance of the two-stage outline creation
3. Assessing the impact of conversation turns
4. Testing the value of source filtering

The metrics should align with those used in the paper: organization quality, breadth of coverage, and factual accuracy.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Single Perspective Ablation
- **Ablated Part**: Multi-perspective question asking component
- **Action**: REPLACE
- **Replacement**: 
  - single general perspective
  - random single perspective
- **Metrics**: organization quality, breadth of coverage, factual accuracy

### Direct Outline Generation
- **Ablated Part**: Two-stage outline creation process
- **Action**: REPLACE
- **Replacement**: 
  - single-stage direct outline generation
  - outline generation from conversations only
- **Metrics**: organization quality, breadth of coverage

### Conversation Depth
- **Ablated Part**: Multi-turn conversation
- **Action**: REPLACE
- **Replacement**: 
  - single-turn QA
  - two-turn conversation
  - five-turn conversation
- **Metrics**: factual accuracy, breadth of coverage

### Source Filter Removal
- **Ablated Part**: Rule-based source filtering
- **Action**: REMOVE
- **Metrics**: factual accuracy, source quality

</div>