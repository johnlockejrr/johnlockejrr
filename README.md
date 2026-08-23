# 👋 Hi there, I'm John Locke Jr. (Teodor Bors)

## 🎯 **Multilingual AI Researcher & Semitic Language Specialist**

I'm passionate about **Natural Language Processing**, **Semitic linguistics**, and **AI optimization**. My work spans Hebrew, Aramaic, Syriac, and Samaritan text processing, with expertise in eGPU optimization, transformer architectures, and historical text digitization — including **set-prediction baseline detection** and PAGE/ALTO export for HTR pipelines.

**ORCID:** [0009-0005-0365-6608](https://orcid.org/0009-0005-0365-6608) · **Zenodo preprint:** [doi:10.5281/zenodo.22059333](https://doi.org/10.5281/zenodo.22059333)

---

## 🚀 **Current Projects & Research**

### 📐 **regnetx-det — Polyline Baseline Detection for Historical Documents**
**Set-prediction detector** that outputs B-spline polyline baselines directly: RegNetX-8GF, RT-DETR-style HybridEncoder, and PolylineTransformer with native PAGE/ALTO export.

- **Paper:** [Zenodo preprint](https://doi.org/10.5281/zenodo.22059333) — architecture & transfer study (not a cBAD hidden-test leaderboard claim)
- **Code:** [`johnlockejrr/regnetx-det`](https://github.com/johnlockejrr/regnetx-det)
- **Stage-0 weights:** [`regnetx-8gf-polyline-baseline-stage0`](https://huggingface.co/johnlockejrr/regnetx-8gf-polyline-baseline-stage0) (multiscript pretrain; Gradio [demo](https://huggingface.co/spaces/johnlockejrr/regnetx-8gf-polyline-baseline-stage0))
- **Hebrew/Samaritan FT:** [`regnetx-8gf-polyline-hebrew-samaritan`](https://huggingface.co/johnlockejrr/regnetx-8gf-polyline-hebrew-samaritan) (`cbad_f1_max` ≈ **0.969** on internal val)
- **Highlights:** HybridEncoder vs FPN neck ablation; native Stage-0 vs D-FINE warm-start; cBAD 2019 **eval** Stage-0 Chamfer F1 **0.907**
- **Siblings:** [`dfine-det`](https://github.com/johnlockejrr/dfine-det), [`convnextv2-det`](https://github.com/johnlockejrr/convnextv2-det), plus hardened BLLA-style polygon export across det/seg packages in the oxygraphos-ocr workspace

### 🔤 **Unikud - Advanced Hebrew NLP System**
**Complete Hebrew text processing pipeline** with advanced nikud restoration capabilities using transformer-based models.

- **Model Architecture**: Custom CANINE-based models optimized for Hebrew
- **eGPU Optimization**: Specialized training scripts for RTX 3090 with Thunderbolt 3.0
- **Datasets**: Mishnaic, Rabbinic, and Modern Hebrew text processing (100K+ samples)
- **Performance**: Memory-efficient training with GPU-cached datasets
- **Applications**: Biblical text analysis, modern Hebrew processing, educational tools

### 🕊️ **Samaritan-Aramaic Translation Models**
**Complete pipeline for fine-tuning MarianMT models** on Hebrew-Aramaic parallel texts, specifically designed for translating between Hebrew (Samaritan) and Aramaic (Targum) texts.

- **Translation Models**: Hebrew ↔ Aramaic bidirectional translation
- **Custom Tokenizers**: Specialized for Semitic languages
- **Dataset Engineering**: Aligned corpus processing and quality analysis
- **Model Optimization**: Early stopping, learning rate scheduling, mixed precision training
- **Applications**: Biblical studies, linguistic research, text preservation

### 📚 **Targumic Aramaic Diacritizer**
**Character-level diacritization** of Targumic Aramaic text using lightweight BiLSTM + Attention architecture.

- **Model Architecture**: 1-layer BiLSTM encoder, LSTM decoder with Luong-style attention
- **Training Data**: ~15,000 aligned verses from Targum Onkelos
- **Performance**: Lightweight model suitable for deployment
- **Applications**: Biblical text vocalization, linguistic research, educational tools

### 🔍 **Post-OCR Correction Systems**
**Advanced OCR post-processing** for historical and medieval texts across multiple languages.

- **Multi-language Support**: Swedish, medieval texts, various scripts
- **Architectures**: BiLSTM, CATMuS-medieval, custom OCR correction models
- **Applications**: Historical document digitization, manuscript preservation, research accessibility

### 🖼️ **Kraken HTR Training & Deployment**
**Handwritten Text Recognition (HTR) system** using Kraken framework for historical manuscripts.

- **Model Training**: Custom HTR models for specific scripts and languages
- **Segmentation**: Advanced page segmentation and text recognition
- **Deployment**: Web applications and API services for HTR
- **Applications**: Manuscript digitization, historical research, cultural preservation

### 🌟 **Samaritan Torah Search Platform**
**Modern web interface** for searching Samaritan Torah text, built with React and FastAPI.

- **Search Features**: Fuzzy matching, exact phrase matching, pagination
- **Responsive Design**: Mobile-friendly interface with Hebrew text support
- **Backend**: FastAPI with Elasticsearch integration
- **Applications**: Biblical research, text study, educational platforms

### 🔒 **Oxygraphos stack & Marian toolkit** *(in active development — private / not public yet)*

These are current local workstreams feeding the open `regnetx-det` releases above. Repos are private for now; descriptions reflect working code.

#### **oxygraphos-ocr** — unified historical OCR / layout workspace
Single `uv` workspace that installs many sibling engines under one CLI style (detectors, segmenters, line recognizers). Includes polyline baseline detectors (`regnetx-det`, `dfine-det`, `convnextv2-det`), segmentation packages (`blla-seg`, `dfine-seg`, `docufcn-seg`, `surya-seg`, `rfdetr-seg`, …), and HTR/OCR recognizers (RepViT, Nemo, PyLaia, Loghi, HTR-VT, PP-OCRv6, …), plus shared hardened PAGE/ALTO polygon export.

#### **oxygraphos-atr** — Automatic Text Recognition workspace
Local-first **ATR** platform (eScriptorium-inspired): projects, async jobs (Redis/RQ), multi-user auth with GPU isolation, and in-workspace recognition using engines from `oxygraphos-ocr` (RepViT, Nemo, PyLaia, Loghi + optional KenLM). Segmentation / baseline models (BLLA, D-FINE, RegNetX, Doc-UFCN, …) plug in as adapters. FastAPI backend + SvelteKit frontend.

#### **oxygraphos-annotator** — PAGE/ALTO annotation UI
Local-first **annotation** app for scanned pages: regions, baselines, optional polygonize, transcription, LTR/RTL projects, ZIP/RAR import, PAGE-like XML export. FastAPI + SQLAlchemy/SQLite + SvelteKit. Complements ATR by focusing on layout/transcription labeling rather than full job orchestration.

#### **marian 1.3.0** (`marianmt-heb-arc`) — Biblical Hebrew ↔ Aramaic / Syriac MT
Installable `marian` CLI/library for MarianMT Semitic translation: train, serve, evaluate, checkpoint averaging. Bidirectional **Hebrew ↔ Targumic Aramaic** and **Hebrew ↔ Classical Syriac** models (chained fine-tunes from `opus-mt-sem-sem`). Example held-out scores: heb→arc BLEU **45.1** / chrF **64.3**; arc→heb BLEU **61.1** / chrF **74.2**.

---

## 🛠️ **Technical Expertise**

### **Programming Languages & Frameworks**
- **Python**: PyTorch, TensorFlow, FastAPI, Streamlit, Gradio
- **JavaScript/TypeScript**: React, Node.js, modern web development
- **C++/Rust**: Performance-critical applications and systems programming
- **SQL/NoSQL**: Database design and optimization

### **AI/ML Technologies**
- **Deep Learning**: PyTorch, Transformers (Hugging Face), TensorFlow, Keras
- **NLP Models**: MarianMT, CANINE, BiLSTM, Attention mechanisms
- **Document / layout detectors**: DETR-style set prediction, HybridEncoder, polyline baselines (RegNetX / D-FINE / ConvNeXt)
- **Computer Vision**: OCR, HTR, image processing with Kraken; PAGE-XML / ALTO export
- **Model Optimization**: Mixed precision training, gradient checkpointing, early stopping

### **eGPU & Hardware Optimization**
- **RTX 3090 24GB** optimization for large-scale training
- **Thunderbolt 3.0** bandwidth management and optimization
- **Memory-efficient training** strategies for large datasets
- **GPU-cached datasets** and distributed training
- **AMD Instinct MI300X** (ROCm) for multiscript Stage-0 pretraining

### **Semitic Language Processing**
- **Hebrew**: Biblical, Mishnaic, Modern Hebrew with nikud restoration
- **Aramaic**: Targumic, Syriac, and various Aramaic dialects
- **Samaritan**: Samaritan Hebrew script and text processing
- **Unicode normalization** and **text segmentation** for Semitic scripts

---

## 🔬 **Research Areas & Specializations**

### **Semitic Linguistics & NLP**
- **Biblical Hebrew** text analysis and processing
- **Targumic Aramaic** translation and diacritization
- **Samaritan Hebrew** script recognition and processing
- **Syriac Aramaic** language models and translation
- **Cross-lingual** Semitic language processing

### **AI Model Optimization**
- **Memory-efficient training** for large-scale datasets (100K+ samples)
- **eGPU performance** optimization for external GPU setups
- **Mixed precision** training strategies (bfloat16, fp16)
- **Gradient checkpointing** and advanced memory management

### **Historical Text Digitization**
- **OCR post-processing** for medieval and historical manuscripts
- **Handwritten Text Recognition (HTR)** for various scripts
- **Baseline / polyline detection** for line-level HTR pipelines
- **Text cleaning** and normalization for ancient languages
- **Dataset creation** for historical text corpora

### **Web Applications & Deployment**
- **Modern web interfaces** for linguistic research tools
- **API development** for NLP services
- **Docker containerization** and production deployment
- **Responsive design** with multilingual text support

---

## 📊 **Recent Achievements & Impact**

- ✅ **Published regnetx-det preprint** on Zenodo ([doi:10.5281/zenodo.22059333](https://doi.org/10.5281/zenodo.22059333)) with HF weights and Gradio demo
- ✅ **Released Stage-0 + Hebrew/Samaritan polyline checkpoints** for historical baseline detection
- ✅ **Hardened PAGE/ALTO polygon export** (BLLA-derived carver + baseline containment) across detector siblings
- ✅ **Building private Oxygraphos ATR / OCR / annotator stack** and Marian Semitic MT toolkit (not public yet)
- ✅ **Developed comprehensive Hebrew NLP system** with eGPU optimization
- ✅ **Created bidirectional Hebrew-Aramaic translation models** for biblical studies
- ✅ **Built lightweight Aramaic diacritizer** using BiLSTM + Attention
- ✅ **Implemented advanced OCR correction** for multiple languages and scripts
- ✅ **Deployed HTR system** for historical manuscript processing
- ✅ **Created modern web platform** for Samaritan Torah research
- ✅ **Optimized training pipelines** for memory efficiency and speed
- ✅ **Processed large-scale datasets** (100K+ samples) with custom preprocessing

---

## 🌟 **Featured Projects & Repositories**

### **[regnetx-det](https://github.com/johnlockejrr/regnetx-det)**
Set-prediction polyline baselines for historical documents (HybridEncoder transfer). Paper: [Zenodo](https://doi.org/10.5281/zenodo.22059333). Weights: [Stage-0](https://huggingface.co/johnlockejrr/regnetx-8gf-polyline-baseline-stage0), [Hebrew/Samaritan](https://huggingface.co/johnlockejrr/regnetx-8gf-polyline-hebrew-samaritan).

### **[Unikud - Hebrew NLP System](https://github.com/johnlockejrr/unikud)**
Complete Hebrew text processing pipeline with advanced nikud restoration, eGPU optimization, and large-scale dataset processing.

### **[Samaritan-Aramaic Translation](https://github.com/johnlockejrr/sam-aram)**
Complete pipeline for fine-tuning MarianMT models on Hebrew-Aramaic parallel texts with custom tokenizers and optimization strategies.

### **[Targumic Aramaic Diacritizer](https://github.com/johnlockejrr/BiLSTM_Attention_diacritization)**
Lightweight BiLSTM + Attention model for character-level diacritization of Targumic Aramaic text.

### **[Post-OCR Correction Systems](https://github.com/johnlockejrr/Post-OCR)**
Advanced OCR post-processing for historical texts across multiple languages and scripts.

### **[Kraken HTR Training](https://github.com/johnlockejrr/kraken-train)**
Handwritten Text Recognition system using Kraken framework for historical manuscript processing.

### **[Samaritan Torah Search](https://github.com/johnlockejrr/samaritanus)**
Modern web interface for searching Samaritan Torah text with React, FastAPI, and Elasticsearch.

### **Private / in progress** *(no public repo links yet)*
`oxygraphos-ocr` · `oxygraphos-atr` · `oxygraphos-annotator` · `marian` (`marianmt-heb-arc`) — see **Current Projects** above.

---

## 🔗 **Connect & Collaborate**

- **GitHub**: [@johnlockejrr](https://github.com/johnlockejrr)
- **Hugging Face**: [@johnlockejrr](https://huggingface.co/johnlockejrr)
- **ORCID**: [0009-0005-0365-6608](https://orcid.org/0009-0005-0365-6608)
- **Zenodo**: [regnetx-det preprint](https://doi.org/10.5281/zenodo.22059333)
- **Research Focus**: Semitic NLP, historical document AI (baselines / HTR / OCR), AI optimization, eGPU computing

---

## 📈 **GitHub Statistics**

<!-- Official successor of github-readme-stats (public vercel.app instance is DEPLOYMENT_PAUSED). Verified 2026-08-23. -->
![John's GitHub stats](https://github-stats-extended.vercel.app/api?username=johnlockejrr&show_icons=true&theme=radical)

![Top Languages](https://github-stats-extended.vercel.app/api/top-langs/?username=johnlockejrr&layout=compact&theme=radical)

---

## 🎯 **Current Research Focus**

Currently working on:
- **Polyline baseline detection** (regnetx-det / dfine-det / convnextv2-det) and PAGE/ALTO export hardening
- **Multiscript Stage-0 pretraining** and Hebrew/Samaritan domain fine-tuning
- **Oxygraphos private stack** — `oxygraphos-ocr` (engine workspace), `oxygraphos-atr` (ATR jobs + recognition), `oxygraphos-annotator` (PAGE/ALTO labeling)
- **MarianMT Semitic MT toolkit** (`marian` / `marianmt-heb-arc`) — Hebrew ↔ Aramaic / Syriac train–serve–eval
- **Advanced Semitic language model training** with eGPU / accelerator optimization
- **Large-scale historical text dataset** creation and preprocessing
- **Cross-lingual Semitic language** processing and translation
- **Memory-efficient training strategies** for transformer models
- **Historical manuscript digitization** and text recognition
- **Web platform development** for linguistic research tools

---

## 💡 **Collaboration Opportunities**

I'm always interested in:
- **Semitic linguistics research** collaborations
- **Historical text digitization** projects
- **Baseline detection / HTR** and document layout AI
- **AI model optimization** for ancient languages
- **eGPU computing** challenges and optimization
- **Cross-cultural linguistic** research partnerships
- **Open-source NLP tool** development

Feel free to reach out if you'd like to work together on Semitic language processing, historical text digitization, AI optimization, or any other exciting projects!

---

## 🌍 **Impact & Vision**

My work focuses on **preserving and making accessible** ancient Semitic texts through modern AI technology. By combining **linguistic expertise** with **cutting-edge machine learning**, I aim to:

- **Bridge ancient and modern** through technology
- **Preserve cultural heritage** through digital means
- **Advance linguistic research** with AI tools
- **Make historical texts accessible** to researchers worldwide
- **Develop sustainable solutions** for text preservation

---

*"Language is the key to understanding culture, and AI is the key to processing language at scale. When we combine both, we unlock the wisdom of the ages."* 🚀📚🕊️
