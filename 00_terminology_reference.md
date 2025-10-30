# Biosensor Data Analysis: Terminology Reference

This document provides definitions and explanations of key terms used throughout the workshop.

---

## Basic Concepts


### **Sampling Rate / Sampling Frequency**
The number of data points collected per second, measured in Hertz (Hz).
- **Example**: 200 Hz means 200 samples per second
- **Typical ECG sampling**: 200-1000 Hz
- **Typical HR sampling**: 1-4 Hz

### **Unix Timestamp**
Seconds elapsed since January 1, 1970 00:00:00 UTC. Used for precise timing.
- **Example**: 1737823379.225836
- Often includes microseconds for precision

---

## ❤️ ECG (Electrocardiogram) Basics

### **ECG / EKG**
A recording of the electrical activity of the heart. Shows characteristic waveforms for each heartbeat.

### **ECG Waveform Components**

```
           R
           |
       P   |   T
       /\  |  /\
      /  \ | /  \
     /    \|/    \
    /      +      \
   /      Q S      \
  /                 \
```

#### **P Wave**
- **What**: Atrial depolarization (atria contract)
- **Duration**: 0.08-0.10 seconds
- **Clinical**: Represents electrical activity spreading through the atria

#### **QRS Complex**
- **What**: Ventricular depolarization (main heartbeat)
- **Duration**: 0.06-0.10 seconds
- **Components**:
  - **Q wave**: First downward deflection
  - **R wave**: First upward deflection (tallest peak) ⭐
  - **S wave**: Downward deflection after R wave

#### **T Wave**
- **What**: Ventricular repolarization (ventricles relax)
- **Duration**: 0.10-0.25 seconds
- **Clinical**: Reflects recovery of ventricles

### **R-Peak**
The highest point of the QRS complex, used to identify individual heartbeats.
- Most prominent feature in ECG
- Used for heart rate calculation
- Basis for HRV analysis

---

## 💓 Cardiac Intervals and Metrics

### **RR Interval**
Time between consecutive R-peaks, measured in milliseconds (ms).
- **Also called**: NN interval (normal to normal) or IBI (interbeat interval)
- **Typical range**: 600-1200 ms (50-100 BPM)
- **Why important**: Basis for HRV analysis

### **Heart Rate (HR)**
Number of heartbeats per minute (BPM).
- **Formula**: HR = 60,000 / RR interval (ms)
- **Resting range**: 60-100 BPM
- **Athletes**: Often 40-60 BPM
- **During exercise**: Can exceed 180 BPM

### **Instantaneous Heart Rate**
Heart rate calculated from each individual RR interval, giving beat-to-beat HR values.

---

## 📈 Heart Rate Variability (HRV)

### **HRV (Heart Rate Variability)**
The variation in time intervals between consecutive heartbeats.
- **Indicates**: Autonomic nervous system function
- **Higher HRV**: Generally indicates better health and adaptability
- **Lower HRV**: Associated with stress, fatigue, or pathology

---

## HRV Metrics: Time-Domain

### **SDNN (Standard Deviation of NN Intervals)**
- **What**: Overall HRV measure
- **Units**: Milliseconds (ms)
- **Reflects**: Total autonomic influence on heart
- **Typical values**: 20-100 ms

### **RMSSD (Root Mean Square of Successive Differences)**
- **What**: Short-term HRV variability
- **Formula**: √(mean of squared differences between successive RR intervals)
- **Reflects**: Parasympathetic (vagal) activity
- **Typical values**: 20-50 ms
- **High values**: Strong parasympathetic tone

### **pNN50**
- **What**: Percentage of successive RR intervals differing by >50ms
- **Units**: Percentage (%)
- **Reflects**: Parasympathetic activity
- **Typical values**: 5-30%

### **SDSD (Standard Deviation of Successive Differences)**
- **What**: Variability of beat-to-beat changes
- **Similar to**: RMSSD
- **Reflects**: Short-term HRV

---

## 🌊 HRV Metrics: Frequency-Domain

Frequency-domain metrics analyze the power spectrum of HRV, revealing rhythmic components.

### **LF (Low Frequency Power)**
- **Frequency range**: 0.04-0.15 Hz
- **Period**: ~7-25 seconds
- **Units**: ms² or normalized units (n.u.)
- **Reflects**: Mixed sympathetic and parasympathetic activity
- **Influenced by**: Baroreflex, blood pressure regulation

