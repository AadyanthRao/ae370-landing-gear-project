# AE370 Group Project: Simulation of Aircraft Landing Gear Dynamics

This repository contains all code, figures, and documentation related to our AE370 Spring 2025 group project. We modeled and simulated the vertical dynamics of an aircraft landing gear system using a coupled mass-spring-damper formulation, subject to realistic ground excitations. The primary goal was to evaluate how system parameters — particularly damping — affect impact forces during landing and the smoothness of post-touchdown motion.

---

## ✈️ Project Objective

To explore how damping and stiffness influence the touchdown behavior of a simplified aircraft landing gear, using a numerical simulation of a single-degree-of-freedom mass-spring-damper system driven by a moving ground profile $z_g(t)$.

We focused on two engineering questions:

1. **How does damping affect touchdown loads?**  
2. **Can we tune stiffness/damping for smoother landings?**

---

## ⚙️ System Overview

We modeled the system as a damped oscillator with base excitation:

- $m$: Effective aircraft mass supported by the gear  
- $k$: Spring stiffness  
- $c$: Damping coefficient  
- $z(t)$: Vertical displacement of the aircraft  
- $z_g(t)$: Terrain input (ground profile)  
- $N(t)$: Normal force transmitted to the airframe  

Equation of motion:  
$$
m\ddot{z} = -k(z - z_g) - c(\dot{z} - \dot{z}_g)
$$

Normal force formulation:  
$$
N(t) = mg - k(z - z_g) - c\left[(\dot{z} - \dot{z}_g) - (\dot{z}(0) - \dot{z}_g(0))\right]
$$

---

## 📈 Key Results

- Verified **4th-order convergence** of our RK4 integrator.  
- Identified optimal damping range for minimizing both peak impact forces and settling time.  
- Demonstrated sensitivity of $N(t)$ to terrain features and system parameters.  
- Showed how relative velocity correction eliminates artificial initial damping spikes.  

Our simulations included:

- Synthetic terrain excitation composed of randomized smooth sine waves.  
- Time-domain plots of displacement $z(t)$, ground profile $z_g(t)$, and normal force $N(t)$.  
- Parameter sweeps across different damping values with comparative analysis.

---

## 📁 Repository Structure

```
ae370-landing-gear-project/
│
├── notebook/
│   └── AE370_Simulation.ipynb        # Main simulation and visualization notebook
│
├── report/
│   ├── AE370_Project_Report.pdf      # Final report
│   ├── AE370_Project_Report.tex      # LaTeX source (optional)
│   └── figures/                      # Exported simulation figures
│
├── code/
│   └── rk4_solver.py                 # RK4 integrator (optional modular form)
│   └── force_analysis.py             # Normal force calculations
│
├── data/
│   └── ground_profile.npy            # Generated synthetic ground data (optional)
│
└── README.md                         # You're here!
```

---

## 🧪 How to Run the Simulation

### Option 1: Google Colab  
Just open the notebook in Colab — no setup required.  
[Open in Colab](https://colab.research.google.com)

### Option 2: Local Python Environment

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ae370-landing-gear-project.git
   cd ae370-landing-gear-project/notebook
   ```

2. Install dependencies:
   ```bash
   pip install numpy matplotlib
   ```

3. Run the notebook:
   ```bash
   jupyter notebook AE370_Simulation.ipynb
   ```

---

## ✅ Reproducibility Statement

We designed this repository to ensure full reproducibility:

- All figures and simulations are generated from `AE370_Simulation.ipynb`.  
- Code is well-commented and modular.  
- Ground excitation is seeded for deterministic behavior.  
- Normal force computations match theoretical equations from the report.

---

## 👥 Team Members

- **Nick Djordjevic**  
- **Zhiwei Jiang**  
- **Anush Rajan**  
- **Aadyanth Rao**  
- **Ella Greer**

---

## 🙏 Acknowledgements

We thank **Professor Goza** and the **AE370 course staff** for their insightful lectures and feedback throughout the semester. This project challenged us to bridge theory and simulation in an aerospace engineering context.

We also acknowledge the responsible use of **ChatGPT** as a supplemental tool for:
- Clarifying LaTeX formatting and structure  
- Debugging Python code and RK4 logic  
- Refining simulation captions and section writeups

All math, simulations, and analysis were performed independently by our team. ChatGPT was used as a reference tool — similar to a textbook or documentation — and all content in the final report was generated with full understanding and intent by the group.

---

## 📎 Report Figure Reference Examples

- **Figure 1:** RK4 convergence plot  
- **Figure 2:** $z(t)$ vs. $z_g(t)$ under terrain excitation  
- **Figure 3:** Normalized force response $N(t)/mg$  
- **Figure 4:** Peak force vs. damping coefficient sweep

---

## 💬 License

This repository is provided for academic purposes only.
