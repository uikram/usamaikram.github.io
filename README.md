# Usama Ikram

**MS Candidate in Artificial Intelligence · DGIST (Daegu, Republic of Korea)**  
Graduate Researcher, [Intelligent Imaging and Vision Systems Laboratory (IIVS)](https://iivs.dgist.ac.kr/wordpress), [Daegu Gyeongbuk Institute of Science and Technology (DGIST)](https://www.dgist.ac.kr/)

[Website](https://uikram.github.io/usamaikram.github.io) ·
[CV (PDF)](https://uikram.github.io/usamaikram.github.io/Usama_Ikram_CV.pdf) ·
[usamaikram@dgist.ac.kr](mailto:usamaikram@dgist.ac.kr) ·
[GitHub](https://github.com/uikram) ·
[LinkedIn](https://www.linkedin.com/in/usamaikram/)

---

## Overview

I am a graduate researcher in the [Intelligent Imaging and Vision Systems Laboratory](https://iivs.dgist.ac.kr/wordpress) at [DGIST](https://www.dgist.ac.kr/), working on computer vision and multimodal AI. Most of my work takes large pretrained models, adapts them to a new domain with LoRA, and then checks what they keep, what they lose, and whether they hold up where they are actually used.

So far that has meant SAM-family segmentation models adapted to quantitative cell phase images, CLIP and a generative vision-language model tested inside a real-time control loop, networks that recover phase and cell masks directly from raw holograms in digital holographic microscopy, and a 63-study clinical evidence synthesis on paediatric type 1 diabetes. Before my MS, I spent two years in industry building computer vision, time-series anomaly detection, and LLM-based evaluation systems, including on-device inference on embedded hardware.

> **Prospective PhD (Fall 2027):** I am looking for funded PhD positions starting in Fall 2027 (or mid-to-late 2027 intakes) to work on vision-language models, multimodal LLMs, and foundation model adaptation for healthcare and biomedical imaging, with a focus on explainable and trustworthy AI. Across my current work and research outreach, I focus on how parameter-efficient fine-tuning (such as LoRA on SAM, MedSAM, and CLIP) reshapes representations: preserving rare morphological or clinical subgroups that full fine-tuning erases, bridging the gap between fluent generative VLMs and spatially grounded visual encoders for clinical report generation and pathology, embedding physical and measurement constraints into learned reconstruction and segmentation, and auditing failure modes that aggregate accuracy or Dice scores hide. **I am also open to remote research collaborations.**

---

## Unifying Research Thread

Across my graduate manuscripts (**M1–M4**) and earlier medical imaging projects, one empirical theme recurs: **aggregate benchmark averages routinely conceal who a model fails and whether its output is physically or clinically usable.**

1. **Tail & Subgroup Preservation:** MobileNet-UNet reached the highest instance score (AJI `0.551`) while losing the spherocyte and stomatocyte classes in every training seed; LoRA-adapted EdgeSAM (`r=32`) and MobileSAM (`r=8`) kept all 4 morphological classes in every seed, whereas single-seed full fine-tuning left MobileSAM with only discocytes (Dice `0.217` vs `0.810`) (**M2**).
2. **Measurement over Pixel Overlap:** A 1-pixel contour perturbation shifts per-cell dry mass by `4.8%` while Dice remains `0.974` (**M1**); adding a physics-aware optical mass preservation objective lowers EdgeSAM's integrated-phase error from `11.20%` (Dice only) to `3.02%`, and lowers it against Dice alone in `42` of `45` seed-paired runs, though only `3` of `15` configurations have a 95% interval excluding zero (**M2**).
3. **Closed-Loop & Evidence Auditing:** A fluent generative VLM (`442.02 ms`) violates a `37.77 ms` closed-loop stability bound by `11.7×` while scoring `51.25%` vs `85.95%` on linear-probe separability (**M3**); mapping `297` associations across `63` paediatric T1D studies shows `100%` (`26/26`) significance in emotional wellbeing versus `68%` (`101/148`) in physiology, exposing selective reporting skew (**M4**).

---

## Research Interests

1. **Low-Rank Adaptation, Learned Rank & Subgroup Survival Under Scarce Labels** *(Anchored in M2 & M3)*  
   Investigating rank-constrained parameterisation `B Diag(v) A` with ℓ₁ soft-thresholding on singular values `v` across attention layers when adapting SAM, MedSAM, or DINO backbones to long-tailed pathology and cell datasets; separating shared low-rank subspaces from minority-specific directions so dominant classes cannot overwrite rare phenotypes; and diagnosing silent rare-class collapse during test-time adaptation.
2. **Bridging the Generative–Discriminative Gap & Verifying Grounding in Medical VLMs** *(Anchored in M3 & M2)*  
   Understanding why generative multimodal objectives lose linear feature separability compared to contrastive encoders (`51.25%` vs `85.95%` in M3); designing hybrid or distilled training so medical VLMs retain both open-ended clinical reasoning and sharp discriminative boundaries; and verifying that generated radiology or pathology claims are anchored to segmented anatomical regions or quantitative measurements.
3. **Explaining & Calibrating Zero-Shot Readout Shifts in Adapted Vision-Language Models** *(Anchored in M3 & Knee OA)*  
   Regularising cross-modal projection alignment when parameter-efficient fine-tuning rotates zero-shot readout (`+6.05%` on EuroSAT vs `−4.37%` on object-centric benchmarks at unchanged `85.69%` linear-probe accuracy in M3); applying concept-level and language-grounded attribution to separate genuine domain transfer from spurious shortcuts; and calibrating clinical VLM uncertainty under noisy or varied prompts.
4. **Physics- & Measurement-Grounded Learning and Composite Objective Co-Design** *(Anchored in M1 & M2)*  
   Characterising when known physical operators (angular-spectrum propagation, optical mass conservation) regularise inverse reconstruction and when composite losses conflict (`+1.4` percentage-point dry-mass error increase in M1; in M2, phase-mask contrast alone did not stop class loss on EdgeSAM until boundary-gradient alignment was added); training segmentation models directly for downstream clinical and metrological accuracy; and leveraging cross-modality consistency for label-free adaptation.
5. **Delay-Aware & Safety-Critical Closed-Loop Perception (Barrier States & Hardware Co-Design)** *(Anchored in M3, M1 & Industry)*  
   Co-designing delay-compensated state estimation and control barrier functions with adaptive-rate VLM perception inside analytical stability bounds (`τ < 37.77 ms` nominal; `18.76 ms` under `±50%` parameter uncertainty); targeting actual memory-bandwidth bottlenecks rather than parameter counts alone (`65%` fewer decoder parameters yielded only `6–7%` GPU speedup in M1); and routing frames between fast contrastive encoders (`17.92 ms`) and generative VLMs on edge hardware (Jetson Nano, RK3588).
6. **Subpopulation Bias Auditing & Evidence-Weighted Clinical Decision Support** *(Anchored in M4, M2 & ADNI)*  
   Fusing longitudinal physiological signals (CGM time series, neuroimaging, microscopy) with psychosocial and demographic context without inheriting literature reporting skew (`68%` vs `100%` domain significance in M4's PEARL framework); building automated subgroup auditing pipelines across demographic and acquisition-site slices; and developing LLM-assisted living systematic review workflows.

---

## Manuscripts

All four manuscripts are first-authored (with **M4** as corresponding author). **M2 was revised and resubmitted** to *Applied Physics B: Lasers and Optics* in October 2026, and **M1, M3, and M4 are under peer review**. None has been accepted or published yet; detailed summaries, figures, and public code repositories are available on the [website](https://uikram.github.io/usamaikram.github.io) and linked below.

### M1 · Joint Phase Reconstruction and Cell Segmentation from Raw Holograms for Per-Cell Dry-Mass Measurement
* **Authors:** **Usama Ikram**, Inkyu Moon
* **Status:** Under review · [Public Code](https://github.com/uikram/End-to-End-Lightweight-Holographic-Reconstruction-and-Quantitative-Cell-Analysis)
* **Summary:** One `9.6M`-parameter network (MobileNetV2 encoder, dual U-Net decoders for sin/cos phase and foreground probability) maps a raw off-axis or in-line Gabor hologram directly to unwrapped phase and cell segmentation masks in `8.39 ms` per `900×900` field (ONNX FP16, RTX A5000) across `800` fields of three cancer cell lines (HeLa, PC-3, T24) over three training seeds.
* **Key Findings:**
  * Reduced off-axis matched-cell dry-mass MAPE from `22.0%` (classical FFT + Otsu) to `17.4%` at comparable Dice (`0.834` vs `0.825`), with `0.593` overall detection recall (`0.912` interior vs `0.212` within `32 px` of the field boundary).
  * Reached `r = 0.867` phase correlation on in-line Gabor holograms (`21.3%` dry-mass MAPE) where single-shot classical propagation failed to separate cells from twin-image artifacts (`r = −0.21`).
  * Demonstrated that a `±1 px` boundary shift changes per-cell dry mass by `4.8%` while Dice remains `0.974`, and reported verified negative results where measurement-aware integrated-phase losses increased per-cell error by `+1.4` percentage points beyond seed variation.

### M2 · Physics-Aware Lightweight Segmentation for Quantitative Holographic Cell Analysis with Optical Mass Preservation
* **Authors:** **Usama Ikram**, Youhyun Kim, Inkyu Moon
* **Status:** **Revised and resubmitted** (October 2026), *Applied Physics B: Lasers and Optics* · [Public Code](https://github.com/uikram/Lightweight_QPI_Segmentation)
* **Summary:** Introduces a composite physics-aware segmentation loss (phase-mask contrast, boundary-gradient alignment, and integrated-phase preservation), computed on background-referenced phase in radians, with LoRA adaptation of EdgeSAM, MobileSAM, and MobileNet-UNet on `248` single-channel 32-bit red-blood-cell phase maps (`182` training, `66` validation, `2,049` annotated validation cells) with four morphological classes. Each architecture was trained at five LoRA ranks with four loss configurations and three seeds (`180` runs).
* **Key Findings:**
  * EdgeSAM (`r=32`), the primary configuration, kept all four classes in every seed (Dice `0.738 ± 0.006`, integrated-phase error `3.02 ± 0.84%`, AJI `0.335`); MobileSAM (`r=8`) reached the highest Dice (`0.810`) and lowest error (`1.32%`); MobileNet-UNet had the highest AJI (`0.551`) but lost spherocytes and stomatocytes in every seed.
  * On EdgeSAM (`r=32`), Dice alone gave `11.20%` integrated-phase error and lost a class in two of three seeds; adding phase-mask contrast, then boundary-gradient alignment, then integrated-phase preservation reduced it to `7.45%`, `3.64%`, and `3.02%`, with no class lost. For MobileSAM and MobileNet-UNet, no single term's effect was separable from seed-to-seed variation.
  * Over a 47-day, 11-timepoint storage study, projected cell area fell by about `44%` in both annotation and predictions, while a dry-mass decrease was not statistically supported under date-clustered permutation tests; predicted per-image dry mass agreed with the annotation within a median absolute relative error of `3.9%` (`r = 0.38`). Absolute dry mass was not independently validated, and no held-out test cohort was available.
  * Merged rank-8 EdgeSAM forward pass: `4.11 ms` (`229–277 FPS`) in ONNX Runtime, strict FP32, RTX A5000.

### M3 · Delay-Aware Deployability of Multimodal Foundation Models for Real-Time Human-Robot Interaction
* **Authors:** **Usama Ikram**, Youhyun Kim, Inkyu Moon
* **Status:** Under review, *IEEE Transactions on Human-Machine Systems* · [Public Code](https://github.com/uikram/Delay_Aware_Deployability_Proof)
* **Summary:** Derives an analytical closed-loop transport-delay stability bound (`τ_max = 37.77 ms` nominal; `18.76 ms` worst-case under `±50%` human-loop parameter variation) using a first-order Padé approximation and the Routh-Hurwitz criterion, benchmarking CLIP, LoRA-CLIP (`0.98M` trainable parameters, `0.65%`), and a generative Frozen Prefix-LM.
* **Key Findings:**
  * Merged LoRA-CLIP satisfied the stability bound at `17.92 ms` worst-case latency (`14.34 ms` mean vs `22.87 ms` unmerged, saving `+8.5 ms` of adapter kernel overhead), whereas autoregressive token decoding pushed the Frozen Prefix-LM to `442.02 ms` (`11.7×` over the bound) despite an `8.25 ms` visual encoder.
  * LoRA-CLIP retained 5-dataset linear-probe representation quality (`85.69%` vs `85.95%` base CLIP, compared to `51.25%` for the generative Prefix-LM) while rotating zero-shot readout (`+6.05%` on EuroSAT, `−4.37%` on object-centric datasets).

### M4 · Determinants of Glycaemic Outcomes in Children and Adolescents with Type 1 Diabetes: A Systematic Review and Evidence Map
* **Authors:** **Usama Ikram** *(corresponding author)*, Abey Jose, Francisca C. Eyzaguirre, Alejandro Mac Cawley
* **Status:** Under review, *Pediatric Diabetes* · PROSPERO `CRD420251045872`
* **Summary:** PRISMA 2020 systematic review and MMAT quality appraisal screening `5,406` records across PubMed, Embase, Scopus, and Web of Science to synthesise `63` studies and `297` factor-study associations into the **PEARL framework** (`47` determinants across `12` sub-domains and `5` domains: Physiology & Clinical Status, Emotional & Psychological Wellbeing, Autonomy & Engagement in Self-Care, Relationships & Family Dynamics, and Lifestyle, Learning & Living Environment).
* **Key Findings:**
  * Physiology accounted for `31.9%` of distinct determinants (`15/47`) but `49.8%` of all tested associations (`148/297`), while nine determinants rested on a single study.
  * Well-replicated physiological determinants reached significance `68%` (`101/148`) of the time versus `100%` (`26/26`) for emotional and psychological wellbeing, identifying substantial selective reporting skew in the psychosocial literature.

---

## Undergraduate Research Projects & Industry Experience

| Role / Project | Organisation / Period | Highlights |
|---|---|---|
| **Graduate Researcher** | IIVS Lab, DGIST (`Sep 2025 – present`) | LoRA adaptation of vision and vision-language models, closed-loop VLM deployability (`M3`), and learned phase reconstruction & segmentation in digital holographic microscopy (`M1`, `M2`) |
| **AI & ML Scientist** | NASTP, Rawalpindi (`Jul – Sep 2025`) | YOLO surveillance detection/segmentation pipelines, autoencoder multimodal representation learning, neural compression/encryption, LLM candidate evaluation, and RK3588 edge deployment |
| **AI Research Engineer** | DeepChain, Islamabad (`Jul 2023 – Mar 2025`) | CNN, LSTM, and autoencoder models for vibration-based predictive maintenance, time-series anomaly detection, Bluetooth trilateration, and sensor-to-terminal data integrity |
| **[Knee Osteoarthritis Grading](https://github.com/uikram/Knee_Osteoarthritis_Classification)** | Undergraduate Research | 8-CNN ensemble with mixed hard/soft voting on `8,260` OAI radiographs (`76.93%` accuracy), audited with Grad-CAM and LIME on joint space narrowing |
| **[Alzheimer's Early Detection](https://github.com/uikram/Early-Detection-of-Alzheimer-s-Disease)** | NUST Final-Year Thesis (Grade A) | CNN classification on ADNI neuroimaging with ridge regression for clinical scores and SVM progression modelling, deployed on an NVIDIA Jetson Nano |

---

## Education & Technical Skills

* **MS in Artificial Intelligence**, [DGIST](https://www.dgist.ac.kr/), Republic of Korea (`Sep 2025 – expected Jun 2027`) · **GPA: 3.86 / 4.30**  
  *Coursework:* Optical Signal Processing (A+), Biomedical Programming (A+), Convex Optimization (A0), Deep Learning Lab (A0), Random Variables and Random Processes (B+), Linear Systems (B+).
* **BE in Electrical Engineering**, [NUST](https://nust.edu.pk/) College of E&ME, Rawalpindi (`Sep 2019 – Jun 2023`) · **CGPA: 3.27 / 4.00** (Final-Year Project Grade: A).
* **Technical Stack:** Python, C++, CUDA, MATLAB, SQL, LaTeX · PyTorch, TensorFlow, Hugging Face Transformers, PEFT (LoRA), ONNX Runtime (FP16), OpenCV, scikit-learn · Off-axis & in-line holographic reconstruction (angular-spectrum propagation, Gerchberg-Saxton) · Embedded inference on NVIDIA Jetson Nano & Rockchip RK3588.

---

## Repository Structure

```text
.
├── index.html                        # Main academic profile & interactive research portfolio
├── README.md                         # Repository documentation & research summary
├── Usama_Ikram_CV.pdf                # Curriculum Vitae (PDF)
├── Profile Picture.jpg               # Profile portrait
└── assets/                           # Verified manuscript figures (M1–M4)
    ├── m1_fig1_pipeline_overview.png
    ├── m1_fig3_phase_predictions.png
    ├── m1_fig7_boundary_sensitivity.png
    ├── m2_fig1_framework_overview.png
    ├── m2_fig6_lora_vs_fft_classes.png
    ├── m2_fig7_phase_gradient_contours.png
    ├── m2_fig9_rbc_morphologies.png
    ├── m2_fig12_storage_dry_mass.png
    ├── m3_fig1_delay_framework.png
    ├── m3_fig2_step_response.png
    ├── m3_fig3_degradation_curves.png
    └── m4_fig4_pearl_framework.svg   # Cropped Figure 4 from the Pediatric Diabetes submission
```

---
