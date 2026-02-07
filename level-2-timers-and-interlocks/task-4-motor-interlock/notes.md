# Task 4 - Motor Interlock (Mutual Exclusion)

## Goal
Prevent two outputs from ever being ON at the same time by making each output block the other.  
Only one output may run at any moment, even if both inputs are pressed.

---

## Concept
Interlocking ensures that two opposing actions cannot occur together.  
Each output uses the *other output’s state* as a condition, creating a safe, mutually exclusive pair.

This is commonly used for:

- Forward and reverse motors  
- Extend and retract cylinders  
- Open and close actuators  

The key idea is simple:  
If one output is ON, the other is forced OFF.

---

## Ladder Logic Explanation
The logic uses two rungs:

- `I1` - Command for `Q1`  
- `I2` - Command for `Q2`  
- `Q1` and `Q2` - Outputs that interlock each other  
- Each rung includes the *opposite output* as a normally closed contact

### How It Works
- When `I1` is pressed, `Q1` energises  
- The NC contact of `Q1` in the second rung opens, blocking `Q2`  
- When `I2` is pressed, `Q2` energises  
- The NC contact of `Q2` in the first rung opens, blocking `Q1`  
- If both inputs are pressed, whichever output was ON first keeps the other locked out  

This guarantees that `Q1` and `Q2` can never be ON at the same time.

---

## Behaviour Table

| I1 | I2 | Q1 | Q2 | Description |
|----|----|----|----|-------------|
| 0  | 0  | 0  | 0  | Idle |
| 1  | 0  | 1  | 0  | Q1 ON, Q2 locked out |
| 0  | 1  | 0  | 1  | Q2 ON, Q1 locked out |
| 1  | 1  | 1  | 0  | Q1 was ON first → Q2 blocked |
| 1  | 1  | 0  | 1  | Q2 was ON first → Q1 blocked |

---

## What This Teaches
- How to create safe mutual exclusion between outputs  
- How NC contacts enforce blocking logic  
- Why interlocks are essential for motors and actuators  
- How PLC outputs can be used as logic conditions  

---

## Files Included
- `task-4-interlock.lld` - LOGO! Soft Comfort project file  
- `screenshot.png` - Ladder logic view  
- `notes.md` - This documentation
