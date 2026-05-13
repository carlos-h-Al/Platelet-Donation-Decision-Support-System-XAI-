# Autonomous Platelet Apheresis: Multi-Model Orchestration (MMO) System

This repository contains the implementation of a specialized **Multi-Model Orchestration (MMO)** system designed to manage simulated platelet donations. The system transitions AI from static risk prediction to an active clinical management framework, capable of adjusting apheresis parameters in real-time to mitigate complications.

## 🚀 Overview

Escalating talent retention challenges in the medical sector (notably within the NHSBT) have increased the vulnerability of specialist expertise required for platelet and plasma apheresis. The MMO system addresses this by:
- **Autonomous Management:** Adjusting apheresis parameters (e.g., citrate infusion, flow rates) in real-time.
- **Explainability:** Utilizing the **SHAP (SHapley Additive exPlanations)** framework to ensure every intervention is mathematically explainable.
- **Natural Interaction:** Combining Small and Large Language Models (LLMs) with text embeddings to translate unstructured donor feedback into executable machine adjustments.

## 🏗️ Architecture

The system is built on a modular "Multi-Model Orchestration" architecture:
1.  **Core Model:** An **eXtreme Gradient Boosting (XGB)** model that serves as the decision-making engine for clinical adjustments.
2.  **LLM Integration:** Interprets donor symptoms from natural language input.
3.  **Text Embeddings:** Maps donor feedback to specific physiological states.
4.  **Edge Deployment:** Designed for local execution (offline) to ensure zero-latency and data privacy.

## 📊 Key Features

-   **Synthetic Dataset Engineering:** Trained on a rigorously engineered synthetic dataset embedded with expert clinical heuristics to overcome data scarcity and privacy constraints.
-   **Noise injection:**
  
  1. **Label noise:** Label noise introduces gularisation, forcing the model to look for the consensus of features.
    
  2. **Sensor jitter (Gaussian noise):** As no medical sensor is perfectly precise, Gaussian noise incorporates the constant minimal noise or vibration present in real-world hardware.

  3. **Static data variance (measurement error):** This technique perturbs the donor’s EBV using a normal distribution before calculating the EBV risk bracket.

  4. **Categorical flip (feature noise):** The operator parameter is randomly altered according to a predefined noise level (0.01).
   
-   **Closed-Loop Interventions:** Automatically manages complications such as **Citrate Toxicity** and **Irregular Flow Rates**.
-   **Clinician Trust (XAI):** Integrated SHAP plots provide transparency for every automated decision, bridging the "black-box" dilemma in medical AI.

## 📈 Performance Results

Extensive comparative simulations validated the system's efficacy:
-   **33.42% reduction** in complication-driven terminations.
-   **1,054.99% increase** in successfully completed donations compared to baseline.
-   **75.82% reduction** in incident density of adverse outcomes per 10,000 minutes.

## 🛠️ Tech Stack

-   **Language:** Python
-   **Core ML:** XGBoost, Scikit-learn
-   **Explainability:** SHAP
-   **Natural Language:** OpenAI LLMs, Text Embeddings
-   **Data Processing:** Pandas, NumPy

## ⚙️ How to use

1. **Generating new donor data:** To generate new data, run the first 3 cells in the `XGB_training.ipynb` file. The required amount of new donors data can be specified in the loop count.

   `# Populate the dictionary with synthetic data for 100,000 donors`

   `for id in range(100000):`
2. **Generating the synthetic donation data:** The same file contains the code to generate the final dataset.

   `dataset, outcomes = dataset_generator_engine(dataset=pd_donors_db)`

   `noisy_dataset = inject_noise_gpu(dataset, noise_level=0.01)`


## 📝 License

This project was developed as part of the Master of Science in Artificial Intelligence dissertation at the University of East London.

---
*Developed by Carlos Henrique Aguillon Lopez under the supervision of Dr. Saeed Sharif.*
