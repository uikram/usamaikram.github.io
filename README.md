# Usama Ikram

**MS Candidate in Artificial Intelligence, DGIST (Daegu, Republic of Korea)**

[uikram.github.io](https://uikram.github.io/usamaikram.github.io) ·
[usamaikram@dgist.ac.kr](mailto:usamaikram@dgist.ac.kr) ·
[LinkedIn](https://www.linkedin.com/in/usamaikram/)

---

I am a graduate researcher in artificial intelligence, working in machine learning and computer
vision with a growing focus on multimodal and foundation models. My research asks what happens to
pretrained models when they leave the benchmark: how they can be adapted to specialised domains at
reasonable cost, and whether the resulting systems are dependable for the purpose they were built for.

That has meant deriving a latency bound for a vision-language model inside a real-time human-robot
interaction loop, adapting lightweight vision backbones to holographic cell imaging, building a network
that measures cells directly from a raw hologram, and leading a systematic review that counted how much
evidence stands behind a set of clinical claims. Before my MS I spent two years as an AI research
engineer, building models for constrained hardware and imperfect data.

I am applying for PhD positions starting in the second half of 2027, in multimodal and foundation
models, efficient and deployable AI, and healthcare applications.

---

## Research

Manuscripts 1 to 3 are first-authored and **under peer review**; none has been accepted or published.
Manuscript 4 is a complete draft **in preparation**. Full texts of all four are available on request.

### 1. Delay-Aware Deployability of Multimodal Foundation Models for Real-Time Human-Robot Interaction

*Usama Ikram, Youhyun Kim, Inkyu Moon* · submitted to *IEEE Transactions on Human-Machine Systems*
→ [`Delay_Aware_Deployability_Proof`](https://github.com/uikram/Delay_Aware_Deployability_Proof)

A model's inference time is a transport delay inside a wearable control loop, and past some threshold
the loop becomes unstable however accurate the perception is. A first-order Padé approximation and the
Routh-Hurwitz criterion give that threshold, 37.77 ms, for a PID-controlled mass-spring-damper plant.

* LoRA-adapted CLIP (0.65% of parameters trained) kept linear-probe quality at 85.69% against 85.95%,
  while zero-shot transfer rose 6.05% on remote-sensing imagery and fell 4.37% on object-centric data.
* Merged LoRA-CLIP reached 17.92 ms worst-case latency, inside the bound and inside the 18.76 ms bound
  that survives ±50% biomechanical variation; unmerged adapters added 8.5 ms.
* A Frozen Prefix-LM reached 442.02 ms, 11.7× over the bound, although its visual encoder took 8.25 ms.

*Measured on a desktop RTX A5000; edge figures are projections; validated in software-in-the-loop
simulation, not on a physical robot.*

### 2. Physics-Aware Lightweight Segmentation for Quantitative Holographic Cell Analysis with Optical Mass Preservation

*Usama Ikram, Youhyun Kim, Inkyu Moon* · submitted to *Applied Physics B: Lasers and Optics*
→ [`Lightweight_QPI_Segmentation`](https://github.com/uikram/Lightweight_QPI_Segmentation)

A cell's dry mass is its quantitative phase integrated over the segmented region, so the boundary is the
domain of a measurement. A Physics-Aware Phase Consistency Loss (phase-mask contrast, boundary-gradient
alignment, integrated-phase preservation) with LoRA-adapted EdgeSAM, MobileSAM and MobileNet-UNet:

* Integrated-phase error fell from 5.22% to 3.04% (EdgeSAM) and 15.52% to 3.01% (MobileNet-UNet),
  with boundary F1 rising to 0.953 and 0.970; contrast alone collapsed boundary F1 to 0.386.
* Full fine-tuning drove one minority class to zero Dice in all three backbones; LoRA at rank 8 kept
  all four classes in both attention-based backbones.
* On 1,974 cells over a 47-day storage study, dry mass from predicted masks matched annotation-derived
  values at r = 0.966; ONNX FP16 inference took 4.33 ms at 16.4 MB.

*Desktop-GPU measurements; embedded deployment not demonstrated; no independent held-out cohort.*

### 3. Determinants of Glycaemic Outcomes in Children and Adolescents with Type 1 Diabetes: A Systematic Review and Evidence Map

*Usama Ikram (corresponding author), Abey Jose, Francisca C. Eyzaguirre, Alejandro Mac Cawley* ·
submitted to *Pediatric Diabetes* · PROSPERO CRD420251045872

63 studies from 5,406 records, screened independently by two reviewers and reported to PRISMA 2020,
organised into the PEARL framework: 47 determinants across five domains under four stated rules, each
with a counted weight of evidence. 68% of the 148 physiological associations reached significance
against all 26 in the psychological domain, which selective reporting explains more economically than
larger effects.

### 4. Measurement-Oriented End-to-End Holographic Quantitative Phase Analysis: Joint Reconstruction, Segmentation and Per-Cell Measurement from a Single Raw Hologram

*Usama Ikram, Inkyu Moon* · in preparation
→ [`End-to-End-Lightweight-Holographic-Reconstruction-and-Quantitative-Cell-Analysis`](https://github.com/uikram/End-to-End-Lightweight-Holographic-Reconstruction-and-Quantitative-Cell-Analysis) (code)

One network (shared MobileNetV2 encoder, two U-Net decoders, 9.6M parameters) maps a raw hologram
directly to phase, segmentation and per-cell dry mass, evaluated on 800 fields of three cancer cell
lines in off-axis and in-line Gabor geometry, with three seeds and a two-SD resolution criterion.

* Off-axis, per-cell dry-mass error fell from 22.45% (classical pipeline) to 17.63%, and boundary F1
  rose from 0.246 to 0.457.
* A per-cell integrated-phase loss did **not** help: it raised dry-mass error beyond seed noise at every
  weight tried, which I attribute (untested) to labels derived from the reconstruction target.
* Model-free error budget: a one-pixel boundary shift costs 4.8% of dry mass at Dice 0.974.

*Detection recall (0.592) is the main weakness; LoRA implemented but not trained; workstation-GPU timings.*

---

## Earlier projects

| Project | Description |
|---|---|
| [Knee osteoarthritis grading](https://github.com/uikram/Knee_Osteoarthritis_Classification) | Kellgren-Lawrence grading from OAI radiographs with a heterogeneous CNN ensemble; Grad-CAM and LIME used to check reliance on joint space narrowing |
| [Alzheimer's early detection](https://github.com/uikram/Early-Detection-of-Alzheimer-s-Disease) | Undergraduate thesis: CNN classification of ADNI imaging with ridge regression and an SVM progression stage, deployed on a Jetson Nano |
| Automated candidate recruitment | LLM-based resume scoring with quizzes generated from each CV and red-flag detection |
| Smart surveillance | Lightweight detection and classification on RK3588 chipsets for on-device smart cameras |
| Predictive maintenance | Vibration-based classification of injection moulding machine states |
| Anomaly detection | Autoencoder that flags anomalies in time series through reconstruction error |
| Machine positioning | Bluetooth signal strength and trilateration to locate machines on a plant floor |

---

## Tools

Python · PyTorch · TensorFlow · Hugging Face · PEFT/LoRA · ONNX Runtime · OpenCV · C++ · CUDA · MATLAB ·
Docker · Git · embedded inference on RK3588 and Jetson Nano

---

*Last updated September 2026.*
