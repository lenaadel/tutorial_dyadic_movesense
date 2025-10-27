# tutorial_dyadic_movesense
Repository made for movesense cardiac data tutorial


## Workshop Overview

This hands-on workshop provides a comprehensive pipeline for analyzing physiological data from movesense biosensors, with a focus on ECG preprocessing and heart rate variability (HRV) analysis for dyadic synchrony studies.

**Duration**: 60 minutes  
**Level**: Intermediate (basic Python/pandas knowledge required)  
**Focus**: Cardiac synchrony analysis in dyadic interactions

---

## Repository Structure

```
tutorial_dyadic_movesense/
├── README.md (this file)
├── QUICKSTART.md
├── 00_terminology_reference.md
├── 01_data_loading_and_exploration.ipynb
├── 02_quick_pipeline_precomputed_HR.ipynb
├── 03_full_pipeline_ECG_processing.ipynb
├── 04_modular_synchrony_analysis.ipynb
├── 04b_dyadic_poincare_and_leader_follower.ipynb
├── data/
│   ├── 234130000540/ (Participant 1 sensor folder)
│   │   ├── ECG-2025_01_25-16_42_59.csv
│   │   ├── HR-2025_01_25-16_42_59.csv
│   │   └── ACC-2025_01_25-16_42_59.csv
│   ├── 234130000594/ (Participant 2 sensor folder)
│   │   ├── ECG-2025_01_25-16_42_59.csv
│   │   ├── HR-2025_01_25-16_42_59.csv
│   │   └── ACC-2025_01_25-16_42_59.csv
│   └── Annotations-2025_01_25-16_42_59.csv
├── processed_data/ (created by Notebook 01)
├── analysis_results/ (created by Notebook 03)
└── requirements.txt
```

---

## Learning Objectives

By the end of this workshop, you will be able to:

1. **Load and organize** biosensor data from multiple participants
2. **Understand** ECG signal components and cardiac metrics
3. **Implement two analysis pipelines**:
   - Quick pipeline using pre-computed heart rate
   - Comprehensive pipeline with raw ECG preprocessing
4. **Compute physiological synchrony** between participants
5. **Make informed decisions** about which pipeline to use for your research

---

## Workshop Structure

### **Notebook 1: Data Loading and Exploration** (10 min)
- Understanding folder structure and file formats
- Loading annotations and defining experimental windows
- Visual inspection of raw ECG signals
- Data quality assessment

**Key Concepts**: Unix timestamps, ECG waveforms, sampling rates

---

### **Notebook 2: Quick Pipeline** (15 min)
- Working with pre-computed heart rate data
- Computing correlation-based synchrony
- Windowed synchrony analysis
- Cross-correlation for leader-follower dynamics

**Key Concepts**: HR vs IBI, Pearson correlation, temporal dynamics

**Use Cases**: 
- Real-time neurophenomenology
- Rapid exploratory analysis
- Prototyping synchrony metrics

---

### **Notebook 3: Full ECG Processing Pipeline** (25 min)
- ECG signal cleaning with NeuroKit2
- R-peak detection
- Computing RR intervals
- Comprehensive HRV analysis (time, frequency, nonlinear domains)
- R-peak based synchrony metrics

**Key Concepts**: Signal processing, HRV metrics, LF/HF components

**Use Cases**:
- Research publications
- Detailed physiological analysis
- When you need beat-to-beat precision

---

### **Wrap-up** (10 min)
- Comparing pipeline results
- Q&A and discussion
- Next steps for your research

---

## Additional Notebooks (Post-Workshop)

### **Notebook 4: Modular Synchrony Analysis Framework**
- Flexible framework for computing multiple synchrony metrics
- Methods: Correlation, Cross-correlation, Coherence, PLI, Envelope, CRQA
- Easy to extend with new methods
- Windowed analysis support
- Batch processing capabilities

**Key Concepts**: Multiple synchrony methods, modular design, advanced metrics

**Use Cases**:
- Comparing different synchrony approaches
- Comprehensive physiological coupling analysis
- Custom metric development

---

### **Notebook 4b: Dyadic Poincaré and Leader-Follower Analysis**
- Overlaid Poincaré plots for dyadic comparison
- Temporal evolution of synchrony patterns
- Windowed dyadic analysis (30-second segments)
- Visual tracking of coordination dynamics

**Key Concepts**: Poincaré plots, dyadic patterns, temporal dynamics

**Use Cases**:
- Visualizing dyadic HRV patterns
- Tracking coordination changes over time
- Understanding beat-to-beat dyadic coupling

---

## Installation

### Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Required Packages