### **HF (High Frequency Power)**
- **Frequency range**: 0.15-0.4 Hz
- **Period**: ~2.5-7 seconds
- **Units**: ms² or normalized units (n.u.)
- **Reflects**: Parasympathetic (vagal) activity
- **Linked to**: Respiratory sinus arrhythmia (RSA)
- **Mechanism**: HR increases during inhalation, decreases during exhalation

### **LF/HF Ratio**
- **What**: Ratio of low to high frequency power
- **Interpretation**: 
  - Higher ratio → Sympathetic dominance
  - Lower ratio → Parasympathetic dominance
- **Controversy**: Interpretation is debated in literature
- **Typical values**: 0.5-3.0

### **VLF (Very Low Frequency)**
- **Frequency range**: 0.003-0.04 Hz
- **Period**: ~25-333 seconds
- **Requires**: Long recordings (>5 minutes)
- **Reflects**: Thermoregulation, hormonal influences

### **TP (Total Power)**
- **What**: Sum of all frequency bands
- **Units**: ms²
- **Reflects**: Overall HRV

---

## 🔄 HRV Metrics: Nonlinear

### **Poincaré Plot**
A scatter plot of RR(n) vs RR(n+1) - each interval plotted against the next.
- **Shape**: "Comet" shape indicates healthy variability
- **Used to calculate**: SD1 and SD2

### **SD1**
- **What**: Short-term variability (width of Poincaré plot)
- **Formula**: SD of points perpendicular to identity line
- **Reflects**: Beat-to-beat variability
- **Related to**: RMSSD

### **SD2**
- **What**: Long-term variability (length of Poincaré plot)
- **Formula**: SD of points along identity line
- **Reflects**: Overall HRV
- **Related to**: SDNN

### **SD1/SD2 Ratio**
- **What**: Ratio of short to long-term variability
- **Lower ratio**: More long-term structure
- **Higher ratio**: More random variability

### **Sample Entropy (SampEn)**
- **What**: Measure of regularity/complexity
- **Higher values**: More irregular (healthier)
- **Lower values**: More regular/predictable

### **Detrended Fluctuation Analysis (DFA)**
- **What**: Measures fractal properties of HRV
- **α1** (short-term): 0.5-1.5 (healthy ~1.0)
- **α2** (long-term): 0.5-1.5

---

## 🔗 Physiological Synchrony

### **Synchrony**
The degree to which two or more physiological signals are coordinated in time.
- **Also called**: Concordance, co-regulation, linkage

### **Dyadic Synchrony**
Synchrony between two individuals (a dyad).
- **Common in**: Social interactions, therapy, collaboration

### **Pearson Correlation (r)**
A measure of linear relationship between two variables.
- **Range**: -1 to +1
- **+1**: Perfect positive correlation
- **0**: No linear relationship
- **-1**: Perfect negative correlation
- **For synchrony**:
  - |r| > 0.7: Strong
  - |r| > 0.4: Moderate
  - |r| > 0.2: Weak

### **Cross-Correlation**
Measures similarity between two signals as a function of time lag.
- **Positive lag**: First signal leads second
- **Negative lag**: Second signal leads first
- **Zero lag**: Synchronous

### **Windowed Analysis**
Computing metrics in overlapping time windows to see how they change over time.
- **Window size**: Duration of each analysis segment (e.g., 30 seconds)
- **Overlap**: Percentage of overlap between windows (e.g., 50%)

### **Phase Synchrony**
Measures coordination of oscillatory phases between signals.
- **Phase Locking Value (PLV)**: 0 (no synchrony) to 1 (perfect synchrony)
- **Requires**: Hilbert transform or wavelet analysis

---

## 🔬 Advanced Synchrony Metrics

### **Phase Locking Index (PLI)**
- **What**: Measures consistency of phase relationship between two oscillating signals
- **Range**: 0 (no phase locking) to 1 (perfect phase locking)
- **How computed**: Hilbert transform extracts instantaneous phase from each signal
- **Reflects**: Oscillatory coupling between participants
- **Advantage**: Captures rhythmic coordination beyond simple correlation
- **Use case**: Detecting synchronized breathing-related heart rate patterns

