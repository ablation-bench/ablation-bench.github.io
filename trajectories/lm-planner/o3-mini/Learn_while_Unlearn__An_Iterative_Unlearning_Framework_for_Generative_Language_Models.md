<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/Learn_while_Unlearn__An_Iterative_Unlearning_Framework_for_Generative_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

After reviewing the paper, note that while the authors have conducted ablation experiments to assess the impact of the paired loss and KL-divergence loss (from the CLE module), they do not explicitly evaluate the contribution of two critical design choices. First is the Iterative Unlearning Refinement (IUR) module, whose role is to dynamically assess the unlearning extent and prevent over-unlearning. An ablation study that completely removes IUR would reveal the importance of iterative updates in balancing unlearning performance and preservation of generative capabilities. Second, while the Contrastive Learning Enhancement (CLE) module relies on KNN sampling to select analogous paired data, its specific design choice is not compared against alternative pairing strategies. Replacing KNN sampling with a simpler random (or frequency-based) sampling strategy can illustrate how crucial proper contrastive data selection is for maintaining model expressiveness during unlearning. For both ablations, we propose evaluating metrics that are central to the paper such as Extraction Likelihood (EL), Memorization Accuracy (MA), BERTScore, BLEU, perplexity (Pile/Wikitext), and GPT Evaluation to rigorously quantify the trade-offs.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation IUR Module
- **Ablated Part**: Iterative Unlearning Refinement (IUR) module that dynamically assesses unlearning extent and prevents over-unlearning
- **Action**: REMOVE
- **Metrics**: Extraction Likelihood (EL), Memorization Accuracy (MA), BERTScore, Pile Perplexity (PPL), Wikitext Perplexity (PPL), GPT Evaluation

### Ablation Contrastive Sampling Strategy
- **Ablated Part**: KNN-based sampling method in the Contrastive Learning Enhancement (CLE) module for selecting paired analogous data
- **Action**: REPLACE
- **Replacement**: 
  - Random Sampling
  - Frequency-based Sampling
- **Metrics**: Extraction Likelihood (EL), Memorization Accuracy (MA), BERTScore, BLEU, Pile Perplexity (PPL), GPT Evaluation

</div>