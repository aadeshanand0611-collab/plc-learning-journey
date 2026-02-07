# Task 5 - Simple Sequence Control

## Goal
Create a three‑step sequence where each output turns ON only after the previous step has completed. The sequence begins with a Start input and stops immediately when the Stop input is pressed.

---

## Concept
A sequence is a controlled chain of events.  
Each step depends on the successful completion of the previous one.  
In this task:

- `Q1` is Step 1  
- `Q2` is Step 2  
- `Q3` is Step 3  

Timers between steps ensure each stage runs for a defined duration before the next begins.

`I1` starts the sequence.  
`I2` stops and resets the entire sequence.

All rungs use `I2` as a normally closed contact so pressing Stop breaks every stage at once.

---

## Ladder Logic Explanation
The logic uses five rungs:

- `I1` and `I2` control Step 1 (`Q1`)  
- `Q1` and `I2` control Timer `T1`  
- `T1` done and `I2` control Step 2 (`Q2`)  
- `Q2` and `I2` control Timer `T2`  
- `T2` done and `I2` control Step 3 (`Q3`)  

### How It Works
- Pressing `I1` energises `Q1` (Step 1)  
- `Q1` starts Timer `T1`  
- When `T1` finishes, `Q2` energises (Step 2)  
- `Q2` starts Timer `T2`  
- When `T2` finishes, `Q3` energises (Step 3)  
- Pressing `I2` at any time opens all NC contacts, turning OFF `Q1`, `Q2`, `Q3` and resetting both timers  

This creates a clean, predictable three‑stage sequence.

---

## Behaviour Table

| I1 | I2 | T1 Done | T2 Done | Q1 | Q2 | Q3 | Description |
|----|----|---------|---------|----|----|----|-------------|
| 0  | 0  | 0       | 0       | 0  | 0  | 0  | Idle |
| 1  | 0  | 0       | 0       | 1  | 0  | 0  | Step 1 active |
| 1  | 0  | 1       | 0       | 1  | 1  | 0  | Step 2 active |
| 1  | 0  | 1       | 1       | 1  | 1  | 1  | Step 3 active |
| *  | 1  | *       | *       | 0  | 0  | 0  | Stop pressed → full reset |

---

## What This Teaches
- How to build multi‑stage automation sequences  
- How timers create controlled delays between steps  
- How NC Stop logic resets an entire process  
- How to structure sequential logic cleanly and safely  

---

## Files Included
- `task-5-sequence.lsc` - LOGO! Soft Comfort project file  
- `screenshot.png` - Ladder logic view  
- `notes.md` - This documentation
