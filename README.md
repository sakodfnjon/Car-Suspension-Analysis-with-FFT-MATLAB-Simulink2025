# Quarter-Car Suspension Optimization using MATLAB & Simulink

##  Project Overview
This project simulates and optimizes a passive Quarter-Car suspension system. The objective is to determine the optimal damping coefficient (c) to maximize passenger comfort and vehicle stability when subjected to a harsh road disturbance (step input).

The analysis compares three damping scenarios (Under-damped, Optimally damped, and Over-damped) using both **Time Domain (Settling Time)** and **Frequency Domain (Fast Fourier Transform)** analysis.

## ⚙️ System Parameters
The system is modeled using standard Second-Order differential equations of motion ($m\ddot{x} + c\dot{x} + kx = F(t)$) with the following Quarter-Car parameters:
* **Mass (m):** 250 kg
* **Spring Stiffness (k):** 16,000 N/m
* **Critical Damping (c_crit):** 4,000 Ns/m
* **Input Disturbance:** 1-unit Step Input (simulating a sharp curb/pothole)

## 📂 Repository Structure
* `final.mlx`: The main MATLAB Live Script that calculates critical damping, automates the Simulink parameter sweep, and generates the analysis dashboard.
* `car_model.slx`: The Simulink block diagram representing the Quarter-Car physics engine (Transfer Function).
* `final.pdf`: The final project report and presentation slides detailing the methodology and mathematical analysis.
* `results.png`: The output dashboard showing the Scope and FFT analysis.
* `extra_scripts/`: Additional MATLAB Live Scripts (`analyze_results.mlx`, `mathsexp.mlx`, `optimize_with_fft.mlx`) used during the experimental phase.

## 🚀 How to Run
1. Ensure you have MATLAB and Simulink installed.
2. Download the repository files to your local machine.
3. Open `final.mlx` in MATLAB and run the Live Script.
4. The script will automatically trigger the `car_model.slx` Simulink model 3 times and generate the comparative dashboard.

## 📊 Results & Analysis
The automated script tests three damping coefficients and extracts the displacement data to generate the Time and Frequency domain dashboard:

![Simulation Results]<img width="1385" height="830" alt="image" src="https://github.com/user-attachments/assets/592884e6-22cc-41d5-a2a4-be264309fb46" />

 

### Key Findings:
1. **Red Line (c=500, Zeta=0.12 | Under-damped):** * **Result:** Uncontrolled resonance. 
   * **Physics:** Fails to dissipate kinetic energy. The vehicle bounces continuously at its natural frequency (1.27 Hz), causing passenger motion sickness.
2. **Green Line (c=6000, Zeta=1.50 | Over-damped):** * **Result:** Sluggish recovery. 
   * **Physics:** The suspension is too stiff. While it prevents bouncing, it takes too long to recover from the bump (high energy in the 0-0.5 Hz range) and transmits harsh road forces to the chassis.
3. **Blue Line (c=2200, Zeta=0.55 | Optimally Damped):** * **Result:** Resonance suppressed. 
   * **Physics:** Effectively converts the kinetic energy of the bump into heat. It settles quickly (< 1.5s) without bouncing, representing the ideal trade-off between comfort and vehicle control.

## 🛠️ Tools Used
* **MATLAB:** Live Scripting, Automation, Signal Processing (FFT), Data Visualization.
* **Simulink:** Physics Modeling, Control Flow, Time-Series Simulation.
