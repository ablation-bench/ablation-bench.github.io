<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/On_Pre_training_Language_Model_for_Antibody

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

One key missing ablation involves the input representation of the antibody. Currently the model “expands the CDR fragment to the full antibody” without comparing if the extra context in the full sequence helps or hurts performance. We propose to perform an ablation comparing the use of the complete antibody sequence versus using only the CDR regions. This experiment would shed light on the importance of the framework regions compared to the highly variable binding sites, and its effect may vary across tasks with different specificity (e.g., antigen binding, paratope prediction, and B cell classification). 

Another missing ablation study focuses on how the germline is integrated with the antibody sequence. The method presently concatenates the antibody with its corresponding germline (using a [SEP] token) for joint encoding. However, it remains unclear whether this is the optimal strategy to capture the evolutionary relationship. An alternative is to encode the antibody and its germline separately using a dual encoder design and then fuse their representations. Comparing these two strategies would reveal the contribution of cross-sequence interactions versus separate modeling of the two components.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Input Scope Ablation
- **Ablated Part**: The representation input: full antibody sequence vs. CDR-only regions
- **Action**: REPLACE
- **Replacement**: 
  - Full Antibody Sequence
  - CDR-only Sequence
- **Metrics**: AUC, F1, MCC, ACC

### Germline Encoding Strategy Ablation
- **Ablated Part**: Germline incorporation mechanism: concatenated joint encoding vs. dual encoder architecture
- **Action**: REPLACE
- **Replacement**: 
  - Concatenation (joint encoding)
  - Dual encoder (separate encoding with late fusion)
- **Metrics**: AUC, F1, MCC, ACC

</div>