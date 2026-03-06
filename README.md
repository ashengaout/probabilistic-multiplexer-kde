# Probabilistic Multiplexer and Kernel Density Estimation (KDE)

## Overview
From-scratch implementation of Kernel Density Estimation on a probabilistic mixture 
distribution, exploring bandwidth selection and the bias-variance trade-off.

The mixture distribution combines three one-dimensional Gaussian random generators, each 
with distinct mean and variance parameters, selected with probabilities $p_1$, $p_2$, $p_3$ 
where $p_1 + p_2 + p_3 = 1$.

---

## Structure

**Part 1 — Large-Scale Sampling and Visualization (n = 10,000)**
Generates 10,000 samples from the mixture distribution, plots a normalized histogram, 
and overlays the true analytical mixture PDF to verify convergence.

**Part 2 — Kernel Density Estimation and RMS Error (n = 10)**
Implements KDE from scratch using a Gaussian kernel. Computes average RMS error over 
50 trials for both a discovery set (used to build the KDE) and a replication set (unseen 
points), and compares the two.

**Part 3 — Effect of Kernel Bandwidth (n = 10)**
Sweeps across a meaningful range of bandwidths and plots average RMS error vs bandwidth 
for both sets, revealing the bias-variance trade-off.

**Part 4 — Discussion: Bias–Variance Trade-off**
Written analysis of the bandwidth sweep results, covering bias, variance, optimal bandwidth, 
discovery vs replication divergence, and the general bias-variance trade-off in 
nonparametric density estimation.

**Part 5 — Effect of Sample Size (n = 100)**
Repeats Parts 2 and 3 with n = 100 and compares results against n = 10, analysing the 
effect of sample size on RMS magnitude, optimal bandwidth shift, and bias-variance balance.

---

## Implementation

All core functions are implemented from scratch without KDE libraries:

- `generate_samples(n)` — probabilistic multiplexer sampling from the mixture distribution
- `mixture_pdf(x)` — evaluates the true analytical mixture PDF
- `gaussian_kernel(u)` — standard Gaussian kernel
- `kde(eval_points, training_points, h)` — Kernel Density Estimator
- `rms_error(kde_vals, true_vals)` — Root Mean Square error
- `run_trial(n, h)` — single experimental trial
- `run_experiment(n, h, n_trials)` — averages RMS over n_trials
- `sweep_bandwidths(n, h_values, n_trials)` — sweeps across bandwidth range
- `plot_bandwidth_sweep(h_values, disc_rms, rep_rms, n)` — plots RMS vs bandwidth

---

## Requirements
```python
numpy
matplotlib
```

---

## Usage

Open `Homework_2.ipynb` in JupyterLab and run all cells in order. No additional 
configuration required.
