<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-35-sonnet/amrbart

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

Based on the paper, the key components that warrant ablation studies are:

1. Graph Pre-training Strategies: The paper introduces two main graph auto-encoding strategies - node/edge level denoising and sub-graph level denoising. Testing their individual contributions is crucial.

2. Unified Pre-training Framework: The paper proposes several tasks to integrate text and graph information. Testing the impact of different combinations is important.

3. Dynamic Masking Rate: The paper uses a dynamic masking rate that increases over time. Testing this against static masking would be valuable.

4. Pre-training Data: The paper mentions using silver data, so testing the impact of different data sources is relevant.

5. Input Format: The unified format combining text and graph sequences is a key innovation that should be tested.

I'll suggest the most important ablation studies focusing on these components, using the metrics mentioned in the paper (BLEU, METEOR, chrF++ for generation; Smatch for parsing).
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Graph Pre-training Strategy Ablation
- **Ablated Part**: graph auto-encoding strategies
- **Action**: REPLACE
- **Replacement**: 
  - node/edge level only
  - sub-graph level only
  - no graph pre-training
- **Metrics**: BLEU, METEOR, chrF++, Smatch

### Pre-training Task Combination
- **Ablated Part**: unified pre-training tasks
- **Action**: REMOVE
- **Metrics**: BLEU, METEOR, chrF++, Smatch

### Masking Rate Strategy
- **Ablated Part**: dynamic masking rate
- **Action**: REPLACE
- **Replacement**: 
  - static 0.15 rate
  - static 0.35 rate
- **Metrics**: BLEU, METEOR, chrF++, Smatch

### Input Format
- **Ablated Part**: unified text-graph input format
- **Action**: REPLACE
- **Replacement**: 
  - text-only format
  - graph-only format
- **Metrics**: BLEU, METEOR, chrF++, Smatch

### Silver Data Usage
- **Ablated Part**: silver data in pre-training
- **Action**: REMOVE
- **Metrics**: BLEU, METEOR, chrF++, Smatch

</div>