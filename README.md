# SSG: Scaled Spatial Guidance for Multi-Scale Visual Autoregressive Generation

<div align="center">

[![OpenReview](https://img.shields.io/badge/OpenReview-paper-blue)](https://openreview.net/forum?id=S6oLw7VixT)&nbsp;
<!-- [![huggingface weights](https://img.shields.io/badge/%F0%9F%A4%97%20Weights-FoundationVision/var-yellow)](https://huggingface.co/FoundationVision/var)&nbsp; -->

</div>

<!-- SSG: Scaled Spatial Guidance for Multi-Scale Visual Autoregressive Generation -->

<!-- <p align="center" style="font-size: larger;">
  <a href="https://arxiv.org/abs/2404.02905">SSG: Scaled Spatial Guidance for Multi-Scale Visual Autoregressive Generation</a>
</p>

<div>
  <p align="center" style="font-size: larger;">
    <strong>??</strong>
  </p>
</div> -->

<p align="center">
<img src="assets/main.png" width=96%>
<p>
    
<br>

## 📣 Update Logs

- Jan 30, 2026: Initial code release

- Jan 26, 2026: 🎉 SSG has been accepted to ICLR 2026. 🎉

- Sep 24, 2025: Paper release

## 📝 Abstract

Visual autoregressive (VAR) models generate images through next-scale prediction, naturally achieving coarse-to-fine, fast, high-fidelity synthesis mirroring human perception. In practice, this hierarchy can drift at inference time, as limited capacity and accumulated error cause the model to deviate from its coarse-to-fine nature. We revisit this limitation from an information-theoretic perspective and deduce that ensuring each scale to contribute high-frequency content not explained by earlier scales mitigates the train–inference discrepancy. With this insight, we propose Scaled Spatial Guidance (SSG), a training-free, inference-time guidance that steers generation toward the intended hierarchy while maintaining global coherence. SSG emphasizes target high-frequency signals, defined as the semantic residual, isolated from a coarser prior. To obtain this prior, we leverage a principled frequency-domain procedure, Discrete Spatial Enhancement (DSE), devised to sharpen and better isolate the semantic residual through frequency-aware construction. SSG applies broadly across VAR models leveraging discrete visual tokens, regardless of tokenization design or conditioning modality. Experiments demonstrate SSG yields consistent gains in fidelity and diversity while preserving low latency, revealing untapped efficiency in coarse-to-fine image generation.

### 💡 Efficient, Training-Free Guidance for VAR-Structured Models:

<p align="center">
<img src="assets/main_pipeline.png" width=96%>
<p>


**Scaled Spatial Guidance (SSG)** 🎯: Unlike standard pre-sampling, which relies solely on the $k$-th step logits, SSG actively incorporates logits from the preceding scale. It calculates the difference between scales to identify and emphasize the specific information required to be generated at step $k$.

**Discrete Spatial Enhancement (DSE)** 🎯: A frequency-domain upscaling method designed to bridge the dimensional gap between scales. This technique minimizes information loss and artifacts when projecting the representation of the previous step to the resolution of the current step.


### 📊 SSG with DSE: Targeting Essential Details while Preserving Established Structural Integrity


<p align="center">
<img src="assets/graphs.png" width=96%>
<p>

## 🛠️ SetUp

### Class Conditional (🏷️ ➔ 🖼️)

#### VAR

```bash
cd VAR
pip install -r requirements.txt
```
For detailed VAR setup instructions, please refer to [VAR Setup](./VAR/README.md).

### Text Conditional (📝 ➔ 🖼️)

#### HART
```bash
cd hart
pip install -r requirements.txt
```
For detailed HART setup instructions, please refer to [HART Setup](./hart/README.md).

#### Infinity
```bash
cd Infinity
pip install -r requirements.txt
```

For detailed Infinity setup instructions, please refer to [Infinity Setup](./Infinity/README.md).

## 📖 Citation

If this project provided insights or was helpful to your research, please give us a star ⭐ and cite us using:

```
@misc{shin2026ssg,
      title={SSG: Scaled Spatial Guidance for Multi-Scale Visual Autoregressive Generation}, 
      author={Youngwoo Shin and Jiwan Hur and Junmo Kim},
      year={2026},
      eprint={2601.XXXXX},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2601.XXXXX}, 
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

This codebase is also built upon the following open-source projects, which are licensed under the MIT License. We thank the authors for their contributions.
* [VAR](https://github.com/FoundationVision/VAR) - Licensed under MIT (see [var/LICENSE](./var/LICENSE))
* [HART](https://github.com/mit-han-lab/hart) - Licensed under MIT (see [hart/LICENSE](./hart/LICENSE))
* [Infinity](https://github.com/FoundationVision/Infinity) - Licensed under MIT (see [infinity/LICENSE](./infinity/LICENSE))
