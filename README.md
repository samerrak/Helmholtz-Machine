# Helmholtz Machine: Brain-Inspired AI

This repository contains an implementation and analysis of Helmholtz Machines, developed as part of COMP 549: Brain Inspired AI, Winter 2025, by Samer Abdulkarim.

## 🌟 Overview

Helmholtz machines are generative models inspired by brain mechanisms. They consist of two pathways:

- **Recognition pathway** (bottom-up): Encodes input data into a latent representation.
- **Generative pathway** (top-down): Decodes the representation to reconstruct the input (also called "dreaming").

Training is performed using the **wake-sleep algorithm**, alternating between refining the generative and recognition pathways.

---

## 💡 Key Concepts

### Description Length Cost

The cost measures the number of bits needed to represent data and its latent explanation:
C(α, d) = C(α) + C(d | α)
- **C(α)**: Cost of describing latent features (recognition pathway).
- **C(d | α)**: Cost of describing data given the features (generative pathway).

A lower total cost implies a more efficient and accurate model.

### Loss Function

The Helmholtz machine minimizes a loss function inspired by the Minimum Description Length (MDL) principle. It involves terms reflecting reconstruction accuracy and the match between recognition and generative distributions.

---

## ⚙️ Wake-Sleep Algorithm

### Wake Phase

- **Goal**: Improve generative weights to better reconstruct data.
- **Process**:
  1. Propagate real data upwards using the recognition model.
  2. Update generative weights by comparing actual and predicted lower-layer activities.

### Sleep Phase

- **Goal**: Improve recognition weights to better infer latent variables.
- **Process**:
  1. Generate ("dream") data using the generative model.
  2. Update recognition weights by comparing actual and predicted higher-layer activities.

---

## 🧪 Experiments

### Single-Class Training

- Network dreams resemble variations of a single digit (e.g., zeros).
- Generative weights show clear class-specific patterns.
- Risk of overfitting; limited generalization.

### Two-Class Training

- Dreams mix features from both classes (e.g., 3s and 8s).
- Generative weights become more complex to capture mixed features.

### All-Class Training

- Dreams become more abstract and noisy.
- Harder for the network to separate features, resulting in increased cost.

### Effect of Hidden Units

- Increasing hidden units improves capacity to capture latent features.
- Lower final cost and more accurate reconstructions.

### Effect of Turning Off Phases

- **No wake phase**: Generative model fails to improve, leading to poor reconstructions.
- **No sleep phase**: Recognition model cannot refine, leading to poor feature inference.
- In both cases, description length cost rises over time.

---

## 🖥️ Code Highlights

Key functions include:

- `wake(inputs, update=True)`: Updates generative weights using data-driven inference.
- `sleep(update=True)`: Updates recognition weights using generated samples.
- `generate()`: Produces "dream" inputs for the sleep phase.

---

## 📈 Results

- Description length plots show characteristic decrease and eventual increase (overfitting or under-optimization).
- Weight visualizations illustrate learned feature representations.
- Generated images ("dreams") provide insight into model performance.

---

## 📄 References

- Dayan, P., Hinton, G.E., Neal, R.M., & Zemel, R.S. (1995). The Helmholtz machine. Neural Computation.
- Course notes and materials from COMP 549: Brain Inspired AI (Winter 2025).

---

## ✉️ Contact

Samer Abdulkarim  
[LinkedIn](https://www.linkedin.com/in/samerabdulkarim)  
Email: samer_ak@icloud.com

---

⭐ Feel free to fork, clone, or contribute!
