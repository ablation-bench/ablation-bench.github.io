<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gpt-4o/An_Empirical_Study_on_Reconstructing_Scientific_History_to_Forecast_Future_Trends

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "An Empirical Study on Reconstructing Scientific History to Forecast Future Trends" introduces a novel framework, HorizonAI, which leverages a dual-system approach to synthesize historical research and predict future trends. The framework utilizes a temporal knowledge graph (PaperTKG) for organizing past research and large language models (LLMs) for reasoning and prediction. The paper presents a comprehensive evaluation using a benchmark called ResBench, focusing on historical completeness and predictive reliability.

The existing ablation studies in the paper focus on the effects of input quality and graph augmentation strategy. The input quality ablation examines the impact of interdisciplinary topics and topic-source paper misalignment on the framework's performance. The graph augmentation strategy ablation evaluates different methods for enhancing the completeness of historical data.

However, there are missing ablation studies that could provide further insights into the framework's components. One potential ablation study could focus on the role of the temporal knowledge graph (PaperTKG) in the framework. By removing or altering the PaperTKG, we can assess its impact on the historical summarization and future prediction tasks. Another potential ablation study could investigate the influence of the dual-system approach, specifically the interaction between System 1 (PaperTKG) and System 2 (LLMs). By modifying the interaction or replacing one of the systems, we can evaluate the necessity and effectiveness of the dual-system approach.

These ablation studies would help attribute the method's performance to its major components and provide a deeper understanding of the framework's design choices.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation Study on PaperTKG
- **Ablated Part**: Temporal Knowledge Graph (PaperTKG)
- **Action**: REMOVE
- **Metrics**: Graph Completeness, Search Efficiency, Historical Summarization Overlap, Predictive Reliability

### Ablation Study on Dual-System Interaction
- **Ablated Part**: Interaction between System 1 (PaperTKG) and System 2 (LLMs)
- **Action**: REPLACE
- **Replacement**: 
  - Only System 1
  - Only System 2
- **Metrics**: Historical Summarization Overlap, Predictive Reliability

</div>