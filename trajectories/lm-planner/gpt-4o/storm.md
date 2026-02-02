<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/storm

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper presents STORM, a system designed to assist in writing Wikipedia-like articles by automating the pre-writing stage. The system is built on three main components: discovering diverse perspectives, simulating conversations for question asking, and creating an outline. The evaluation is based on a dataset called FreshWiki, and the system is compared against a baseline in terms of organization and coverage.

To design ablation studies, we should focus on the key components of STORM and their contributions to the overall performance. The main components to consider are the perspective-guided question asking, the simulation of conversations, and the outline creation process. Each of these components plays a crucial role in the system's ability to generate well-organized and comprehensive articles.

1. **Perspective-Guided Question Asking**: This component is responsible for generating diverse perspectives that guide the question-asking process. Ablating this part would help understand its impact on the quality of the questions and the resulting outline.

2. **Simulating Conversations**: This component involves simulating multi-turn conversations to generate questions and gather information. Ablating this part would reveal its importance in refining the questions and ensuring the information is comprehensive.

3. **Outline Creation**: The process of creating an outline from the gathered information is crucial for the final article's structure. Ablating this part would show how much the outline contributes to the article's organization and coverage.

4. **Use of Trusted Sources**: The system relies on trusted sources for grounding the answers. Ablating this part would help understand the impact of source reliability on the article's factual accuracy.

5. **Draft Outline Generation**: The initial draft outline is generated using the LLM's internal knowledge. Ablating this part would show the importance of the draft outline in the final outline's quality.

Each ablation study will focus on one of these components, either by removing it or replacing it with a simpler or alternative method. The metrics to report will include the ones used in the paper, such as organization, coverage, heading soft recall, and heading entity recall.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation 1: Perspective-Guided Question Asking
- **Ablated Part**: Perspective-guided question asking component
- **Action**: REMOVE
- **Metrics**: organization, coverage, heading soft recall, heading entity recall

### Ablation 2: Simulating Conversations
- **Ablated Part**: Simulated conversations for question asking
- **Action**: REMOVE
- **Metrics**: organization, coverage, heading soft recall, heading entity recall

### Ablation 3: Outline Creation
- **Ablated Part**: Outline creation process
- **Action**: REMOVE
- **Metrics**: organization, coverage, heading soft recall, heading entity recall

### Ablation 4: Use of Trusted Sources
- **Ablated Part**: Use of trusted sources for grounding answers
- **Action**: REMOVE
- **Metrics**: organization, coverage, heading soft recall, heading entity recall

### Ablation 5: Draft Outline Generation
- **Ablated Part**: Initial draft outline generation using LLM's internal knowledge
- **Action**: REMOVE
- **Metrics**: organization, coverage, heading soft recall, heading entity recall

</div>