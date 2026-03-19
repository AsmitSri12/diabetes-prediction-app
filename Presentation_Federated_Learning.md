---
marp: true
theme: default
paginate: true
size: 16:9
style: |
  section {
    background-color: #f8f9fa;
    font-family: 'Arial', sans-serif;
  }
  h1 {
    color: #2c3e50;
  }
  h2 {
    color: #34495e;
    border-bottom: 2px solid #3498db;
    padding-bottom: 10px;
  }
  li {
    margin-bottom: 10px;
  }
---

<!-- _class: lead -->
# Federated Learning Framework using healthcare data(Type-2 Diabetes)

**United Institute of Technology, Prayagraj**

**Supervisor:**
Surya Prakash Dwivedi

**Team Members:**
Asmit Srivastava
Mohammad Fahad
Saurabh Singh

---

## Index

1. Introduction
2. Literature Review
3. Problem Statements and Objectives
4. Methodology
5. Requirement Analysis
   - Functional Requirements
   - Non-Functional Requirements
6. SDLC Models Used
7. Conclusion
8. Future Scope
9. References

---

## 1. Introduction

- **Overview:** Healthcare organizations generate vast amounts of patient data, but data privacy laws (HIPAA, GDPR) restrict data sharing.
- **Federated Learning (FL):** A novel approach that trains machine learning models across multiple decentralized hospital clients holding local data samples, without exchanging them.
- **Focus:** Predicting Type-2 Diabetes using the Pima Indians Diabetes Dataset while ensuring patient records never leave the hospital servers.
- **Key Concepts:** Localized training, model parameter aggregation, privacy preservation (Differential Privacy), and security protocols (SHA-512).

---

## 2. Literature Review

The framework builds upon foundational research in privacy-preserving AI:

- **Federated Averaging (FedAvg):** McMahan et al. (2017) demonstrated communication-efficient learning of deep networks from decentralized data.
- **Handling Heterogeneity (FedProx):** Li et al. (2020) highlighted ways to optimize FL in heterogeneous networks where data isn't uniformly distributed (non-IID).
- **Differential Privacy (DP):** Abadi et al. (2016) introduced robust mechanisms (gradient clipping and Gaussian noise) to further protect against model inversion attacks.
- **Medical AI Implications:** FL significantly lowers barriers for multi-institutional healthcare collaborations without compromising patient confidentiality.

---

## 3. Problem Statements and Objectives

### Problem Statement
Traditional machine learning requires centralizing patient data onto a single server, which raises serious **privacy, regulatory, and ethical concerns**. Healthcare data is inherently siloed, imbalanced, and localized.

### Objectives
1. **Develop a Privacy-Preserving System:** Implement a Federated Learning framework that only shares model parameter updates (weights) rather than raw records.
2. **Handle Data Heterogeneity:** Effectively train on highly imbalanced and non-IID datasets across hospital boundaries using FedProx.
3. **Ensure Security & Integrity:** Implement SHA-512 hashing to prevent model update corruption in transit and layer Differential Privacy (DP) for strict privacy budgets.

---

## 4. Methodology

### System Architecture
- **Clients (Hospitals):** Keep patient data local. Compute parameter updates using a custom Neural Network (DiabetesNet with BatchNorm & Dropout).
- **Central Server:** Aggregates gradients using Weighted FedAvg or FedProx and performs global evaluations.

### Training Flow (Iterative Rounds)
1. **Broadcast:** Server sends global model weights to all participating clients.
2. **Local Training:** Clients train on local data (using Adam, Cosine LR, and weighted BCELoss).
3. **Secure Transmission:** Clients send updated weights (hashed via SHA-512) back to the server.
4. **Aggregation & Evaluation:** Server validates hashes, aggregates models, and logs precision metrics (AUC-ROC, F1, Recall).

---

## 5. Requirement Analysis

### Functional Requirements
- **Data Partitioning:** Ability to split datasets into simulated local environments (IID and non-IID / Dirichlet).
- **Distributed Training:** Support for isolated client-side training and central server aggregation.
- **Security Protocols:** Implementation of SHA-512 hashing for parameter integrity.
- **Evaluation Mechanism:** Server-side held-out dataset evaluation focusing on medical-grade metrics (AUC-ROC, Recall).

### Non-Functional Requirements
- **Privacy Policy:** Zero raw data transmission (regulatory compliance).
- **Scalability:** System should easily scale to integrate new hospital clients.
- **Robustness & Stability:** Ensure numerical stability in predictions (handling class imbalances).

---

## 6. SDLC Models Used

The project was developed incorporating phases from multiple Systems Development Life Cycle (SDLC) models:

- **Waterfall Model:**
  - Used in the initial phases for strict requirement gathering, defining the system architecture, mathematical formulas, and dataset identification.
- **Incremental Model:**
  - Applied during the implementation phase. First, standard FedAvg was integrated, followed by incremental additions like FedProx, SHA-512 validation, and Differential Privacy (DP).
- **RAD (Rapid Application Development) Model:**
  - Utilized for the machine learning prototyping phase. Allowed for rapid iteration, continuous testing of hyperparameters, and tweaking model architectures based on AUC-ROC and F1 scores.

---

## 7. Conclusion

- We successfully built a functional **Federated Learning Framework** for predicting Type-2 diabetes without centralizing sensitive patient data.
- **Performance:** Achieved competitive medical metric scores (AUC-ROC ~ 0.84) nearly matching standard centralized models.
- **Privacy & Security:** Integrated robust defenses including Differential Privacy and cryptographic integrity checks.
- **Impact:** Demonstrates that healthcare institutions can collaborate on advanced AI models while strictly adhering to data privacy and compliance laws.

---

## 8. Future Scope

1. **Secure Aggregation (SecAgg):** Implementing advanced cryptographic techniques to protect the central server from observing individual client updates, mitigating risks from malicious clients.
2. **Multi-modal Data Integration:** Expanding the framework to handle larger, complex medical datasets such as MRI scans or full Electronic Health Records (EHRs).
3. **Real-world Hospital Deployment:** Transitioning from simulated environments to interconnected, secure cloud deployments across actual medical institution IT networks.
4. **Adaptive Privacy Budgets:** Dynamically adjusting Differential Privacy noise relative to the risk evaluated at each client node.

---

## 9. References

1. McMahan, H. B., et al. (2017). *Communication-efficient learning of deep networks from decentralized data.* AISTATS.
2. Li, T., et al. (2020). *Federated optimization in heterogeneous networks.* MLSys.
3. Abadi, M., et al. (2016). *Deep learning with differential privacy.* CCS.
4. Beutel, D. J., et al. (2020). *Flower: A friendly federated learning research framework.* arXiv:2007.14390.
5. Pima Indians Diabetes Database, National Institute of Diabetes and Digestive and Kidney Diseases.

---

<!-- _class: lead -->
# Thank You

**Questions & Discussion**
