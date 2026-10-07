# Diwali Decoration Lights - LED Blinking Circuit Project

## 🎆 Happy Diwali! 🎆

A **Pure IC-Based LED Blinking & Light Show Circuit** for Diwali decorations using only logic gates and timing ICs - NO microcontroller required!

---

## Project Overview

Create a **festive LED blinking pattern** using:
- **555 Timer IC** (Astable Oscillator mode) for timing
- **Counter ICs** (7490, 7493) for sequential patterns
- **Multiplexer IC 74153** for light show routing
- **Flip-Flops** (7474) for LED control logic
- **AND/OR Gates** for pattern generation

**Perfect for:** Diwali lights, festival decorations, entrance displays

---

## Circuit Type 1: Simple LED Blinker (Beginner)

### Components
- **IC 555** (Timer) × 1
- **Capacitors:** 10µF, 0.01µF
- **Resistors:** 1kΩ, 10kΩ, 100kΩ
- **LEDs:** Red/Yellow (Diwali colors) × 8
- **Transistor:** 2N2222 (for LED current amplification)
- **Power supply:** 5V DC

### 555 Astable Mode Pinout

```
         ┌─────────┐
    GND │1       8│ VCC (+5V)
  TRIG  │2       7│ DISCH
   OUT  │3       6│ THRES
  CTRL  │4       5│ RST
         └─────────┘
```

### Simple Blinking Circuit

```
        ┌─────────────────────────────────┐
        │                                 │
       10µF                             VCC (+5V)
        │                                 │
    ┌───┴────────────────────────────────┬┘
    │                                    │
   GND                              [IC 555]
    │                           ┌────────┴────┐
    │                           │ Pin 7(D)    │
    │                    1kΩ ───┤             │
    │                    10kΩ ──┤             │
    │                    100kΩ ┐│ Pin 6(T)   │
    │                          ││ Pin 2(T)   │
    │   ┌───────────────────────┘│           │
    │   │          0.01µF        │ Pin 3(O)  │
    │   │            │           └─────┬─────┘
    │   └────────────┤                 │
    │           GND  │              LED OUTPUT
    │                │                 │
    └────────────────┼─────────────────┘
                     │
                    LED (with 330Ω resistor)
                     │
                    GND
```

### Timing Formula

**Frequency of Blinking:**
```
f = 1.44 / ((R1 + 2×R2) × C)

Where:
R1 = 1kΩ
R2 = 10kΩ
C = 10µF

f ≈ 7.2 Hz (Blinks ~7 times per second) ✨
```

---

## Circuit Type 2: Multi-LED Chasing Effect (Intermediate)

### Components
- **IC 555** × 1 (Clock generator)
- **IC 7490** (Decade Counter) × 1
- **IC 74153** (4-to-1 Multiplexer) × 2
- **IC 7404** (NOT gate) × 1
- **LEDs:** 8 (in Diwali colors: Red, Yellow, Orange)
- **Resistors:** 330Ω (for each LED), 10kΩ (pull-downs)
- **Capacitors:** 10µF, 0.01µF
- **Power:** 5V DC

### Circuit Diagram

```
[IC 555 TIMER]
    ↓
    ├─→ OUTPUT (1-7Hz clock pulse)
    │
    ↓
[IC 7490 COUNTER]
    │
    ├─→ QA, QB, QC, QD (4 outputs)
    │   (Counts from 0 to 9 in binary)
    │
    ↓
[IC 74153 MUX × 2]
    │
    ├─→ Selects which LED to light
    │   (Routes clock through 8 different LEDs)
    │
    ↓
LED ARRAY (8 LEDs in series/parallel)
    │
    └─→ GND (through 330Ω resistor each)
```

### Pin Connections

**IC 555 to IC 7490:**
```
555 Pin 3 (Output) → 7490 Pin 14 (Input A)
555 Pin 3 (Output) → 7490 Pin 1 (Reset must be LOW for counting)
```

**IC 7490 to IC 74153 (Multiplexer):**
```
7490 QA → 74153 Pin 6 (Selection A)
7490 QB → 74153 Pin 11 (Selection B)
7490 QC → 74153 Pin 6 (for 8-to-1 via cascading)
7490 QD → 74153 Pin 11 (for cascading)
```

