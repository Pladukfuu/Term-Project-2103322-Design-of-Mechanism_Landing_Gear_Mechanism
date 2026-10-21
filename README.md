## Project overview

- **Project name:** [Landing gear mechanism]
- **Problem / purpose:** [To investigate the kinematic trajectories and linkage rotation angles during the retraction and deployment processes to ensure smooth and uninterrupted operation.]
- **Team:** [Sawrasit Sriviset : Simscape Multibody and Symbolic mathematics]
- **Status:** Working on Symbolic mathematics
- **Last updated:** [2026-10-21]

## Repository structure

| Path | Purpose |
|---|---|
| `hardware/mechanical/` | CAD models, drawings, and fabrication files |
| `hardware/electronics/` | Schematics, PCB files, and wiring diagrams |
| `hardware/bom.csv` | Bill of materials with quantities, units, and sourcing details |
| `software/firmware/` | Microcontroller code and board setup |
| `software/application/` | PC or Raspberry Pi application code |
| `machine-skills/` | Machine commands, procedures, and skill instructions |
| `simulation/` | Models, scripts, assumptions, and simulation results |
| `docs/` | Assembly, setup, operation, and maintenance instructions |
| `media/` | Images, GIFs, and links to demonstration videos |
| `experiments/` | Procedures, raw data, and results |
| `publications/` | Project-related journal and conference papers |

## Software and Tools
* **CAD & 3D Modeling:** Autodesk Inventor Professional 2027, Autodesk Fusion 360
* **Kinematic & Dynamic Simulation:** MATLAB R2026a, MATLAB Simscape

## Collaboration and file practices

* **File Formats:** 
  * Save primary 3D CAD models and assemblies as `.ipt` / `.iam` (Inventor 2027) or `.f3d` (Fusion 360) under `hardware/mechanical/`.
  * Store kinematic equations and simulation models as `.m` scripts and `.slx` files (MATLAB/Simscape R2026a) under `simulation/`.
  * Export exchange formats like `.step` or `.stl` for cross-platform previewing.

