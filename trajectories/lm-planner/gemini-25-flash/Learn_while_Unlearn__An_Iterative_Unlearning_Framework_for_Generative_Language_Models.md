<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Learn_while_Unlearn__An_Iterative_Unlearning_Framework_for_Generative_Language_Models

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Learn while Unlearn: An Iterative Unlearning Framework for Generative Language Models" introduces the ICU framework with three core components: Knowledge Unlearning Induction (KUI), Contrastive Learning Enhancement (CLE), and Iterative Unlearning Refinement (IUR). The KUI module uses an unlearning loss ($\mathcal{L}_{\text{fgt}}$), the CLE module uses analogous data with a learning enhancement loss ($\mathcal{L}_{\text{lrn}}$) and a KL divergence loss ($\mathcal{L}_{\text{kl}}$), and the IUR module dynamically updates the forget set and provides a stopping criterion. The total loss is $\mathcal{L} = \mathcal{L}_{\text{fgt}} + \alpha \mathcal{L}_{\text{lrn}} + \beta \mathcal{L}_{\text{kl}}$.

The paper includes an ablation study (Section 4.6) that investigates the impact of the individual losses within the CLE module, specifically removing $\mathcal{L}_{\text{lrn}}$ (setting $\alpha=0$) and removing $\mathcal{L}_{\text{kl}}$ (setting $\beta=0$). Section 4.7 explores the sensitivity to the hyperparameters $\alpha$ and $\beta$.

While these ablations are informative about the contribution of the individual loss terms within CLE, they do not fully ablate the main components of the framework. Two important missing ablation studies are:

1.  **Ablating the entire Contrastive Learning Enhancement (CLE) module:** The existing ablations remove $\mathcal{L}_{\text{lrn}}$ or $\mathcal{L}_{\text{kl}}$ individually, but not both simultaneously. Removing the entire CLE module (equivalent to setting both $\alpha=0$ and $\beta=0$) would directly assess the overall contribution of the "Contrastive Learning Enhancement" aspect, which is central to the paper's claim of preserving expressive capabilities while unlearning. This would show the performance trade-off when only using the unlearning loss ($\mathcal{L}_{\text{fgt}}$) combined with the iterative refinement.

2.  **Ablating the Iterative Unlearning Refinement (IUR) module:** The IUR module's dynamic updating of the forget set and its specific stopping criterion based on unlearning metrics are key features. An ablation study removing this iterative process and replacing it with a fixed training schedule (e.g., training for a predetermined number of epochs) would demonstrate the value of the dynamic refinement and stopping mechanism. This would highlight whether the iterative process is crucial for balancing unlearning and preservation or if a fixed training approach could suffice.

These two missing ablations are crucial for understanding the contribution of the two main novel modules (CLE and IUR) proposed by the ICU framework beyond a basic unlearning approach. Ablating the entire CLE module is arguably more important as it tests the core "learn while unlearn" mechanism.

The metrics used for these ablations should be the comprehensive set reported in the paper's main results and existing ablations, covering both unlearning performance and general model capabilities.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: No CLE
- **Ablated Part**: Contrastive Learning Enhancement module (removing both learning enhancement loss and KL divergence loss)
- **Action**: REMOVE
- **Metrics**: EL10 (%), MA (%), BERT (F1), Entropy, Cls Avg. (ACC), Dia Avg. (F1), Pile (PPL), Wikitext (PPL), GPT

### Ablation: No IUR
- **Ablated Part**: Iterative Unlearning Refinement module (dynamic forget set update and stopping criterion)
- **Action**: REPLACE
- **Replacement**: 
  - Train for a fixed number of epochs (e.g., average epochs reported for ICU in Table 1)
- **Metrics**: EL10 (%), MA (%), BERT (F1), Entropy, Cls Avg. (ACC), Dia Avg. (F1), Pile (PPL), Wikitext (PPL), GPT

</div>