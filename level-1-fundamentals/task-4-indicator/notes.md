# Task 4 - Indicator Light Logic (Q2 Mirrors Q1)

## Goal
Extend the previous motor control logic so that:

- `Q1` = Motor  
- `Q2` = Indicator Light  

The indicator light must:

- Turn ON whenever the motor (`Q1`) is ON  
- Turn OFF whenever the motor is OFF  
- Never operate independently  
- Always reflect the exact state of `Q1`

This introduces the concept of **output‑to‑output dependency**, commonly used for status lights, alarms, and HMI indicators.

---

## Concept
In industrial control systems, indicator lights are often tied directly to the state of a device.  
This ensures operators always know:

- When a motor is running  
- When a valve is open  
- When a heater is active  

In this task, `Q2` simply **follows** the state of `Q1`.

There is no additional logic, timing, or latching - just a direct relationship.

---

## Ladder Logic Explanation
The rung contains:

- `Q1` - Motor output coil  
- `Q1` feedback contact - used as the condition for `Q2`  
- `Q2` - Indicator light output coil  

### How It Works
- When the motor (`Q1`) energizes, its contact closes  
- This immediately energizes `Q2`  
- When the motor turns OFF, the contact opens  
- `Q2` turns OFF at the same moment  

This ensures the indicator light always matches the motor state.

---

## Behavior Table

| Q1 (Motor) | Q2 (Indicator) | Description |
|------------|----------------|-------------|
| 0          | 0              | Motor OFF → Indicator OFF |
| 1          | 1              | Motor ON → Indicator ON |

---

## What This Teaches
- How to link outputs together using feedback contacts  
- How to create status indicators for motors, valves, and actuators  
- Why indicator lights should always reflect real device states  
- How PLC logic can drive operator feedback devices  

This task reinforces the idea that outputs can be used as logic conditions, not just inputs.

---

## Files Included
- `task-4-indicator.lld` - LOGO! Soft Comfort project file  
- `screenshot.png` - Ladder logic view  
- `notes.md` - This documentation