**LED Connections:**
```
LED1 ──→ (330Ω) → GND
LED2 ──→ (330Ω) → GND
LED3 ──→ (330Ω) → GND
LED4 ──→ (330Ω) → GND
LED5 ──→ (330Ω) → GND
LED6 ──→ (330Ω) → GND
LED7 ──→ (330Ω) → GND
LED8 ──→ (330Ω) → GND
```

---

## Circuit Type 3: Festive Pattern (Advanced)

### Components
- **IC 555** × 2 (Different frequencies)
- **IC 7474** (Flip-Flops) × 2
- **IC 7408** (AND gates) × 1
- **IC 7432** (OR gates) × 1
- **IC 4017** (Johnson Counter) × 1
- **LEDs:** 10 (representing Diwali Diyas)
- **Resistors & Capacitors:** As before

### Pattern Logic

```
Counter State | LED Pattern
──────────────┼─────────────────────────
0             | ✨ (LED 1)
1             | ✨ (LED 2)
2             | ✨ (LED 3)
3             | ✨ (LED 4)
4             | ✨ (LED 5)
5             | ✨ (LED 1,2,3,4,5 - All ON)
6             | ✨ (LED 6)
7             | ✨ (LED 7)
8             | ✨ (LED 8)
9             | ✨ (LED 1-8 - Pulse effect)
```

---

## Practical Breadboard Layout

### Step-by-Step Assembly

**Part 1: Clock Circuit (IC 555)**
1. Connect Pin 8 to +5V
2. Connect Pins 1, 4 to GND
3. Connect Pin 2 to Pin 6 (TRIG & THRES together)
4. Add 10µF between Pins 2,6 and GND
5. Add 1kΩ resistor from Pin 7 to +5V
6. Add 10kΩ resistor from Pin 7 to Pin 2
7. Add 0.01µF capacitor from Pin 5 to GND
8. Output from Pin 3

**Part 2: Counter Circuit (IC 7490)**
1. Connect Pin 5, 10 to GND
2. Connect Pin 16 to +5V
3. Connect 555 Output (Pin 3) to 7490 Pin 14
4. Connect Pin 1 to GND (to enable counting)
5. Outputs QA-QD = Pins 12, 9, 8, 11

**Part 3: LED Output Stage**
1. Connect each LED anode to 74153 output
2. Connect LED cathode through 330Ω to GND
3. Add bypass capacitor (0.1µF) near power pins

---

## Expected Visual Effects

### Effect 1: Simple Blink (555 Timer Only)
- **Pattern:** All LEDs blink together
- **Speed:** ~7 blinks/second
- **Look:** Classic twinkling effect

### Effect 2: Running Light (Counter + Mux)
- **Pattern:** LEDs light up sequentially (1→2→3→4→5→6→7→8→1)
- **Speed:** ~1 complete cycle per second
- **Look:** Diwali Diyas lighting up one by one

### Effect 3: Pulse & Chase (Advanced)
- **Pattern:** Mix of sequential + all-on effects
- **Speed:** Variable (multi-frequency)
- **Look:** Festive light show with patterns

---

## Component Shopping List

| Component | Quantity | Price (Approx) |
|-----------|----------|---|
| IC 555 Timer | 2 | ₹20 |
| IC 7490 Decade Counter | 1 | ₹30 |
| IC 74153 Multiplexer | 2 | ₹40 |
| IC 7474 Flip-Flop | 1 | ₹20 |
| IC 7408 (AND gate) | 1 | ₹15 |
| IC 7432 (OR gate) | 1 | ₹15 |
| Red LEDs | 5 | ₹20 |
| Yellow LEDs | 3 | ₹15 |
| Orange LEDs | 2 | ₹10 |
| 330Ω Resistors | 10 | ₹10 |
| 10kΩ Resistors | 5 | ₹5 |
| 1kΩ Resistors | 2 | ₹2 |
| 100kΩ Resistors | 2 | ₹2 |
| 10µF Capacitor | 5 | ₹20 |
| 0.01µF Capacitor | 3 | ₹10 |
| Breadboard | 1 | ₹150 |
| Jumper Wires | 50 | ₹50 |
| Power Supply 5V | 1 | ₹300 |
| **Total** | - | **~₹720** |

