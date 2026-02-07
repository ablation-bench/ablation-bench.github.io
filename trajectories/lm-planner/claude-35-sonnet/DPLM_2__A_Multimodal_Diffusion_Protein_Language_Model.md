<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/claude-3.5-sonnet/DPLM_2__A_Multimodal_Diffusion_Protein_Language_Model

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

First, let me identify the main ablation studies already present in the paper:

1. The paper includes ablations on sequence pre-training and synthetic structures (Section A.6)
2. There are ablations on the self-mixup training strategy (Section A.5)
3. The paper studies different codebook sizes for the structure tokenizer (Section B.2)

Looking at the key components of DPLM-2, I notice two important missing ablations:

1. The structure tokenizer architecture is a critical component, using GVP-based encoder and IPA-based decoder. While the paper evaluates different codebook sizes, it doesn't ablate the choice of encoder/decoder architectures.

2. The paper uses a distinct noise scheduler for structure and sequence tokens during training, which is a novel contribution, but doesn't fully explore different scheduling strategies.

I'll focus on these two as they represent core methodological choices that could significantly impact performance.

The metrics used in the paper vary by task but generally include:
- For structure prediction: RMSD, TMscore
- For sequence generation: AAR (amino acid recovery), scTM (structure consistency)
- For co-generation: scTM, scRMSD, pLDDT
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Structure Tokenizer Architecture Ablation
- **Ablated Part**: GVP encoder and IPA decoder in structure tokenizer
- **Action**: REPLACE
- **Replacement**: 
  - ESM-based encoder
  - AlphaFold2-style encoder
  - Simple MLP encoder
  - Transformer decoder
- **Metrics**: lddt_ca, TMscore, RMSD

### Noise Scheduler Strategy Ablation
- **Ablated Part**: Distinct noise schedulers for structure and sequence
- **Action**: REPLACE
- **Replacement**: 
  - shared noise scheduler
  - fixed ratio scheduler
  - curriculum scheduler (increasing structure noise over time)
- **Metrics**: scTM, scRMSD, AAR, pLDDT

</div>