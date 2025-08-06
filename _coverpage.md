<!-- markdownlint-disable first-line-h1 -->

<img src="_media/icon.png" alt="logo" width="200"/>

# **AblationBench**

> Evaluating Automated Planning of Ablations in Empirical AI Research

[Talor Abramovich](https://talorabr.github.io)&nbsp;&nbsp;&nbsp;&nbsp;[Gal Chechik](https://chechiklab.biu.ac.il/~gal/)

- A benchmark suite for automated ablation planning
- Current LM system identifies only **29%** of the original ablations on average
- Submit your own results to our [Leaderboard](#leaderboard)!

<div class="scroll-arrow-wrapper">
  <div class="scroll-arrow"></div>
</div>

<style>
.scroll-arrow-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60px;
  pointer-events: none; /* avoids interfering with buttons */
}

.scroll-arrow {
  width: 40px;
  height: 40px;
  position: relative;
  animation: arrow-bounce 1.5s infinite;
}

.scroll-arrow::before {
  content: '';
  position: absolute;
  top: 10px;
  left: 0;
  width: 100%;
  height: 100%;
  border: solid black;
  border-width: 0 0 4px 4px;
  transform: rotate(315deg);
  box-sizing: content-box;
  display: block;
}

/* Confined to only this arrow */
@keyframes arrow-bounce {
  0%, 100% {
    transform: translateY(0);
    opacity: 0.7;
  }
  50% {
    transform: translateY(8px);
    opacity: 1;
  }
}
</style>

[Learn More](#ablationbench)
[Paper 📎](https://www.arxiv.org/abs/2507.08038)
[HuggingFace 🤗](https://huggingface.co/collections/ai-coscientist/ablationbench-682701a2c1eafb87b1b087ea)
[GitHub 💻](https://github.com/ai-scientist-bench/ablation-bench)




<!-- ![color](#b1ffbb) -->
<!-- ![](/_media/icon.png) -->
