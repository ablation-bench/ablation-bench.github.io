<!-- markdownlint-disable first-line-h1 -->

<img src="_media/icon.png" alt="logo" width="200"/>

# **AblationBench**

> Evaluating Automated Planning of Ablations in Empirical AI Research

[Talor Abramovich](https://talorabr.github.io)&nbsp;&nbsp;&nbsp;&nbsp;[Gal Chechik](https://chechiklab.biu.ac.il/~gal/)

- A benchmark suite for automated ablation planning
- Current LM system identifies only **29%** of the original ablations on average
- Submit your own results to our [Leaderboard](#leaderboard)!


[Learn More](#ablationbench)
[Paper 📎](https://www.arxiv.org/abs/2507.08038)
[HuggingFace 🤗](https://huggingface.co/collections/ai-coscientist/ablationbench-682701a2c1eafb87b1b087ea)
[GitHub 💻](https://github.com/ai-scientist-bench/ablation-bench)


<div class="down-arrow"></div>

<style>
.down-arrow {
  width: 50px;
  height: 40px;
  margin: 30px auto;
  position: relative;
  animation: bounce-down 1.5s infinite;
  opacity: 0.7;
}

.down-arrow::before {
  content: '';
  position: absolute;
  top: 10px;
  left: 0;
  width: 100%;
  height: 100%;
  border: solid #000;
  border-width: 0 0 4px 4px;
  transform: rotate(315deg); /* Makes it point down like a V */
  box-sizing: content-box;  /* Prevents affecting layout */
  display: block;
}

@keyframes bounce-down {
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

<!-- ![color](#b1ffbb) -->
<!-- ![](/_media/icon.png) -->
