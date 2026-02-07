# Task 3 - Pulse Timer (TP)

## Goal
Create a circuit where the output turns ON for a fixed duration every time the input receives a rising edge. The output must stay ON for the full preset time, even if the input turns OFF immediately after the edge.

---

## Concept
A TP generates a fixed‑length pulse on every rising edge of the input.  
Once triggered, the timer runs independently of the input.  
The output remains ON for the full preset duration, then turns OFF automatically.

In LOGO!, the TP used in this task restarts its timing window if a new rising edge occurs before the previous pulse has finished. This behaviour is specific to LOGO! and differs from some PLC brands where pulses cannot overlap.

---

## Ladder Logic Explanation
The rung contains:

- `I1` - Input that provides the rising edge  
- `T1` - TP block  
- `Q1` - Output that stays ON for the preset pulse duration  

### How It Works
- When `I1` transitions from 0 to 1, the TP starts timing  
- `Q1` turns ON immediately and stays ON for the full preset time  
- If `I1` stays ON, the pulse does not extend  
- If a new rising edge occurs before the pulse ends, LOGO! restarts the timer and begins a new full pulse  
- When the timer expires, `Q1` turns OFF  

This makes TP ideal for one‑shot triggers, alarms, and timed actuations.

---

## Behaviour Table

| I1 | Rising Edge | Timer Active | Q1 | Description |
|----|-------------|--------------|----|-------------|
| 0  | No          | No           | 0  | Idle |
| 1  | Yes         | Yes          | 1  | Pulse starts |
| 1  | No          | Yes          | 1  | Pulse continues |
| 1  | No          | No           | 0  | Pulse expired |
| 0  | No          | No           | 0  | Idle |
| 1  | Yes         | Yes          | 1  | New pulse triggered |

---

## What This Teaches
- How rising‑edge‑triggered timing works  
- Why TP outputs ignore the input after the edge  
- How LOGO! TP restarts pulses when edges arrive quickly  
- How to generate consistent, fixed‑length pulses for solenoids, alarms, and triggers  

---

## Files Included
- `task-3-tp.lsc` - LOGO! Soft Comfort project file  
- `screenshot.png` - Ladder logic view  
- `notes.md` - This documentation
