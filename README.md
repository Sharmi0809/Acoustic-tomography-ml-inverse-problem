# Acoustic Travel-Time Tomography: Analytical Inversion vs MLP

## MSc Advanced Computing with Artificial Intelligence – Dissertation Project

This repository contains the implementation developed for my MSc dissertation at the University of Stirling.

The project investigates a synthetic **2D acoustic travel-time tomography inverse problem**, where the objective is to reconstruct hidden slowness values from measured acoustic travel times.

Two reconstruction approaches are compared:

1. Analytical inversion using linear algebra
2. A Multi-Layer Perceptron (MLP) neural network

The main aim was to investigate how accurately a neural network can learn the inverse mapping from travel-time measurements to underlying slowness values, and how its performance compares with the analytical solution as problem complexity and measurement noise increase.

---

## Problem Formulation

The forward problem is represented as:

d = K m

where:

- `d` represents the measured travel-time data
- `K` is the sensitivity matrix describing ray-path lengths through the grid cells
- `m` represents the unknown slowness values to be reconstructed

The inverse problem involves estimating `m` from the observed travel-time measurements `d`.

---

## Methods

### Analytical Inversion

A conventional linear-algebra-based inversion method was used as the baseline solution.

For this controlled synthetic linear problem, the analytical approach provides highly accurate reconstruction under clean-data conditions.

### Multi-Layer Perceptron (MLP)

A neural network was trained to learn the inverse relationship:

Travel-time measurements → Slowness values

The MLP uses:

- ReLU activation in hidden layers
- Linear output layer
- Adam optimizer
- Learning rate: 0.001
- Mean Squared Error (MSE) loss
- Batch size: 128
- Early stopping

Independent training, validation and test datasets were generated to evaluate generalisation to unseen examples.

---

## Experimental Setup

Experiments were conducted across increasingly complex 2D grid sizes:

- 2 × 2 — 4 unknown slowness values
- 3 × 3 — 9 unknown values
- 4 × 4 — 16 unknown values
- 5 × 5 — 25 unknown values
- 6 × 6 — 36 unknown values

This allowed the effect of increasing inverse-problem complexity on reconstruction performance to be studied.

---

## Noise Robustness

To evaluate robustness under imperfect measurements, five different noise models were investigated:

- Gaussian noise
- Uniform noise
- Laplace noise
- Multiplicative noise
- Impulsive noise

Noise levels ranging from 0.00 to 0.30 were evaluated.

Monte Carlo simulations with 1,000 runs per condition were used to reduce dependence on individual random noise realisations and provide more robust performance estimates.

---

## Evaluation Metrics

Model performance was evaluated using:

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- Relative Error

Additional experiments investigated challenging slowness distributions, peak detectability and neural-network stability across different random training seeds.

---

## Key Results

Under clean-data conditions, analytical inversion achieved approximately 99.9% reconstruction accuracy across the tested grid sizes.

The MLP also achieved strong performance on unseen clean data:

| Grid Size | MLP Accuracy |
|-----------|-------------:|
| 2 × 2 | 99.91% |
| 3 × 3 | 99.71% |
| 4 × 4 | 99.60% |
| 5 × 5 | 99.05% |
| 6 × 6 | 98.43% |

MLP performance gradually decreased as grid complexity increased.

Both analytical and MLP approaches were affected by increasing measurement noise, with multiplicative and impulsive noise producing particularly challenging conditions at larger grid sizes.

---

## Technologies Used

- Python
- TensorFlow / Keras
- NumPy
- Pandas
- scikit-learn
- Matplotlib
- Jupyter Notebook
- Linear Algebra
- Machine Learning
- Neural Networks
- Monte Carlo Simulation

---

## Repository Contents

`3538849_code.ipynb`

Main Jupyter Notebook containing the implementation of the synthetic data generation, analytical reconstruction, MLP training and evaluation, noise experiments and performance analysis.

---

## Key Learning Outcomes

This project provided practical experience in:

- Designing and training neural networks
- Developing synthetic machine-learning datasets
- Solving inverse problems
- Comparing ML models with analytical methods
- Testing model robustness under multiple noise distributions
- Evaluating models using quantitative error metrics
- Performing Monte Carlo experiments
- Analysing model scalability and generalisation

---

## Conclusion

For this controlled linear inverse problem, analytical inversion remains the natural and most accurate solution.

However, the MLP successfully learned the inverse mapping and generalised to unseen synthetic slowness distributions.

The experiments demonstrate both the potential and limitations of neural-network-based inverse modelling, particularly as problem dimensionality and measurement noise increase.

Future work could extend the approach to larger grids, more realistic ray geometries, real travel-time measurements and alternative deep-learning architectures such as convolutional neural networks.

---

## Author

**Sharmila Devi Shanmugam**

MSc Advanced Computing with Artificial Intelligence  
University of Stirling, Scotland, UK

Interested in Machine Learning, Artificial Intelligence, Data Science and applied AI engineering.
