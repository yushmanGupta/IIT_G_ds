
# Dynamic Pricing for Urban Parking Lots

## 📘 Introduction

This project implements dynamic pricing for 14 urban parking lots using real-time data. It is the Capstone Project for **Summer Analytics 2025** hosted by Consulting & Analytics Club × Pathway.

The goal is to adjust parking prices based on real-time demand, competition, and environmental factors to optimize parking lot usage.

## 📊 Models Implemented

### ✅ Model 1: Baseline Linear Model
Price increases linearly based on occupancy:

```python
Price_t+1 = Price_t + α * (Occupancy / Capacity)
```

### ✅ Model 2: Demand-Based Model
Price is a function of a composite demand score using:

- Occupancy Rate
- Queue Length
- Traffic Level
- Special Day Indicator
- Vehicle Type

Demand formula:

```python
Demand = α*(Occupancy/Capacity) + β*QueueLength - γ*Traffic + δ*SpecialDay + ε*VehicleWeight
Price_t = BasePrice * (1 + λ * NormalizedDemand)
```

### ✅ Model 3: Competitive Pricing Model
Adjusts price based on proximity to nearby parking lots:

- If the current lot is full and competitors are cheaper → price is reduced
- If competitors are expensive → price is increased

## 🔄 Real-Time Simulation

The simulation mimics real-time data streaming using `Pathway`. Each timestamp is processed sequentially to update pricing for each lot.

All pricing logic is applied at every time step, and the final price for each lot is computed using the three models.

## 📈 Bokeh Visualizations

Dynamic pricing is visualized using `Bokeh`:

- Real-time line plots for each parking space
- Comparison of baseline, demand-based, and competitive prices
- Interactive hover tool for detailed inspection

Example plot code:
```python
p.line('time', 'baseline', source=source, color='blue', legend_label="Baseline")
p.line('time', 'demand', source=source, color='green', legend_label="Demand-Based")
p.line('time', 'competitive', source=source, color='red', legend_label="Competitive")
```

## ⚙️ Installation

Install necessary libraries in Google Colab:

```bash
pip install bokeh geopy pandas numpy
```

## ▶️ Usage Instructions

1. Clone the repository or open the notebook in Google Colab.
2. Run all cells sequentially.
3. View the plots using Bokeh inline in Colab.
4. Adjust model parameters (like α, β, λ) to experiment with different pricing strategies.

## ✅ Summary

This notebook demonstrates how real-time data and basic economic logic can be combined to create adaptive pricing systems for urban infrastructure.

The modular design allows experimentation with pricing logic and easy integration of new features.