```bash
pip install pandas numpy matplotlib scipy neurokit2
```

Or use the provided requirements file:

```bash
pip install -r requirements.txt
```

---

## Data Format

### Folder Structure
Each recording session has:
- **Sensor folders**: Named with sensor IDs (e.g., 234130000540)
- **Annotations file**: Contains timing information for the experiment
- **Multiple modalities** per sensor:
  - `ECG-*.csv`: Raw ECG signal (~200 Hz)
  - `HR-*.csv`: Pre-computed heart rate (~2 Hz)
  - `Temperature-*.csv`, `Acc-*.csv`, etc. (not used in this workshop)

### Important: Participant Mapping
⚠️ **You must maintain a separate log** mapping sensor IDs to participant identities!

Example:
```
Sensor 234130000540 → Participant A (experimenter)
Sensor 234130000594 → Participant B (subject)
```

---

## 🎓 Key Terminology

See `00_terminology_reference.md` for detailed definitions of:
- ECG components (P, Q, R, S, T waves)
- Cardiac intervals (RR, PR, QT)
- HRV metrics (SDNN, RMSSD, LF, HF)
- Synchrony measures

---

## Getting Started

### Quick Start

1. **Clone or download** this repository
2. **Install dependencies**: `pip install -r requirements.txt`
3. **Place your data** in the `data/` folder if you want to use your own.
4. **Open** `01_data_loading_and_exploration.ipynb`
5. **Follow along** with the workshop!

### Using Your Own Data

To use your own biosensor data:

1. Organize your data following the structure shown above
2. Update the `data_dir` path in Notebook 1
3. Update the sensor IDs in the participant mapping
4. Run through the notebooks!

---

## Pipeline Comparison

| Feature | Quick Pipeline | Full Pipeline |
|---------|---------------|---------------|
| **Speed** | Fast (seconds) | Slower (minutes) |
| **Input** | Pre-computed HR | Raw ECG |
| **Preprocessing** | None needed | Signal cleaning |
| **HRV Metrics** | Limited | Comprehensive |
| **Precision** | ~2 Hz | Beat-to-beat |
| **Use Case** | Real-time, exploratory | Research, detailed analysis |

---

## Tips for Success

### For Workshop Facilitators:
- **Pre-run all notebooks** to verify they work
- **Prepare backup data** in case of issues
- **Have examples ready** of good vs. poor quality signals
- **Budget 5 extra minutes** for Q&A
- **Encourage hands-on practice** in the "Try It Yourself" sections

### For Participants:
- **Follow along actively** - run each cell as we go
- **Ask questions** when concepts are unclear
- **Experiment** with parameters in the exercises
- **Take notes** on which approaches work for your research
- **Save your modified notebooks** for future reference

---

## Advanced Topics (Beyond Workshop)

Once comfortable with the basics, explore:

1. **Advanced Synchrony Metrics** (See Notebook 4):
   - Phase synchrony (Hilbert transform) - PLI method
   - Coherence analysis (frequency-domain)
   - Cross-recurrence (CRQA)
   - Envelope correlation
   - Granger causality
   - Dynamic Time Warping

2. **Dyadic Visualization** (See Notebook 4b):
   - Overlaid Poincaré plots
   - Windowed dyadic patterns
   - Temporal evolution tracking

3. **Multivariate Analysis**:
   - Combining ECG with EDA (electrodermal activity)
   - Respiratory sinus arrhythmia
   - Multi-modal synchrony

4. **Statistical Analysis**:
   - Significance testing for synchrony
   - Comparing synchrony across conditions
   - Mixed-effects models

5. **Real-time Implementation**:
   - Streaming data processing
   - Online R-peak detection
   - Live synchrony visualization

---

## References and Further Reading

### NeuroKit2
- Documentation: https://neuropsychology.github.io/NeuroKit/
- Paper: Makowski et al. (2021). *NeuroKit2: A Python toolbox for neurophysiological signal processing*

### PyRQA
- Documentation: https://pypi.org/project/PyRQA/8.1.0/
- The underlying computational approach of PyRQA is described in detail within the following thesis, which is openly accessible at https://edoc.hu-berlin.de/handle/18452/19518. Rawald, T. (2018): Scalable and Efficient Analysis of Large High-Dimensional Data Sets in the Context of Recurrence Analysis, PhD Thesis, Berlin : Humboldt-Universität zu Berlin, 299 p.

---


## License

This workshop material is provided for training purposes but please cite appropriately if you use these materials in your research. 

---

## Acknowledgments

This workshop was designed for researchers working with biosensor data in social neuroscience, neurophenomenology, and dyadic interaction studies.

**** 
