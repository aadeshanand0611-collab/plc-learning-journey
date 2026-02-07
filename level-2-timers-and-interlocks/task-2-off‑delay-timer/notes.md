# Task 2 - Off‑Delay Timer (TOF)

## Goal
Create a circuit where an output turns ON immediately when the input turns ON, but stays ON for a defined delay after the input turns OFF. The timer only begins counting once the input goes FALSE.

---

## Concept
A TOF energises its output as soon as the input becomes TRUE.  
When the input turns FALSE, the TOF begins timing.  
If the input stays FALSE for the full preset duration, the output turns OFF.  
If the input turns TRUE again before the timer finishes, the timer resets and the output remains ON.

This behaviour is used for fans, lights, and any device that must continue running briefly after the trigger is removed.

---

## Ladder Logic Explanation
The rung contains:

- `I1` - Input that controls the TOF  
- `T1` - TOF block  
- `Q1` - Output that stays ON after input turns OFF  

### How It Works
- When `I1` turns ON, `Q1` turns ON immediately  
- When `I1` turns OFF, the TOF begins counting  
- If the timer reaches the preset value, `Q1` turns OFF  
- If `I1` turns ON again before the timer finishes, the timer resets and `Q1` stays ON  

---

## Behaviour Table

| I1 | Timer Counting | Timer Done | Q1 | Description |
|----|----------------|------------|----|-------------|
| 0  | No             | No         | 0  | Idle, waiting for input |
| 1  | No             | No         | 1  | Input ON, output ON |
| 0  | Yes            | No         | 1  | Input OFF, delay active |
| 0  | No             | Yes        | 0  | Delay finished, output OFF |

---

## What This Teaches
- How TOF maintains output power after input removal  
- How PLCs create controlled shutdown delays  
- Why TOF resets instantly when the input turns back ON  
- How to use TOF for run‑on fans, lights, and hold‑on logic  

---

## Files Included
- `task-2-tof.lld` - LOGO! Soft Comfort project file  
- `screenshot.png` - Ladder logic view  
- `notes.md` - This documentation
