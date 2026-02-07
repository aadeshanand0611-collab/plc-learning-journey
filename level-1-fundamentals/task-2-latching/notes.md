# Task 2 - Start/Stop Motor Latching (Seal‑In Circuit)

## Goal
Create a motor control circuit where:

- `I1` = Start (NO pushbutton)  
- `I2` = Stop (NC pushbutton)  
- `Q1` = Motor  

The motor must:

- Turn ON when Start is pressed  
- Stay ON after Start is released (latching)  
- Turn OFF when Stop is pressed  
- Stay OFF until Start is pressed again  

This introduces the fundamental industrial concept of a **seal‑in (latching) circuit**.

---

## Concept
A latch allows an output to maintain its state even after the initiating input is released.

Two approaches were explored:

1. **Using a built‑in Set/Reset (SR) block**  
2. **Building the latch manually using a feedback contact from `Q1`**

Both methods achieve the same behavior but teach different aspects of PLC logic.

---

## Method 1 - Latching Relay (SR Block)

### Logic Rules

| S | R | Q | Meaning |
|---|---|---|---------|
| 0 | 0 | Hold | Output stays as it was |
| 1 | 0 | 1 | Set |
| 0 | 1 | 0 | Reset |
| 1 | 1 | 0 | Reset has priority |

### Explanation
- `I1` energizes the **Set** input  
- `I2` energizes the **Reset** input  
- `Q1` follows the SR block output  

When both inputs are off, the output **holds** its previous state.

---

## Method 2 - Manual Latch (Seal‑In Contact)

### Ladder Logic Explanation
The rung contains:

- `I1` — Start (NO)  
- `I2` — Stop (NC)  
- `Q1` — Motor output coil  
- `Q1` feedback contact — placed in parallel with `I1`  

### How It Works
- Pressing Start energizes `Q1`  
- Once `Q1` is ON, its feedback contact keeps the rung true  
- Releasing Start does not break the circuit  
- Pressing Stop opens the NC contact and drops out the latch  

This mirrors real industrial ladder logic used in motor starters.

---

## Behavior Table

| I1 | I2 | Q1 | Description |
|----|----|----|-------------|
| 0  | 0  | Hold | Output stays in previous state |
| 1  | 0  | 1 | Start pressed → Motor ON |
| 0  | 0  | 1 | Motor stays ON (latched) |
| 0  | 1  | 0 | Stop pressed → Motor OFF |
| 1  | 1  | 0 | Reset has priority |

---

## What This Teaches
- How latching (seal‑in) circuits work  
- Why NC Stop buttons are used in industry  
- How PLCs maintain state across scan cycles  
- The difference between **Set/Reset logic** and **manual latching**  
- How to convert inputs to **momentary pushbuttons** in simulation  

This task builds the foundation for safety logic, interlocks, and sequencing.

---

## Files Included
- `task-2-latchingMethod-1.lld` — LOGO! Soft Comfort project file with method 1
- `task-2-latchingMethod-2.lld` — LOGO! Soft Comfort project file with method 2
- `screenshot.png` — Ladder logic view  
- `notes.md` — This documentation