---

## Frequency Adjustment Guide

To change blinking speed, modify **R1, R2, C** in 555 timer:

```
For SLOW blink (1 blink/second):
- R1 = 10kΩ, R2 = 100kΩ, C = 100µF
- f ≈ 0.7 Hz

For MEDIUM blink (3-4 blinks/second):
- R1 = 1kΩ, R2 = 10kΩ, C = 10µF
- f ≈ 7 Hz

For FAST blink (10+ blinks/second):
- R1 = 100Ω, R2 = 1kΩ, C = 1µF
- f ≈ 70 Hz
```

---

## Safety & Installation

⚠️ **Important:**
- Use regulated **5V DC power only**
- Never exceed 5V on IC pins
- Ensure proper **heatsinking** for brightness (use transistor amplification)
- Install **fuse (500mA)** in power line
- **NO 230V AC directly to ICs** - use adapter only
- Keep away from water/moisture (Diwali rain precaution)
- Check all connections before power ON

---

## Testing Steps

1. **Power ON** - LEDs should start blinking
2. **Observe Pattern** - Should be continuous
3. **Check Frequency** - Count blinks in 10 seconds
4. **Verify All LEDs** - Each should light up
5. **Safety Check** - No excessive heat from ICs

---

## Simulation Before Breadboard

Use **Logisim** or **CircuitLab** to:
- Test counter sequences
- Verify timing calculations
- Visualize LED patterns
- Debug connections

---

## Display Setup Ideas

### Decoration Options:
1. **Diwali Diya Box** - Mount LEDs in a wooden/cardboard frame
2. **Doorway Arch** - String LEDs along entrance
3. **Window Display** - Arrange in decorative pattern
4. **Festival Lantern** - Inside transparent container
5. **Rangoli LED Frame** - Embed LEDs in rangoli border

### Placement:
```
┌─────────────────────────┐
│   🔴🟡🟠🔴🟡🟠🔴🟡      │  (LED Strip)
│   ✨ ✨ ✨ ✨ ✨ ✨ ✨ ✨ │  (Blinking Effect)
│   Main Entrance / Door   │
│                         │
└─────────────────────────┘
```

---

## Troubleshooting

| Problem | Cause | Solution |
|---------|-------|----------|
| LEDs not blinking | No clock signal | Check 555 timer connections |
| Dim LEDs | High resistance | Add transistor amplifier |
| Uneven brightness | Bad capacitor | Replace capacitor |
| Counter stuck | Input not connected | Verify 555→7490 connection |
| One LED always ON | Mux selection issue | Check Pin 6, 11 connections |

---

## Extension Ideas

1. **Add Sound Effect** - Use piezo buzzer with timer IC
2. **Variable Speed Control** - Use potentiometer on 555
3. **More Colors** - Add RGB LEDs with switching logic
4. **Wireless Control** - Add IR receiver circuit (separate project)
5. **Temperature Sensor** - Adaptive brightness based on heat

---

## Lab Report Format

1. **Title:** Diwali LED Light Show - IC Based Circuit
2. **Objective:** Design blinking/chasing LED pattern
3. **Theory:** Timer, Counter, Multiplexer working
4. **Circuit Diagram:** Detailed schematic
5. **Truth Tables:** Counter outputs
6. **Implementation:** Breadboard steps
7. **Results:** Video/photos of blinking pattern
8. **Conclusion:** Applications of IC-based timing circuits

---

## 🎆 **HAPPY DIWALI!** 🎆

**Celebrate this Diwali with Electronics!** ✨

Your pure IC-based LED decoration circuit is:
- ✅ No microcontroller needed
- ✅ Simple to build
- ✅ Low cost
- ✅ Reusable year after year
- ✅ Perfect for learning digital logic

**"May your Diwali be as bright as these LEDs!"** 💡🎉

---

**Created with ❤️ for Diwali celebrations using pure IC logic circuits**

