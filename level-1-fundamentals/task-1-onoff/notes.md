# Task 1 — Basic ON/OFF Control

## Goal
Create the simplest possible PLC control:  
**Input `I1` directly controls Output `Q1`.**

This establishes the foundation for understanding how the PLC scan cycle reads inputs and updates outputs.

---

## Concept
This task demonstrates the most fundamental PLC behavior:

- When **I1 = OFF**, the PLC evaluates the rung as false → **Q1 = OFF**
- When **I1 = ON**, the PLC evaluates the rung as true → **Q1 = ON**

There is no memory, latching, or additional logic beyond a single input controlling a single output.

---

## Ladder Logic Explanation
The rung contains:

- `I1` — Normally Open contact  
- `Q1` — Output coil  

The PLC continuously scans this rung.  
If `I1` is energized, `Q1` energizes.  
If `I1` is de‑energized, `Q1` turns off.

This is the baseline behavior from which all more complex logic is built.

---

## Behavior Table

| I1 | Q1 | Description |
|----|----|-------------|
| 0  | 0  | Input OFF → Output OFF |
| 1  | 1  | Input ON → Output ON |

---

## What This Teaches
- How a PLC evaluates a simple rung  
- How inputs and outputs behave during the scan cycle  
- The difference between **momentary** and **maintained** inputs  
- The foundation for building latches, interlocks, and safety logic later  

This task is intentionally simple — it’s the “Hello World” of PLC programming.

---

## Files Included
- `task-1-onoff.lsc` — LOGO! Soft Comfort project file  
- `screenshot.png` — Ladder logic view  
- `notes.md` — This documentation
