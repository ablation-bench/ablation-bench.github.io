<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/o3-mini/ddm2

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The proposed ablation studies target the key innovations in DDM². The highest‐priority study evaluates the impact of our Markov chain state matching mechanism. Instead of matching the noise level (σ) to find the appropriate intermediate state Sₜ where the noisy input is represented, we can simply start the reverse process from S_T (the conventional unconditional diffusion start point). This ablation will clarify how critical the conditional generation via state matching is. 

Next, our method uses a “noise shuffle” operation in Stage III during diffusion model training. Removing the shuffle will show whether forcing the network to learn from the noisy distribution directly (without spatial decorrelation) degrades performance. 

Another aspect is the processing scheme: our method improves spatial consistency by training a slice-to-slice (2D) mapping rather than the conventional patch-to-voxel or volume‐wise approach used in Patch2Self. An ablation replacing the slice-wise design with a volume-wise alternative will reveal its contribution to both consistency and denoising quality.

We also propose an ablation on the loss function used for training the diffusion denoiser (F). Our method adopts a modified J-invariance loss (supervising F using the noisy input directly) to prevent F from simply inverting the preliminary denoiser (Φ). Comparing this with a traditional supervised loss computed on the denoised output from Φ will quantify the benefit of the J-Invariance strategy.

Finally, the noise model learning stage includes an explicit noise mean correction step (subtracting the estimated residual’s mean) to ensure the noise model is zero-mean. Removing this compensation will assess the importance of this calibration in matching the diffusion noise schedule.
</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); border-left: 5px solid #9c27b0; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #7b1fa2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Ablation: Fixed Start Diffusion
- **Ablated Part**: Markov chain state matching component in Stage II that determines the starting state Sₜ based on the estimated noise distribution
- **Action**: REPLACE
- **Replacement**: 
  - fixed start at S_T
- **Metrics**: SNR, CNR

### Ablation: Remove Noise Shuffle
- **Ablated Part**: Noise shuffle operation in Stage III used during diffusion model training to decorrelate spatial noise
- **Action**: REMOVE
- **Metrics**: SNR, CNR

### Ablation: Volume-wise Denoising
- **Ablated Part**: Slice-wise processing scheme in Stage I for noise model learning and denoising
- **Action**: REPLACE
- **Replacement**: 
  - traditional volume-wise (patch-to-voxel) processing
- **Metrics**: SNR, CNR, Spatial consistency

### Ablation: Conventional Loss Function
- **Ablated Part**: J-Invariance optimization in Stage III that supervises F using the noisy input instead of the denoised approximation
- **Action**: REPLACE
- **Replacement**: 
  - loss computed with Φ output
  - standard supervised loss with approximated clean image
- **Metrics**: SNR, CNR

### Ablation: Without Noise Mean Correction
- **Ablated Part**: Explicit noise mean correction in Stage II that forces the residual noise to have zero mean before matching
- **Action**: REMOVE
- **Metrics**: SNR, CNR

</div>