### **Coherence**
- **What**: Frequency-domain correlation between two signals
- **Range**: 0 to 1 for each frequency
- **Computed via**: Welch's method on power spectral densities
- **Output**: Coherence spectrum showing coupling strength at each frequency
- **Interpretation**:
  - High coherence in HF band (0.15-0.4 Hz): Respiratory coupling
  - High coherence in LF band (0.04-0.15 Hz): Baroreflex synchronization
- **Advantage**: Identifies which specific frequency bands show strongest coupling
- **Differs from correlation**: Correlation is time-domain; coherence is frequency-specific

### **Envelope Correlation**
- **What**: Correlation of signal amplitude envelopes (ignoring phase)
- **Measures**: Co-modulation of signal amplitudes over time
- **How computed**: Hilbert transform to extract instantaneous amplitude, then correlate
- **Reflects**: Whether both participants' physiological arousal increases/decreases together
- **Use case**: Detecting co-regulation of arousal levels independent of exact timing

### **Granger Causality**
- **What**: Statistical test of whether past values of X improve predictions of Y
- **Question answered**: "Does knowing X's history help predict Y's future?"
- **Important distinction**: "Granger causality" ≠ true causality (it's predictive relationship)
- **Bidirectional testing**: Test both X→Y and Y→X separately
- **Result**: Can be unidirectional, bidirectional, or no causality
- **Use case**: Leader-follower analysis in dyadic interactions
- **Requirements**: Requires longer time series (typically >100 samples) and stationary data

### **Cross-Recurrence Quantification Analysis (CRQA)**
- **What**: Analyzes recurrent patterns between two nonlinear time series
- **Purpose**: Captures complex, nonlinear coordination that linear methods miss
- **Key metrics**:
  - **RR (Recurrence Rate)**: Percentage of recurrent states (0-1)
  - **DET (Determinism)**: Percentage of recurrent points forming diagonal lines
  - **L (Average Diagonal Line)**: Mean length of diagonal structures
  - **LMAX (Longest Diagonal Line)**: Maximum diagonal line length
  - **ENT (Entropy)**: Shannon entropy of diagonal line distribution
  - **LAM (Laminarity)**: Percentage of recurrent points in vertical structures
- **Interpretation**:
  - Higher DET: More predictable coordination patterns
  - Longer L: More stable coupling episodes
  - Higher ENT: More complex coordination repertoire
- **Requires**: PyRQA package, careful parameter selection
- **Use case**: Complex social interactions, developmental studies, therapy dyads

### **Dyadic Poincaré Plot**
- **What**: Scatter plot of Participant 1's RR intervals vs Participant 2's RR intervals at each moment
- **Differs from individual Poincaré**: Individual plots RR(n) vs RR(n+1) for one person
- **What to look for**:
  - **Points near identity line**: Both participants have similar heart rates at that moment
  - **Tight clustering**: Stable, consistent coordination
  - **Wide scatter**: Variable/loose coordination
  - **Correlation strength**: Quantifies coupling (r > 0.5 = strong)
  - **Systematic offset**: One participant consistently faster/slower
- **Extensions**: Can compute lag-1 dyadic correlations for directionality
- **Use case**: Visualizing moment-to-moment cardiac coupling

### **Bland-Altman Plot** (for dyadic analysis)
- **What**: Plots mean RR vs difference in RR between two participants
- **X-axis**: (RR₁ + RR₂) / 2
- **Y-axis**: RR₁ - RR₂
- **Purpose**: Assess agreement and systematic bias between participants
- **Key features**:
  - **Mean difference line**: Shows systematic offset
  - **±1.96 SD lines**: 95% limits of agreement
  - **Points outside limits**: Moments of large discordance
- **Use case**: Identifying periods where participants are out of sync

---

## 🔧 Signal Processing Terms

### **Baseline Wander**
Low-frequency drift in the ECG signal, often due to:
- Respiration
- Body movement
- Electrode contact changes

### **Artifacts**
Unwanted signals or noise in the data:
- **Motion artifacts**: From movement
- **Electrode artifacts**: Poor contact
- **Powerline interference**: 50/60 Hz electrical noise
- **Muscle artifacts**: EMG contamination

### **Filtering**
Removing unwanted frequencies from a signal:
- **High-pass filter**: Removes low frequencies (baseline wander)
- **Low-pass filter**: Removes high frequencies (noise)
- **Band-pass filter**: Keeps only frequencies in a range
- **Notch filter**: Removes specific frequency (e.g., 60 Hz powerline)

### **Signal-to-Noise Ratio (SNR)**
Ratio of desired signal power to noise power.
- **Higher SNR**: Cleaner signal
- **Measured in**: Decibels (dB)

### **Interpolation**
Estimating values between known data points.
- **Linear**: Straight line between points
- **Cubic spline**: Smooth curve through points
- **Why needed**: Creating evenly-spaced time series from irregular beat data

---

## 🧠 Autonomic Nervous System (ANS)

### **ANS**
The part of the nervous system controlling involuntary functions (heart rate, digestion, etc.).

### **Sympathetic Nervous System**
- **Function**: "Fight or flight" response
- **Effects on heart**: Increases heart rate, decreases HRV
- **Associated with**: Stress, arousal, activity

### **Parasympathetic Nervous System (Vagal)**
- **Function**: "Rest and digest" response  
- **Effects on heart**: Decreases heart rate, increases HRV
- **Primary nerve**: Vagus nerve
- **Associated with**: Relaxation, recovery, social engagement

### **Vagal Tone**
The degree of vagal nerve activity.
- **High vagal tone**: Better emotional regulation, health
- **Measured by**: HF power, RMSSD

### **Respiratory Sinus Arrhythmia (RSA)**
Normal variation in heart rate during breathing.
- **Inhalation**: HR increases (vagal withdrawal)
- **Exhalation**: HR decreases (vagal activation)
- **Reflects**: Parasympathetic function
- **Captured by**: HF component of HRV

---

## 📱 Sensor-Specific Terms

### **Sensor ID**
Unique identifier for each biosensor device (e.g., 234130000540).
- **Important**: Map to participant identities in your records

### **Annotations File**
Contains timing markers for events during recording:
- Recording start/stop
- Experiment phase markers
- Audio/video annotation start/stop

### **Pre-computed vs. Raw Data**
- **Pre-computed**: Processed by sensor (e.g., HR values)
  - Pros: Fast, ready to use
  - Cons: Limited control, less detail
- **Raw**: Unprocessed signal (e.g., ECG samples)
  - Pros: Full control, beat-to-beat precision
  - Cons: Requires preprocessing

---

## Methodological Considerations

### **Stationarity**
Assumption that statistical properties don't change over time.
- **Important for**: Frequency-domain HRV analysis
- **Requires**: Relatively stable conditions

### **Artifact Correction**
Removing or correcting invalid beats:
- **Ectopic beats**: Abnormal heartbeats
- **Missed beats**: R-peaks not detected
- **False detections**: Noise detected as R-peak

---

## 🎓 Best Practices

### **Data Quality Assessment**
Always visually inspect:
- Raw signals for artifacts
- R-peak detection accuracy
- Distribution of RR intervals

### **Participant Instructions**
For clean data:
- Minimize movement
- Relax muscles
- Maintain steady breathing (or track it)
- Proper electrode placement

### **Reporting Standards**
When publishing, report:
- Sensor type and placement
- Sampling rate
- Preprocessing methods
- HRV analysis parameters
- Statistical methods

---

## Quick Reference: Typical Values

| Metric | Typical Range | Units |
|--------|---------------|-------|
| Resting HR | 60-100 | BPM |
| RR Interval | 600-1200 | ms |
| SDNN | 20-100 | ms |
| RMSSD | 20-50 | ms |
| pNN50 | 5-30 | % |
| LF | 500-2000 | ms² |
| HF | 500-2000 | ms² |
| LF/HF | 0.5-3.0 | ratio |

*Note: Values vary by age, fitness, context*

---

## 🔍 Common Abbreviations

- **ANS**: Autonomic Nervous System
- **BPM**: Beats Per Minute
- **DFA**: Detrended Fluctuation Analysis
- **ECG/EKG**: Electrocardiogram
- **EDA**: Electrodermal Activity
- **HF**: High Frequency
- **HR**: Heart Rate
- **HRV**: Heart Rate Variability
- **IBI**: Inter-Beat Interval
- **LF**: Low Frequency
- **ms**: milliseconds
- **NN**: Normal-to-Normal (RR interval)
- **PLV**: Phase Locking Value
- **PPG**: Photoplethysmography
- **RMSSD**: Root Mean Square of Successive Differences
- **RSA**: Respiratory Sinus Arrhythmia
- **SDNN**: Standard Deviation of NN intervals
- **SNR**: Signal-to-Noise Ratio
- **VLF**: Very Low Frequency

---
