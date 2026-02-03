
# Probability Density Function Learning using Roll-Number-Parameterized Non-Linear Model

## Overview
This project demonstrates the learning of parameters of a probability density function after applying a roll-number-based non-linear transformation to real-world air quality data. The NO₂ concentration values from the India Air Quality dataset are used as the input feature.

The objective of the work is to apply a deterministic transformation, model the transformed data using a Gaussian-shaped probability density function, and estimate its parameters using statistical techniques.

---

## Dataset
- Source: India Air Quality Dataset (Kaggle)
- Feature Used: NO₂ concentration
- Data Type: Real-world environmental data

Non-numeric and missing values are removed during preprocessing.

---

## Methodology

### Step 1: Roll-Number-Based Transformation
Each NO₂ value \( x \) is transformed into a new variable \( z \) using the following function:

\[
z = T_r(x) = x + a_r*sin(b_r*x)
\]

where,

\[
a_r = 0.05 ∗ (r mod 7)
\]
\[
b_r = 0.3 ∗ (r mod 5 + 1)
\]

Here, \( r \) represents the university roll number. This transformation introduces a controlled non-linearity while remaining deterministic.

---

### Step 2: Probability Density Function Modeling

After applying the roll-number-based transformation, the transformed variable z is modeled using the following probability density function:

p̂(z) = c · exp( −λ (z − μ)² )

This function represents a Gaussian-shaped distribution, where:
- μ controls the center (mean) of the distribution
- λ controls the spread of the distribution
- c is a normalization constant

---

### Step 3: Parameter Estimation

Let z₁, z₂, … , zₙ denote the transformed data samples.

The parameters of the probability density function are estimated using Maximum Likelihood Estimation (MLE) as follows:

• Mean (μ)  
The mean is computed as the average of the transformed values:
μ = (1 / N) × Σ zᵢ

• Variance (σ²)  
The variance is computed as:
σ² = (1 / N) × Σ (zᵢ − μ)²

• Lambda (λ)  
Lambda is related to the variance as:
λ = 1 / (2 × σ²)

• Normalization Constant (c)  
The normalization constant is computed to ensure that the total probability integrates to one:
c = √(λ / π)

These parameters completely define the probability density function for the transformed variable z.

---

## Results

### Estimated Parameters

| Parameter | Description |
|---------|-------------|
| \( mu \) | Mean of transformed variable |
| \( lambda \) | Inverse variance parameter |
| \( c \) | Normalization constant |

The exact numerical values are obtained by executing the provided Python script.


---

## Tools and Technologies
- Python
- NumPy
- Pandas

Statistical estimation methods are used; no machine learning libraries are involved.

---

