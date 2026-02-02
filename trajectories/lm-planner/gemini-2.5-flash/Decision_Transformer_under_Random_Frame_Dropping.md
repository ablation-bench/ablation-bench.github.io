<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Decision_Transformer_under_Random_Frame_Dropping

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Decision Transformer under Random Frame Dropping" proposes DeFog, an offline reinforcement learning algorithm robust to frame dropping. DeFog builds upon the Decision Transformer architecture and introduces three main components to handle frame dropping: 1) train-time frame dropping by masking observations/rewards in the offline dataset, 2) a drop-span embedding to indicate the duration of dropped frames, and 3) a freeze-trunk finetuning stage.

The paper includes several ablation studies (Section 4.5 and Appendix C) investigating:
- The effectiveness of the explicit drop-span embedding compared to an implicit method and removing it.
- The impact of the freeze-trunk finetuning stage and finetuning individual components.
- The necessity of the Decision Transformer backbone by comparing to TD3+BC on masked data.
- The effect of predicting state/reward tokens.
- Different aspects of the train-time frame dropping scheme, such as mask update interval, placeholder strategy for dropped frames, the random process for dropping, and whether to drop actions.

While these ablations cover many aspects, a key hyperparameter in the train-time frame dropping and finetuning stages is the *probability* of dropping frames (p<sup>d</sup>). The paper uses specific, sometimes different, values for p<sup>d</sup> during training and finetuning across different environments and datasets (Tables 3 and 5), but it does not systematically ablate the impact of choosing different values for these drop rates.

Understanding how the training drop rate (p<sup>d</sup> during the main training phase) affects the model's ability to generalize to various test-time drop rates is crucial. Does training with a very high drop rate make it robust across the board, or is there an optimal training drop rate? Similarly, the finetuning stage is designed to boost performance at higher drop rates, and the drop rate used *during* finetuning is a critical factor. Ablating this parameter would clarify its role and guide hyperparameter selection.

Therefore, two important missing ablation studies are:
1.  Ablating the probability of dropping frames during the main training stage.
2.  Ablating the probability of dropping frames during the freeze-trunk finetuning stage.

These ablations would provide valuable insights into how the core training and finetuning mechanisms contribute to robustness and how to best configure them. The primary metric used throughout the paper for evaluating performance under frame dropping is the average return across different test-time drop rates, which should be used here as well.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Train Drop Rate Ablation
- **Ablated Part**: Probability of dropping frames during the main training stage (p_d)
- **Action**: REPLACE
- **Replacement**: 
  - 0.2
  - 0.5
  - 0.8
  - 0.9
- **Metrics**: Average Return under different test-time drop rates (0% to 90%)

### Finetune Drop Rate Ablation
- **Ablated Part**: Probability of dropping frames during the freeze-trunk finetuning stage (p_d)
- **Action**: REPLACE
- **Replacement**: 
  - 0.8
  - 0.9
  - 0.95
- **Metrics**: Average Return under different test-time drop rates (0% to 90%)

</div>