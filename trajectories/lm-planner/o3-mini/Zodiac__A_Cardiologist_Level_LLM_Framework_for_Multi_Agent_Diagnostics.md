<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Zodiac__A_Cardiologist_Level_LLM_Framework_for_Multi_Agent_Diagnostics

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper already shows ablations that remove fine-tuning, in-context learning, and fact-checking; as well as a single-agent variant to highlight the need for multi-agent collaboration. However, two key design choices have not been ablated. First, ZODIAC’s strength stems from its multi-modal input where both tabular metrics and ECG tracings are used. No study was reported on the isolated contribution of each modality. An ablation that replaces the joint multi-modal input with only one of the modalities (either only tabular metrics or only ECG images) would clarify each modality’s impact on diagnostic accuracy and security. Second, the system uses in-context learning with demonstrations that are carefully selected based on patient demographics and arrhythmia subclass. There is no investigation into how critical this tailored demonstration selection strategy is. Replacing the tailored demos with randomly selected (or mismatched) demonstrations would provide insight into the importance of demographic and clinical matching for in-context learning.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Multi-Modal Input Ablation
- **Ablated Part**: integration of multi-modal data (tabular metrics and ECG tracings) into the diagnostic workflow
- **Action**: REPLACE
- **Replacement**: 
  - only tabular modality
  - only ECG modality
- **Metrics**: ACC, CPL, ORG, CPH, SCI, CNS, FFH, FFB

### In-Context Demo Selection Ablation
- **Ablated Part**: the demonstration selection strategy for in-context learning
- **Action**: REPLACE
- **Replacement**: 
  - random demo selection
  - mismatched demo selection
- **Metrics**: ACC, CPL, ORG, CPH, SCI, CNS, FFH, FFB

</div>