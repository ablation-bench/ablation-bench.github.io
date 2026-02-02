<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/powerfulpromptft

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The user requested up to 5 ablation studies for the paper "Don't Stop Pretraining? Make Prompt-based Fine-tuning Powerful Learner". I have analyzed the paper's proposed method, Prompt-based Continued Pre-training (PCP), which involves constructing a continued pre-training corpus using prompt templates and labels (golden or pseudo) and then performing MLM-based continued pre-training on this corpus before final prompt-based fine-tuning.

I identified several key components of the PCP method:
1.  The core idea of continued pre-training.
2.  The novel aspect of using prompt-based formatting with labels during continued pre-training.
3.  The use of an unsupervised objective (MLM) for continued pre-training.
4.  The pseudo-labeling process for unlabelled data (in the semi-supervised setting).
5.  The specific verbalizer mapping used in the prompt format.
6.  The composition/ratio of data (labelled vs unlabelled) in the continued pre-training corpus.
7.  The model initialization strategy for the continued pre-training phase.

I reviewed the paper's experimental results section to avoid suggesting ablations that are already presented as core comparisons or analyses. The paper extensively compares PCP with conventional TAPT (which is essentially PCP without the prompt formatting during continued pre-training) and analyzes the effect of the *amount* of unlabelled data.

Based on this, I selected four important and distinct aspects of PCP that are not fully explored as dedicated ablation studies in the paper:

1.  **The contribution of pseudo-labeled unlabelled data:** In the semi-supervised setting, PCP uses unlabelled data with pseudo-labels in the continued pre-training corpus. An ablation removing this component (i.e., using only labelled data for continued pre-training) would directly assess the value of the semi-supervised aspect of PCP's continued pre-training phase.
2.  **The importance of the specific verbalizer:** PCP uses a prompt format $\mathcal{T}(X, \mathcal{M}(y))$ where $\mathcal{M}(y)$ is a verbalizer mapping labels to meaningful words. Ablating this by using generic tokens instead of meaningful words for the label part during continued pre-training would test if the semantic content of the verbalized label is crucial or if just the structural inclusion of a label token is sufficient.
3.  **The effect of model initialization for continued pre-training:** PCP initializes the model for continued pre-training with the base pre-trained LM parameters. An alternative is to initialize it with the parameters obtained from the initial fine-tuning on labelled data (Step 1). This ablation would investigate which initialization is better for the subsequent continued pre-training phase.
4.  **The impact of the data ratio in the continued pre-training corpus:** The composition of the corpus $\mathcal{C}$ (ratio of labelled to unlabelled data) could influence performance. While the paper varies the total amount of unlabelled data, exploring different *ratios* for a fixed total size or relative to the labelled set size would provide further insight into the optimal data mix.

These four ablations cover different facets of the PCP method and are ranked by their perceived importance in understanding the method's success, starting with the role of the semi-supervised data component. The metrics used are the standard evaluation metrics reported in the paper (Accuracy, Pearson/Spearman Correlation, and Mean Performance across tasks).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### PCP without Pseudo-labeled Unlabelled Data
- **Ablated Part**: Inclusion of unlabelled data with pseudo-labels in the continued pre-training corpus.
- **Action**: REPLACE
- **Replacement**: 
  - Construct corpus using only labelled data with golden labels
- **Metrics**: Accuracy, Pearson Correlation, Spearman Correlation, Mean Performance

### PCP with Generic Verbalizer for CPT
- **Ablated Part**: Using task-specific verbalizer words in the continued pre-training corpus.
- **Action**: REPLACE
- **Replacement**: 
  - Use generic tokens (e.g., [LABEL_0], [LABEL_1]) for labels in the CPT corpus
- **Metrics**: Accuracy, Pearson Correlation, Spearman Correlation, Mean Performance

### PCP CPT Initialization from Fine-tuned Model
- **Ablated Part**: Initializing the continued pre-training model with base LM parameters.
- **Action**: REPLACE
- **Replacement**: 
  - Initialize the continued pre-training model with parameters from initial fine-tuning on labelled data
- **Metrics**: Accuracy, Pearson Correlation, Spearman Correlation, Mean Performance

### PCP CPT Corpus Data Ratio
- **Ablated Part**: The ratio of labelled vs unlabelled data in the continued pre-training corpus.
- **Action**: REPLACE
- **Replacement**: 
  - Test different proportions of labelled to unlabelled data (e.g., varying the number of unlabelled examples relative to the labelled set size)
- **Metrics**: Accuracy, Pearson Correlation, Spearman Correlation, Mean Performance

</div>