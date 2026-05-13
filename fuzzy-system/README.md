# Fuzzy Logic Controller for Task Offloading

This project implements a **Mamdani fuzzy logic controller** for task offloading in an edge computing scenario.

The goal is to decide whether a task should be executed locally or offloaded to an edge server by minimizing the overall cost, defined as:

$$
\text{Cost} = \text{Delay} + \text{Energy}
$$

The implementation is designed to be simple, interpretable, and based on fuzzy rules rather than hard thresholds.

---

## Project Overview

In this simulation, each task is evaluated based on inputs such as:

- **Task Size**
- **Local Queue**
- **Edge Queue**

Using these inputs, the fuzzy controller determines the probability of offloading.  
The final action is then selected as follows:

- If `POff <= 50`, the task is executed **locally**
- If `POff > 50`, the task is **offloaded** to the edge server with the smaller queue
- If both edge servers have the same queue length, the controller selects the first one

---

## Implementation Details

The controller is built using `scikit-fuzzy` and includes:

- Fuzzy antecedents and consequent definitions
- Triangular membership functions
- A rule base that:
  - prefers offloading for larger tasks or high local queue values
  - avoids offloading when the edge servers are congested
- A Mamdani inference system for decision making

---

## Simulation Setup

The fuzzy agent is integrated into a simulation with:

- Multiple user equipments (UEs)
- Two edge servers
- `200` time slots

For each task, the following metrics are computed:

- **Total Delay**
- **Total Energy**
- **Total Weighted Cost**

---

## Baselines

The fuzzy controller is compared with two baseline policies:

- **Local Only**
- **Random**

---

## Results

The fuzzy controller achieves a better trade-off between delay and energy consumption.

| Method       | Cost  | Delay | Energy |
|-------------|------:|------:|------:|
| Local Only   | 922.2 | 370.1 | 552.2 |
| Random       | 834.2 | 255.1 | 579.1 |
| Fuzzy Logic  | 810.7 | 229.8 | 581.0 |

Although the fuzzy policy slightly increases energy usage, it significantly reduces delay and achieves the lowest total cost among the three methods.

---

## Requirements

- Python
- NumPy
- Matplotlib
- scikit-fuzzy

Install dependencies with:
```bash
pip install numpy matplotlib scikit-fuzzy
```

---
## How to Run
Open the notebook and run the cells sequentially:

```bash
jupyter notebook fuzzy.ipynb
```

---
## Notes
This project was created to explore how fuzzy logic can be used for intelligent decision making in edge computing environments.

The main advantage of the fuzzy approach is that it provides a human-readable rule base while still producing adaptive decisions.

---
## Future Improvements
Possible extensions for this project:

Add more input features
Tune membership functions automatically
Compare with reinforcement learning based offloading
Extend the simulation to more edge servers
Use real workload traces
