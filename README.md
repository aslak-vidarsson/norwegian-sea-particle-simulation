# Modeling Marine Plastic Transport  
*Numerical simulation of particle trajectories using Heun’s method and oceanographic data*

The results can be found in **FINAL_DRAFT_PROJECT3.ipynb**. This was a two-week project in the course "Introduction to numerical calculations" at NTNU by Aslak Vidarsson Homme and Hallstein Olesønn Hagaseth, both students at NTNU.

## 🌊 Introduction
Plastic pollution in the ocean poses significant ecological and environmental challenges. Predicting where plastic debris travels and where it may eventually strand is essential for understanding long-term environmental impact and for planning cleanup operations.

In this project, we simulate the motion of plastic particles drifting with ocean currents and wind. Although the ocean contains an immense number of particles, their collective behavior can be approximated by tracking a smaller representative sample.
---

## 📁 Project Overview
The project consists of:

- A numerical solver based on **Heun’s method** (improved Euler).
- An **Interpolator class** for accessing ocean current and wind fields from the *NorKyst-800m* dataset.
- Simulation of particle trajectories in different regions along the Norwegian coast.
- Analysis of runtime behavior, convergence, and numerical stability.
- Investigation of how the **windage factor** influences stranding probability.

---

## 🔧 Methods

### Heun’s Method
Particle motion is modeled by the differential equation:

\[
\mathbf{v}(x, t) = \mathbf{u}(x,t) + f_w \cdot \mathbf{w}(x,t)
\]

where  
- **u** = ocean current  
- **w** = wind velocity  
- **f_w** = windage factor  

Heun’s method is used to update particle positions, and numerical tests were performed to choose a stable and accurate time step.

### Interpolation of Ocean Data
Ocean current and wind fields are retrieved from the NorKyst-800m dataset. Bilinear interpolation is used to evaluate these fields at arbitrary particle positions.

---

## 🌍 Simulations

### Particle Trajectories
Particle trajectories were simulated starting in several regions:
- Outside Trondheim  
- Outside Kristiansand  
- Along the Norwegian coast  
- In northern Norway  

Plots were created both in Cartesian coordinates and using proper map projection.

**Key observations:**
- Particles starting close together diverge rapidly due to flow variability.
- Some regions exhibit chaotic trajectories, while others show more structured motion.
- Uniformly distributed particles along the coast generally drift toward land.

---

## 🏖️ Stranding Analysis

A particle is considered *stranded* if it crosses a defined coastal boundary.  
Simulations were performed with different particle counts and windage factors.

**Main findings:**
- Around **10,000** particles provide sufficiently stable stranding statistics.
- With **zero windage**, almost no particles strand in this dataset.
- Increasing windage significantly increases both the likelihood and speed of stranding.
- Higher windage causes earlier stranding, but not necessarily a larger total fraction once all particles have reached the coastline.

---

## 📌 Conclusions
This project demonstrates how numerical models combined with real oceanographic data can provide insight into the transport and fate of marine plastic. Key conclusions include:

- Trajectories are highly sensitive to initial conditions.  
- Heun’s method with a small time step yields stable, reliable solutions.  
- Windage is a dominant factor in driving particles toward shore.  
- Ocean currents alone rarely explain observed stranding patterns in our study area.  

Even with a simplified model, the simulations capture important aspects of drift dynamics and help illustrate how marine debris is transported by environmental forces.

---
