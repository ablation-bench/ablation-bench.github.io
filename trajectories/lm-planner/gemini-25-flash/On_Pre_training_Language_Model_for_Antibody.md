<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/On_Pre_training_Language_Model_for_Antibody

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "On Pre-training Language Model for Antibody" introduces EATLM, a pre-trained antibody language model that incorporates antibody-specific evolutionary information. The core components of EATLM include a Transformer architecture, pre-training on the OAS database using concatenated antibody and germline sequences, and two novel pre-training objectives: Ancestor Germline Prediction (AGP) and Mutation Position Prediction (MPP), in addition to standard Masked Language Modeling (MLM) on the concatenated sequence.

The paper already includes several important ablation studies. Specifically, Table 2 and Table 8 show the performance of EATLM when the AGP objective is removed (EATLM w/o AGP), when the MPP objective is removed (EATLM w/o MPP), and when both are removed (EATLM w/o AGP & MPP). This effectively ablates the contribution of the proposed evolution-aware pre-training tasks. The paper also compares EATLM to various other PPLMs and PALMs, and explores larger model sizes.

However, two potentially important ablation studies are missing:

1.  **Ablation of Germline Input during Pre-training:** EATLM's design fundamentally relies on using the germline sequence alongside the antibody sequence during pre-training, even in the baseline MLM objective (EATLM w/o AGP & MPP still uses the concatenated sequence). An ablation that removes the germline sequence *entirely* from the pre-training input (i.e., pre-training only on antibody sequences, perhaps with standard MLM) would directly assess the benefit of providing the germline context during the initial representation learning phase, independent of the specific AGP and MPP tasks. This would clarify if the germline's value comes from the specific evolution tasks or simply from being present in the input sequence during general language modeling.

2.  **Ablation of Finetuning Strategy:** The paper finetunes the entire pre-trained EATLM model on the downstream tasks. A common practice in transfer learning is to evaluate the quality of the learned representations by freezing the pre-trained backbone and training only a task-specific classification or labeling head. This ablation would reveal whether the pre-trained representations are directly transferable and useful, or if significant adaptation of the entire model is required during finetuning for optimal performance on antibody tasks.

These two missing ablations would provide deeper insights into the contribution of EATLM's specific input structure and the nature of its learned representations for downstream tasks.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### EATLM w/o Germline Input
- **Ablated Part**: Using germline sequence as input during pre-training
- **Action**: REMOVE
- **Metrics**: AUC, F1, MCC, ACC

### EATLM Frozen Backbone
- **Ablated Part**: Finetuning the entire pre-trained model on downstream tasks
- **Action**: REPLACE
- **Replacement**: 
  - Freeze backbone, train head
- **Metrics**: AUC, F1, MCC, ACC

</div>