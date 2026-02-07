<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/llama-3.1-405b-instruct/Evolving_Alignment_via_Asymmetric_Self_Play

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Evolving Alignment via Asymmetric Self-Play" presents a novel approach to aligning large language models (LLMs) with human values. The authors propose a game-theoretic framework, called **eva**, which involves an asymmetric game between two players: a creator and a solver. The creator generates new prompt distributions, while the solver optimizes its response policy to align with human preferences. The goal of **eva** is to evolve the prompt distribution to improve the alignment of the LLM with human values.

The authors demonstrate the effectiveness of **eva** through experiments on various benchmarks, including AlpacaEval 2.0, MT-Bench, and Arena-Hard. The results show that **eva** can improve the alignment of LLMs with human values, outperforming traditional methods that rely on fixed prompt distributions.

One of the key contributions of this paper is the introduction of a new principle for open-ended RLHF, which generalizes classical RLHF by allowing the prompt distribution to evolve over time. The authors also propose a new algorithm for **eva**, which involves alternating optimization between the creator and the solver.

The paper also discusses the limitations and potential future directions of **eva**, including the need for more efficient and scalable algorithms, and the importance of exploring different evolving methods and informativeness metrics.

Overall, the paper presents a novel and promising approach to aligning LLMs with human values, and demonstrates the potential of **eva** to improve the alignment of LLMs with human values.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation A
- **Ablated Part**: informativeness metric
- **Action**: REPLACE
- **Replacement**: 
  - variance
  - mean
- **Metrics**: win rate, average score

### Ablation B
- **Ablated Part**: evolving method
- **Action**: REPLACE
- **Replacement**: 
  - SelfInstruct
  - EvolQuality
  - EvolComplexity
- **Metrics**: win rate, average score

</div>