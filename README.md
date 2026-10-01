# Continual Learning Framework for Industry 4.0 Predictive Maintenance

> **Official Implementation** of a supervised online machine learning computational methodological framework designed for real-time predictive maintenance and multi-label alarm prediction in dynamic industrial environments.

By adapting and optimizing the **BAT-OCDM** rehearsal strategy (centered on dynamic memory management), this framework effectively combats **catastrophic forgetting** and **concept drift** without requiring costly full offline retraining.

---

## 📌 Key Features

* **Online & Continual Learning:** Operates under a Domain Incremental Learning paradigm for streaming industrial data.
* **Efficient Memory Management:** Features a dynamic update mechanism maintaining $O(1)$ time complexity to prevent latency spikes during real-time processing.
* **Drift-Triggered Updates:** Integrates Early Concept Drift Detection (ECDD) to execute intensive retraining only when distribution shifts occur, saving computation and filtering sparse fault noise.
* **Multi-Label Alarm Prediction:** Solves complex multi-label classification tasks across highly unbalanced industrial time windows.
* **Optimized Architecture Variants:**
  * `BAT-OCDM MOD123`: Structural architectural optimizations to the base model.
  * `BAT-OCDM ECDD`: Integrated drift detection for adaptive retraining.
  * `BAT-OCDM KD-Rules`: Enhanced with Knowledge Distillation and expert domain rules.

---

## 📊 Datasets & Benchmark Setup

The framework is evaluated on two public, real-world Industry 4.0 datasets:

### 1. ALPI (*Alarm Logs in Packaging Industry*)
* **Scope:** 20 packaging machines globally across 16 months (14 machines selected for sequential tasks).
* **Task:** Multi-label classification forecasting future alarm occurrences.
* **Feature Representation:**
  * **Input ($x$):** Normalized counts of 154 distinct alarm codes over a 1,720-minute input window.
  * **Output ($y$):** $N$-hot encoded vector indicating active alarms in a subsequent 480-minute window.
* **Evaluation:** Grouped frequency analysis (High, Medium, Low) to address severe class imbalance.

### 2. PdM_errors (*Microsoft Azure Predictive Maintenance*)
* **Scope:** Hourly telemetry and operational log data from 100 industrial machines across 2015 (`PdM_errors.csv`).
* **Task:** Detection and prediction of non-obstructive operational anomalies (`error1` to `error5`).
* **Objective:** Assesses model resilience against soft fault dynamics in continuously operating machinery.

---

## 📈 Benchmark Results

* **Top Performance:** The **BAT-OCDM ECDD** variant achieved the best performance balance over baseline methods (standard OCDM and Reservoir Sampling).
* **Scalability:** Maintained good memory update latency during streaming inference, avoiding execution spikes seen in standard OCDM implementations.
* **Resource Efficiency:** Reduced overall compute overhead by suppressing retraining on transient noise while rapidly reacting to systemic failures.
