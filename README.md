# Usama Ikram

**MS Candidate in Artificial Intelligence, DGIST (Daegu, Republic of Korea)**

[Website](https://uikram.github.io/usamaikram.github.io) ·
[CV (PDF)](https://uikram.github.io/usamaikram.github.io/Usama_Ikram_CV.pdf) ·
[usamaikram@dgist.ac.kr](mailto:usamaikram@dgist.ac.kr) ·
[LinkedIn](https://www.linkedin.com/in/usamaikram/)

---

I am a graduate researcher in the Intelligent Imaging and Vision Systems Laboratory at DGIST, working
on computer vision and multimodal AI. Most of my work takes large pretrained models, adapts them to a
new domain with LoRA, and then checks what they keep, what they lose, and whether they hold up where
they are used: SAM-family segmentation models adapted to cell images, CLIP and a generative
vision-language model tested inside a real-time control loop, and networks that recover phase and cell
masks directly from raw holograms in digital holographic microscopy. Before my MS I spent about two
years in industry building vision, time-series and LLM-based systems, some on embedded hardware.

I am looking for PhD positions starting in Fall 2027 to work on vision-language models and LLMs for
healthcare and biomedical imaging, with a focus on explainable and trustworthy AI.

---

## Manuscripts

All four are first-authored and **under peer review**. None has been accepted or published.

**M1. Joint Phase Reconstruction and Cell Segmentation from Raw Holograms for Per-Cell Dry-Mass Measurement**
*Usama Ikram, Inkyu Moon* · under review ·
[code](https://github.com/uikram/End-to-End-Lightweight-Holographic-Reconstruction-and-Quantitative-Cell-Analysis)
One network maps a raw off-axis or in-line hologram to quantitative phase and a cell segmentation.
Off-axis, matched-cell dry-mass error was 17.4% against 22.0% for the tested classical pipeline at
similar Dice, reported with detection recall (0.593) over three training seeds. Measurement-aware
integrated-phase losses increased the error and are reported as a negative result.

**M2. Physics-Aware Lightweight Segmentation for Quantitative Holographic Cell Analysis with Optical Mass Preservation**
*Usama Ikram, Youhyun Kim, Inkyu Moon* · under review, *Applied Physics B: Lasers and Optics* ·
[code](https://github.com/uikram/Lightweight_QPI_Segmentation)
A loss that preserves the phase integrated over each cell cut integrated-phase error from 5.22% to 3.04%
(EdgeSAM) and from 15.52% to 3.01% (MobileNet-UNet). Full fine-tuning erased a minority class in all
three backbones, while rank-8 LoRA kept all four classes in both SAM-based models.

**M3. Delay-Aware Deployability of Multimodal Foundation Models for Real-Time Human-Robot Interaction**
*Usama Ikram, Youhyun Kim, Inkyu Moon* · under review, *IEEE Transactions on Human-Machine Systems* ·
[code](https://github.com/uikram/Delay_Aware_Deployability_Proof)
A 37.77 ms stability bound derived with a Padé approximation and the Routh-Hurwitz criterion. Merged
LoRA-CLIP met it at 17.92 ms worst case; a Frozen Prefix-LM took 442 ms because of autoregressive
decoding, and its features scored 51.25% under linear probing against 85.95% for CLIP.

**M4. Determinants of Glycaemic Outcomes in Children and Adolescents with Type 1 Diabetes: A Systematic Review and Evidence Map**
*Usama Ikram (corresponding author), Abey Jose, Francisca C. Eyzaguirre, Alejandro Mac Cawley* ·
under review, *Pediatric Diabetes* · PROSPERO CRD420251045872
63 studies from 5,406 records, organised into the PEARL framework of 47 determinants across five
domains with a counted weight of evidence for each.

---

## Undergraduate research projects

| Project | Description |
|---|---|
| [Knee osteoarthritis grading](https://github.com/uikram/Knee_Osteoarthritis_Classification) | Eight-CNN ensemble with mixed voting on OAI radiographs (76.93% accuracy); Grad-CAM and LIME used to check reliance on joint space narrowing |
| [Alzheimer's early detection](https://github.com/uikram/Early-Detection-of-Alzheimer-s-Disease) | Undergraduate thesis: CNN, ridge regression and SVM models on ADNI data, deployed on a Jetson Nano |
| Industry projects | DeepChain: vibration-based predictive maintenance, autoencoder anomaly detection, Bluetooth trilateration. NASTP: RK3588 smart-camera detection, LLM-based candidate screening |

---

## Tools

Python · PyTorch · TensorFlow · Hugging Face · PEFT/LoRA · ONNX Runtime · OpenCV · C++ · CUDA · MATLAB ·
Docker · Git · hologram reconstruction (angular spectrum, Gerchberg-Saxton) · embedded inference on
RK3588 and Jetson Nano

---

*Last updated October 2026.*
