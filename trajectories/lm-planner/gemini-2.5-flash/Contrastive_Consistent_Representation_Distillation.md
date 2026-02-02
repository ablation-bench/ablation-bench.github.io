<style>
.trajectory-box strong {
  color: #1a1a1a !important;
}
.trajectory-box h3 {
  color: #1a1a1a !important;
}
</style>

# lm-planner/gemini-2.5-flash/Contrastive_Consistent_Representation_Distillation

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); border-left: 5px solid #2196f3; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #1976d2; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">🧠 Reasoning Trace</h2>

The paper "Contrastive Consistent Representation Distillation (CoCoRD)" proposes a novel knowledge distillation method combining contrastive learning with consistent representations. The core components include a fixed-size teacher dictionary (queue), a teacher with a momentum-updated projection head, a student, and a slow-moving student with its own momentum-updated projection head. The method uses a contrastive loss (InfoNCE) and a prediction loss (MSE) between the student and the slow-moving student, along with a task-specific loss.

The paper includes several ablation studies:
1.  **Study of Encoder Combinations (Section 4.3.1):** Investigates which model (Teacher, Student, Slow-moving Student) should provide representations for the dictionary (contrastive encoder) and the class-positive targets (cognate encoder). This confirms the importance of using the pre-trained teacher for the dictionary and the slow-moving student for the cognate targets.
2.  **Study of Momentum (Section 4.3.2):** Explores the impact of the momentum coefficients (mc and mr) for the teacher projection head and the slow-moving student/projection head, respectively. This shows that momentum updates (mc < 1, mr < 1) are generally beneficial compared to no momentum (mc=0, mr=0) or frozen (mc=1, mr=1).
3.  **Study of Hyper-parameters (Section 4.3.3):** Analyzes the effect of temperature (τ), dictionary size (N), and loss balancing factors (λctr, λcls, λpred). This demonstrates the sensitivity to τ and N, and confirms that all three loss components are important (λctr > 0, λpred > 0, λcls > 0).

Based on the method description and existing ablations, I identify two important missing ablation studies:

1.  **Symmetrization of the Prediction Loss (Lpred):** The paper introduces a prediction loss (Lpred) between the student's prediction of the slow-moving student's representation and the actual slow-moving student representation. This loss is then symmetrized by swapping the inputs to the student and slow-moving student (Lpred + L~pred). While the importance of the prediction loss itself is shown (Table 7, λpred=0 vs λpred=4), the necessity or benefit of this specific symmetrization is not ablated. It would be valuable to see if using only one direction of the prediction loss (e.g., student predicting slow-moving student, or vice versa) is sufficient or if the symmetrization provides a significant boost.

2.  **Role of Teacher Projection Head Momentum in Cross-Architecture Distillation:** The paper states in Section 1 that if the teacher and student have different feature dimensions (common in cross-architecture KD), the teacher projection head is randomly initialized and *not updated* (implying mc=1). However, the ablation study on momentum (Table 6) uses the resnet110/resnet32 pair, which is a cross-architecture combination (as shown in Table 2), and presents results for mc < 1 (e.g., mc=0.999). This suggests the teacher projection head *is* momentum-updated in cross-architecture settings, contradicting the earlier statement. An explicit ablation comparing a frozen teacher projection head (mc=1) vs. a momentum-updated one (mc<1) specifically for a cross-architecture pair would clarify the method's implementation and the role of teacher momentum in this scenario.

These two ablations are important because they investigate specific design choices (symmetrization) and clarify potential inconsistencies in the method description regarding cross-architecture settings (teacher momentum). They would help attribute performance gains more precisely and provide clearer guidance for implementing CoCoRD, especially in diverse student-teacher scenarios.
</div>

<div style="background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%); border-left: 5px solid #4caf50; padding: 20px; margin: 20px 0; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); color: #1a1a1a;" class="trajectory-box">
<h2 style="color: #2e7d32; margin-top: 0; margin-bottom: 15px; font-size: 1.3em;">📋 Ablation Plan</h2>

### Study of Lpred Symmetrization
- **Ablated Part**: Symmetrization of the prediction loss (Lpred)
- **Action**: REPLACE
- **Replacement**: 
  - Lpred only
  - L~pred only
- **Metrics**: Top-1 accuracy (%)

### Study of Teacher Momentum in Cross-Architecture KD
- **Ablated Part**: Momentum update for the teacher projection head (mc) in cross-architecture distillation
- **Action**: REPLACE
- **Replacement**: 
  - 1.0
  - 0.999
- **Metrics**: Top-1 accuracy (%)

</div>