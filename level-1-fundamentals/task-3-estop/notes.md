# Task 3 - Emergency Stop (E‑Stop) Logic

## Goal
Modify the existing Start/Stop latch so that:

- `I1` = Start (NO pushbutton)  
- `I2` = Stop (NC pushbutton)  
- `I3` = Emergency Stop (NC safety contact)  
- `Q1` = Motor  

The motor must:

- Turn OFF immediately when the Emergency Stop is pressed  
- Stay OFF while the Emergency Stop is active  
- **Not restart automatically** when the Emergency Stop is released  
- Only restart when Start is pressed again  

This reflects real industrial safety behavior.

---

## Concept
Emergency Stops in industry are **normally closed (NC)** devices.  
This ensures:

- If a wire breaks  
- If the contact fails  
- If the device is unplugged  

…the circuit opens and the machine **fails safe** (turns OFF).

In this task, the E‑Stop is inserted **in series** with the existing latch logic so it can interrupt the circuit at any time.

---

## Ladder Logic Explanation
The rung contains:

- `I1` - Start (NO)  
- `I2` - Stop (NC)  
- `I3` - Emergency Stop (NC)  
- `Q1` - Motor output coil  
- `Q1` feedback contact - for latching  

### How It Works
- When `I3` is **not pressed**, the NC contact is closed → normal operation  
- When `I3` is **pressed**, the NC contact opens → the latch drops out immediately  
- Releasing the E‑Stop **does not** restart the motor  
- The operator must press Start again to re‑energize the circuit  

This prevents unexpected machine restarts - a critical safety requirement.

---

## Behavior Table

| I1 | I2 | I3 | Q1 | Description |
|----|----|----|----|-------------|
| 0  | 0  | 0  | 0  | All inputs released → Motor OFF |
| 1  | 0  | 0  | 1  | Start pressed → Motor ON |
| 0  | 0  | 0  | 1  | Motor stays ON (latched) |
| 0  | 1  | 0  | 0  | Stop pressed → Motor OFF |
| 0  | 0  | 1  | 0  | E‑Stop pressed → Motor OFF immediately |
| 0  | 0  | 0  | 0  | E‑Stop released → Motor remains OFF (no auto‑restart) |

---

## What This Teaches
- Why Emergency Stops are **normally closed**  
- How to integrate safety devices into latch logic  
- Why machines must **not** auto‑restart after an E‑Stop  
- How PLC logic enforces safe machine behavior  
- The difference between operational control (Start/Stop) and safety control (E‑Stop)  

This task introduces real‑world safety principles used in every industrial control system.

---

## Files Included
- `task-3-estop.lld` - LOGO! Soft Comfort project file  
- `screenshot.png` - Ladder logic view  
- `notes.md` - This documentation
