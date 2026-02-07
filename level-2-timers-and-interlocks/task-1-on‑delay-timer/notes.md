# Task 1 - On‑Delay Timer (TON)

## Goal
Create a circuit where an output turns ON only after the input has remained ON for a defined delay. The input becomes TRUE immediately, but the output waits until the timer finishes.

---

## Concept
A TON begins timing as soon as its input becomes TRUE.  
If the input stays TRUE for the full preset duration, the timer’s done bit becomes TRUE and the output energises.  
If the input turns OFF before the timer completes, the timer resets instantly.

This behaviour is used for soft starts, staged energising, and safety delays.

---

## Ladder Logic Explanation
The rung contains:

- `I1` - Input that starts the delay  
- `T1` - TON block  
- `Q1` - Output that turns ON only after the delay  

### How It Works
- When `I1` turns ON, the TON begins counting  
- If `I1` stays ON for the full preset time, the TON done bit activates  
- The done bit energises `Q1`  
- If `I1` turns OFF at any time, the TON resets and `Q1` turns OFF immediately  

---

## Behaviour Table

| I1 | Timer State | Q1 | Description |
|----|-------------|----|-------------|
| 0  | Idle        | 0  | Waiting for input |
| 1  | Counting    | 0  | Delay active, output still OFF |
| 1  | Done        | 1  | Delay finished, output ON |
| 0  | Reset       | 0  | Input removed, timer resets |

---

## What This Teaches
- How TON delays work  
- How PLCs create controlled timing before energising equipment  
- Why TON resets immediately when the input drops  
- How to use TON for safe, predictable delays  

---

## Files Included
- `task-1-ton.lld` - LOGO! Soft Comfort project file  
- `screenshot.png` - Ladder logic view  
- `notes.md` - This documentation
